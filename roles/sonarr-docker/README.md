# Sonarr Docker

An Ansible role that installs Sonarr using LinuxServer's Sonarr image

[https://hub.docker.com/r/linuxserver/sonarr/](https://hub.docker.com/r/linuxserver/sonarr/)

My Sonarr configuration

-   Standard Episode Format: `{Series.Title}.S{season:00}E{episode:00}.{Episode.Title}.{Quality.Full}.{Release.Group}`
-   Daily Episode Format: `{Series.Title}.{Air-Date}.{Episode.Title}.{Quality.Full}`
-   Anime Episode Format: `{Series.CleanTitle}.S{season:00}E{episode:00}.{absolute:000}.{Episode.Title}.{Quality.Full}.{Release.Group}`
-   Series Folder Format: `{Series Title}`
-   Season Folder Format: `Season {season:00}`
-   Multi-Episode Style: `Scene`
