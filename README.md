# Introduction

Privoxy is a privacy enhancer tool to setup a http proxy to block ads and undesired hosts.
It does more things, but we will use it as a http to socks5 bridge to gateway to tor network (using the browser)


# Requirements

- Android device
- Tor Browser installed (https://torproject.org/download/#android)
- Termux installed on Android (download recommended from F-Droid)
- git package installed on termux `apt update; apt install git`


# Installation (on Termux)

```bash
git clone https://github.com/xnikotecx/privoxy-tor-android-termux
cd privoxy-tor-android-termux/
./setup.sh
```

# How to start using it

On termux, from the cloned repo root path:

```bash
./privoxy.start
```

Open the Tor Browser, and keep it open (otherwise http proxy won't be able to communicate to socks5 proxy)

Now configure every Wifi Network to use an http proxy (on Proxy Section that should exist, of course)

Proxy Host `127.0.0.1` Proxy Port: `9051`

Or complete URL if required: http://127.0.0.1:9051

Wolaah! You are now using your Tor Browser's bridge for every App!!


## Important NOTICE

Keep in mind that system Apps could be able to avoid the proxy.
As well as an Android app creating an http/https request spawning a new process that is not dalvik, will not use this proxy.

This proxy will be used by every App if using a normal Android System-wide dalvik JAVA API for accesing the internet (http/https)

You shoud see kbs of traffic going throught tor on Notifications Bar (Tor Browser notification status) OR using `tcpdump -i wlan0` if available
Using tcpdump, you should see traffic going to the tor guard and back to you.

I also recommend you to hit the "NEW IDENTITY" button on Tor Browser Notification status once in a while.

DNS requests will still be leaked. This setup provides well enough privacy against surveillance and fingerprinting, but... for a completely anonymous experience, use the actual Tor Browser.
