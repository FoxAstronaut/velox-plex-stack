# Plex Stack

- [Plex Media Server](https://github.com/linuxserver/docker-plex)
- [Sonarr](https://github.com/Sonarr/Sonarr) - TV Shows automation/organizing/file management
- [Radarr](https://github.com/Radarr/Radarr) - Movies automation/organizing/file management
- [Tautulli](https://github.com/Tautulli/Tautulli) - Plex usage/performance monitoring system
- [Organizr](https://github.com/causefx/Organizr) - Single web portal that embeds other web UI's, such as Sonarr, Radarr etc
- [Portainer](https://github.com/portainer/portainer) - Graphical Docker container management tool
- [Qbittorrent](https://github.com/qbittorrent/qBittorrent) - Torrent client
- [Overseerr](https://github.com/sct/overseerr) - Web portal where users can log in with their Plex account and request movies/shows. Plex/Radarr/Sonarr integration
- [Bazarr](https://github.com/morpheus65535/bazarr) - Automatic subtitle management/download
- [Prowlarr](https://github.com/Prowlarr/Prowlarr) - Integrates with Radarr/Sonarr to manage their indexer/client settings in one place.
- [Kometa](https://github.com/Kometa-Team/Kometa) (aka Plex Meta Manager) - Tool for customizing Plex library metadata. For example custom posters, collections, etc.

## Install Steps

1. Clone the repo

2. Now make a copy of the example env file and open it in a text editor

3. Change the config according to your needs. The last line is for the Plex token, keep in mind that it is only valid for 4 minutes after generation (you can generate a new one if it expires too quickly)

4. Start the stack.:

```
docker compose -f /opt/plex-stack/docker-compose.yml up --detach
```

And remove the included example env file:

```
rm .env.example
```

5. Go to `http://localipofserver:32400/web` and log in with your Plex account to claim the server

6. Go to Settings > Remote Access and verify connectivity (green lock)



## Configuration

All of these programs needs to be configured, which is outside the scope of this guide. [TRaSH-Guides](https://trash-guides.info/) has great detailed guides for setting everything up.

Almost all of them are configured via web GUIs. Organizr is a great tool that can be used to organize all links into a single web portal. Each web gui is bound to it's own port on the host in this example, using unencrypted http. Therefore they should not be reachable from the internet via port forwarding. A reverse proxy can be used to proxy all traffic to each service with domain names, HTTPS, additional authentication etc. Traefik is the proxy I prefer, but setting it up is something that is also outside the scope of this guide at the moment.

## Troubleshooting

Portainer is a great graphical tool that you can use to manage/monitor your containers. It can be reached via http://ipofserver:9000/. You will have to create a password for the admin account, then you should see your environment under home. Here you can read logs, restart containers, recreate, remove etc.

Indentation is also important when working with .yml files, usually docker compose will be able to tell you which line is wrong but incorrect indentation can lead to unexpected/weird errors so watch out for that when copying/pasting stuff for example.

If your server says it's unavailable remotely, it's probably due to one of these things:

* You are behind a CGNAT connection, which means you share one public IP with many others, and can't forward ports yourself. CGNAT addresses start with 100. Some ISPs can give you a real public IP if you request it, often for free.

* You have not forwarded ports correctly. Check your routers port forwarding settings.

* You are double NATed. You sit behind a router, which has it's WAN port connected to another router (sometimes the ISPs depending on country).

You can easily test port connectivity using telnet. [Here](https://kb.synology.com/vi-vn/DSM/tutorial/Whether_TCP_port_is_open_or_closed) is a link explaining how to do it.

If telnet can connect directly to the servers local IP on TCP 32400, the issue is probably the router settings, either your own or some upstream ISP router.