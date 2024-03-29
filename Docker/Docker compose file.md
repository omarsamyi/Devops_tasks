
---
### TASK:
--- 
The Nautilus application development team shared static website content that needs to be hosted on the `httpd` web server using a containerised platform. The team has shared details with the DevOps team, and we need to set up an environment according to those guidelines. Below are the details:
1. On `App Server 2` in `Stratos DC` create a container named `httpd` using a docker compose file `/opt/docker/docker-compose.yml` (please use the exact name for file).
2.  Use `httpd` (preferably `latest` tag) image for container and make sure container is named as `httpd`; you can use any name for service.
3. Map `80` number port of container with port `3000` of docker host.
4. Map container's `/usr/local/apache2/htdocs` volume with `/opt/security` volume of docker host which is already there. (please do not modify any data within these locations).

---
### Answer:
---
### Steps:
-  SSH into the host.
-  `sudo vi /opt/docker/docker-compose.yml`
```
version: '3'

services:

  httpd:

    container_name: httpd

    image: httpd:latest

    ports:

      - "3000:80"

    volumes:

      - /opt/security:/usr/local/apache2/htdocs
```