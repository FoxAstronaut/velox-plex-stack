# Docker Media Stack

Media stack for managing and streaming media

## Containers

### Media
- [Plex](https://github.com/linuxserver/docker-plex) - Media streaming server
- [Sonarr](https://github.com/Sonarr/Sonarr) - TV request automation, organisation & file management
- [Radarr](https://github.com/Radarr/Radarr) - Movie request automation, organisation & file management
- [Qbittorrent](https://github.com/qbittorrent/qBittorrent) - Download client
- [Tautulli](https://github.com/Tautulli/Tautulli) - Plex usage/performance monitoring system
- [Bazarr](https://github.com/morpheus65535/bazarr) - Automatic subtitle management/download
- [Prowlarr](https://github.com/Prowlarr/Prowlarr) - Manages Radarr & Sonarr indexer and client settings
- [Plex Meta Manager aka Kometa](https://github.com/Kometa-Team/Kometa) - Tool for customizing Plex library metadata

### Docker Management & Monitoring
- [Portainer](https://github.com/portainer/portainer) - Graphical Docker container management tool
- [Prometheus](https://github.com/prometheus/prometheus) - Monitoring system and time series database
- [Node Exporter](https://github.com/prometheus/node_exporter) - Export hardware and system metrics
- [Grafana](https://github.com/grafana/grafana) - Pretty graphs
- [CAdvisor](https://github.com/google/cadvisor) - Monitors container resource usage and performance

### Networking
- [Nginx Proxy Manager](https://github.com/NginxProxyManager/nginx-proxy-manager) - Reverse proxy with admin web UI

### Future
- Music - Server options - Symfonium, Lidarr. Clients options - Navidrome, Feishin
- Photos - Server options - Lychee, Piwigo. Clients options - Photoprism, Chevereto

## Install Steps

1. Clone this repo

2. Make a rename or copy  the `.env.example` to `.env`

3. Set your Plex token & set a in the `.env` file

Tip: It expires pretty quickly so I had to restart the plex container a couple times idk the if it will just refresh if the `.env` changes

4. Start the stack with `docker compose up` (You can add `-d` to run it in the background)

5. Once everything starts up you can go to `http://whateveryouripis:32400/web` and claim your plex server. Then mess around with settings for 4 hours

## Configuration

Most of the setup is based off of [TRaSH-Guides](https://trash-guides.info/) but checkout the linked github repos above as they mostly have good docs

## Credit
This started as a fork of [btstromberg/plex-stack](https://github.com/btstromberg/plex-stack) so alot of credit to them for getting the initial setup in a somewhat working state