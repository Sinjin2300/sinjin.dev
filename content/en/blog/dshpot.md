---
title: Dead Simple Honeypot - dshpot
date: 2026-03-03T13:19:24-07:00
draft: false
tags:
  - projects
  - security
  - blog
categories: projects
description: Exactly as the title says, a dead simple SSH honeypot for tinkerers.
layout: single
---

I've been wanting to have more public projects using rust on my GitHub since
most of my work is done in private repos away from prying eyes. I figured rather
than make some nonsense like l33tcode problem tutorial or some basic _flexing_
projects like a language or database, I would do something that I actually have
a want or need for. <br>

If you don't want to read this and just wan't to see the project,
[go here.](https://github.com/Sinjin2300/dshpot)

### What

Enter dshpot. <br>

dshpot is a **d**ead **s**imple **h**oney**pot** for SSH that has the express
purpose of being east to setup and use and not too feature rich. It simply logs
SSH password requests and stores relevant information in a sqlite database.
_Nothing Fancy_. <br>

I'm still planning on adding some more features like Prometheus exporters and
anything that I can reasonably be convinced will be useful.

### Why

Since I've started my homelab adventures the topic of security has come up time
and time again in all of my research on self hosting. If you have ever setup a
VPS you are _hopefully_ accutely aware of the steps that must be taken in the
**2 minutes** you have before bots start hammering your server. I've always
thought that reading the access.log and trying to parse what is going on after
hardening my SSH access was tedious and not a very pleasant experience. It also
felt kind of wasteful, like information was being lost in just letting fail2ban
reject people. <br>

There was also this idle curiousity about **what** passwords and usernames were
being atemmpted, like building a password list off of what other hackers have
already determined to be the most worthwhile combinations to try. That is the
intention of this project, it just enables you, the user, to **see** what people
are trying and test your assumptions and theories without having to make a
honeypot yourself.

### Usage

There are more thorough instructions on the
[github page](https://github.com/Sinjin2300/dshpot) so I will just cover the
most quick and simple way here. <br>

With **Nix** installed on your system with flakes enabled, all you have to do is
run:

```sh
nix run "github:Sinjin2300/dshpot" -- init && 
nix run "github:Sinjin2300/dshpot" -- serve
```

This will create an ssh host key as well as the database in the directory you
are currently in and begin accepting connections. <br> It defaults to port
`2222`:

```sh
$ ssh blog@localhost -p 2222
...
blog@localhost's password:
...
```

and the output:

```sh
... client=127.0.0.1:44288 password=test username=blog attempt=1
... client=127.0.0.1:44288 password=passwords username=blog attempt=2
... client=127.0.0.1:44288 password=appear username=blog attempt=3
```

If you want to run your own queries, the schema is available in the github
source, you can also just use sqlite3 and print the schema yourself with
`.schema connections` using the connections table as an example. <br><br>

I hope you find some use for this tool :)
