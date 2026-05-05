# HomeServer
This repository contains the Docker configuration for a full-stack media server running on a recycled **Lenovo**.

## Hardware Specs
- **Host:** Lenovo X1 Yoga 1st Gen (Signature Edition)
- **OS:** Debian 13 (Headless)
- **CPU:** Intel Core i5
- **Storage:** 4TB Seagate Ironwolf HDD (Mounted at `/mnt/hdd`)
- **Performance:** Capability of 6-10 simultaneous 1080p streams.

## Features
- **VPN Protection:** All torrent traffic is routed through **Private Internet Access** via `gluetun`.
- **Media Stack:** Jellyfin, Sonarr, Radarr, Prowlarr, and Bazarr.
- **Download Client:** qBittorrent protected by killswitch.
- **Monitoring:** Node-exporter (optionnal)
