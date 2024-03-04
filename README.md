# docker-samba-file-server
Docker Compose configuration for a Samba file server

- [Samba](https://www.samba.org/) is software that allows Linux to share files with Microsoft Windows.
- This repository is a Samba file server inside [Docker Compose](https://docs.docker.com/compose/) that can be accessed from Windows systems as well as other computers on your network.
- This server comes with one default user and password.
- All files will be stored in the Docker Compose volume named `samba_storage`. 
- To ensure other devices can access these files over your network, make sure your firewall allows incoming traffic on port 445, which is used by Samba for file sharing.

To start the server, set the user name and password in environment variables.
This information is needed to connect to the server.
```bash
USER=samba
PASS=secret
docker compose up
```

To stop the server:
```bash
# Type Ctrl+C then
docker compose down
```

To connect to the server:
First, make sure that `smbclient` is installed. Then
```bash
smbclient -U samba --password secret //localhost/Data
```

# Author, Licence

This repository is copyright :copyright: 2024 by Alan Tseng

However, it uses other components that are covered by their respective licences:
- [Samba](https://www.samba.org/)
- [`dockurr/samba` Docker image](https://hub.docker.com/r/dockurr/samba)
