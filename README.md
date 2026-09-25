# HomeServer
Repo Docker pour un media server complet qui tourne sur un **Lenovo** recyclé.

## Hardware Specs
- **Host:** BMAX B4 Turbo 
- **OS:** Debian 13 (Headless)
- **CPU:** Intel N150
- **Memory:** 16 GB GB
- **Storage:** 4 TB Seagate Ironwolf HDD (montée sur `/mnt/hdd`)
- **Performance:** 20 streams 1080p simultanés (5 en 4K)

## Features
- **VPN Protection:** tout le trafic torrent passe par **Private Internet Access** via `gluetun` (killswitch inclus)
- **Anti-bot bypass:** `byparr` pour contourner les protections Cloudflare sur les indexers
- **Media Stack:** Jellyfin, Sonarr, Radarr, Prowlarr, Bazarr
- **Download Client:** qBittorrent, protégé derrière le VPN
- **Requests:** Seerr pour gérer les demandes de films/séries
- **TV:** Dispatcharr + Viniplay pour la partie TV live
- **Monitoring:** Node-exporter (optionnel)
- **Management:** Portainer pour gérer les containers, Homepage comme dashboard d'accueil

## Services

| Service | Port | Rôle |
|---|---|---|
| Gluetun | 8080, 9696, 8191 | VPN + expose qBittorrent/Prowlarr/Byparr |
| Radarr | 7878 | Gestion films |
| Sonarr | 8989 | Gestion séries |
| Bazarr | 6767 | Sous-titres |
| Jellyfin | 8096, 8920 | Serveur media (transcodage HW via `/dev/dri`) |
| Seerr | 5055 | Demandes utilisateurs |
| Dispatcharr | 9191 | Gestion flux IPTV |
| Viniplay | 8998 | Lecteur IPTV |
| Portainer | 9443 | Admin Docker |
| Homepage | 3001 | Dashboard |
| Node-exporter | 9100 | Metrics (Prometheus) |

## Notes
- Réseau Docker `medianet` en bridge, MTU 1400 (nécessaire pour éviter les soucis de fragmentation avec le VPN)
- Jellyfin et Viniplay utilisent l'accélération GPU (`/dev/dri`), vérifie que les GID `992`/`44` correspondent bien à `render`/`video` sur ton host
