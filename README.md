## MEDIA STACK


1) clone this repo

```bash
git clone https://github.com/calinbule/media-stack.git .
```

2) rename the evv.sample file to .env then follow the instructions inside the file to define the necessary variables 

```bash
mv env.sample .env
```

3) set the executable flag on the install-media file

```bash
chmod +x install-media
```

4) run the install-media file to create the directory structure and create the docker cluster; this utility ca also be used to update the cluster if needed

```bash
./install-media
```
 -----

 For configuration purposes, in order to configure the various components of the cluster, we will ned the IPs of the individual containers. In order to generate the IP for a container we first need its name:

 ```bash
docker ps
```

```bash
CONTAINER ID   IMAGE                                      COMMAND                  CREATED          STATUS                    PORTS                                                                                 NAMES
b1949742da19   linuxserver/sonarr                         "/init"                  11 minutes ago   Up 11 minutes             0.0.0.0:8989->8989/tcp                                                                sonarr
51669defe111   linuxserver/transmission                   "/init"                  11 minutes ago   Up 11 minutes             0.0.0.0:9091->9091/tcp, 51413/tcp, 51413/udp                                          transmission
8a3383bb727a   linuxserver/radarr                         "/init"                  11 minutes ago   Up 11 minutes             0.0.0.0:7878->7878/tcp                                                                radarr
649128f315d8   plexinc/pms-docker                         "/init"                  11 minutes ago   Up 11 minutes (healthy)   1900/udp, 32410/udp, 8324/tcp, 32412-32414/udp, 32469/tcp, 0.0.0.0:32400->32400/tcp   plex
48fa2e8f26f4   ghcr.io/flaresolverr/flaresolverr:latest   "/usr/bin/dumb-init …"   11 minutes ago   Up 11 minutes             0.0.0.0:8191->8191/tcp                                                                flaresolverr
988aeaf790d7   linuxserver/jackett                        "/init"                  11 minutes ago   Up 11 minutes             0.0.0.0:9117->9117/tcp                                                                jackett
c825f6d47f85   linuxserver/bazarr                         "/init"                  11 minutes ago   Up 11 minutes             0.0.0.0:6767->6767/tcp                                                                bazarr
d55e07686317   jellyfin/jellyfin                          "/jellyfin/jellyfin"     11 minutes ago   Up 11 minutes (healthy)   0.0.0.0:8096->8096/tcp                                                                jellyfin
```

Using the name ofthe container we obtain its IP with the following command:

 ```bash
 docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' <container name>
```

Ex: 

 ```bash
 docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' plex
 172.21.0.2
```