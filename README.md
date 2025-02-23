# jellyfin
Jellyfin Arr Suite configuration

# External services
sign up for GeekNZ account
https://www.nzbgeek.info/

and Eweka account
https://www.eweka.nl/en/

# create folder structure
Create folder structure as listed here, allows for easy / speedy transfers & connections between services
https://wiki.servarr.com/docker-guide#examples

# Deploy Host tools
Deploy Portainer & Watchtower

docker compose -f host-docker-compose.yaml up -d

# Deploy stack
Log into portainer http://localhost:9000

Stack / Add Stack
Either Upload docker-compose OR link to repository... deploy media-docker-compose.yml

# JellyFin setup
Log into jellyfin http://localhost:8096
Setup Library Folders to point to /data/media/ folders that were mapped in docker-compose

# SABnzbd setup
Log into sabnzdb http://localhost:8080

- Update Folders to point to /data/usernet/incomplete, /data/usenet/complete, /data/usenet/watch for Temporary Download Folder, Completed Download Folder, Watched Folder respectively 
- Add server based on Eweka creds created above (host/port/username/password)
- Update categories such that tv, movies, books, music are linked to the tv, movies, books, music folders located in the /data/usenet/completed paths
  
# Sonarr setup (TV Shows)
Log into sonarr http://localhost:8989

- Settings / Media Management, set a Root Folder to /data/media/tv
- Setting / Indexers, add new Newznab preset, selecting NBZGeek, Add API Key from GeekNZ account created above
- Settings / Download Clients, add new SABnzdb, adding host, port, API, username, password from SABnzbd setup above.  Ensure that category is 'tv' to match the category/folder setup from SABnzbd above

# Radarr setup (Movies)
Log into radarr http://localhost:7878

Follow the exact same steps from Sonarr, using the 'movies' folder, and category


NOTE:
- on top of SABnzbd downloader, you can also configure torrent downloader using the qtorrent instance included in this stack
