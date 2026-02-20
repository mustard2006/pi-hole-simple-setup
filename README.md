# pi-hole-simple-setup

I’m using Raspberry Pi Zero WH.

In this setup I installed Pi-hole on a Raspberry Pi Zero WH running OS Lite. It works as a network-level ad blocker, so all devices on the local network have ads filtered. Pi-hole can also be configured through a web interface using the Pi’s local IP in a browser.

## Requirements

* Raspberry Pi Zero WH
* MicroSD card (8 GB or larger)
* Micro-USB power supply
* Wi-Fi network
* PC with Linux or WSL
* Router with DHCP

## Setup Overview

Raspberry Pi OS Lite is installed with SSH and Wi-Fi enabled. The Pi is accessed via SSH and Pi-hole is installed just using the official script. The Wi-Fi interface `wlan0` is used, a common DNS provider like Cloudflare or Google is chosen, and a static IP is set (I used the dynamic IP from the router and made it static). The web interface is enabled and privacy mode is set to hide device and domain logs, showing only anonymous stats (the third option).

## Privacy and Logging

By default Pi-hole hides device and domain logs. You can reduce logging and SD card wear by adding `MAXDBDAYS=7` in the `pihole-FTL.conf` file. This keeps only the last 7 days of data.

If you want maximum privacy, you can install a recursive DNS resolver like 'unbound' so the Pi does not rely on external DNS providers, i personally did not try this so it's all up to you.

## Network Integration

To filter ads on all devices, set your router's DNS to the Pi's IP address, if not then only the Pi itself will filter ads.

**Note:** pi-hole blocks only network-level ads. Ads that are embedded inside websites, like streaming sites, are not filtered because they are served directly by the site.

## Recommendations

* Use a static IP or DHCP reservation for stability (I set a static ip to pi-hole device through routers interface)
* Keep privacy mode enabled
* Consider Unbound for full DNS privacy (if you actually need it)

## Result

After setup, you have a pi zero running Pi-hole, blocking ads for your whole network. You can use the web dashboard to manage pi-hole and check stats.
