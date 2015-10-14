---
layout: post
date: 2015-10-14
title: "Using Karma with Browsers installed from Homebrew"
categories: javascript angular
read_time : 3
feature_image: categories/work-feature
show_related_posts: false
---

I have my Macbook Pro setup scripted so I can reset the entire OS anytime I need and get it setup fairly quickly. I use Homebrew Cask to install most of the applications I use, such as browsers.

Recently, I found that Karma has trouble capturing the browsers since Homebrew installs things differently from the normal install. Firefox (or Chrome, or any browser installed with Homebrew) would fail to be captured by Karma over and over. I kept getting error messages about how Firefox could not be captured, then could not be killed, and then Karma just hangs it seems.

```bash
➜ karma start
14 10 2015 13:42:37.184:WARN [karma]: No captured browser, open http://localhost:9876/
14 10 2015 13:42:37.195:INFO [karma]: Karma v0.13.11 server started at http://localhost:9876/
14 10 2015 13:42:37.202:INFO [launcher]: Starting browser Firefox
14 10 2015 13:43:37.206:WARN [launcher]: Firefox have not captured in 60000 ms, killing.
14 10 2015 13:43:39.209:WARN [launcher]: Firefox was not killed in 2000 ms, sending SIGKILL.
14 10 2015 13:43:41.214:WARN [launcher]: Firefox was not killed by SIGKILL in 2000 ms, continuing.
```

The fix is simple, don't use Homebrew to install browsers.

You simply install Firefox (or other browser) by downloading and installing it like you normally would from Mozilla's site. Make sure you uninstall it from Homebrew first if you already have it installed.
