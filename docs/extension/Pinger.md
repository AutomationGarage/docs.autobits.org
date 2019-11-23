---
id: Pinger
title: Pinger
sidebar_label: Pinger
---

lets you test reachability of computers and other hosts on network and measure network round-trip time.

List the hosts under `[Hosts]` section:
```ini
[Hosts]
Google = google.com
Wikipedia = wikipedia.org
Facebook = facebook.com
DNS1 = 8.8.8.8
DNS2 = 8.8.4.4
```
Use one line per host.
Text before the `=` sign is friendly, human-readable name of the host.
Text after the `=` sign is IP address or DNS name of the host to ping.