
---
### TASK:
---
As per recent requirements shared by the Nautilus application development team, they need custom images created for one of their projects. Several of the initial testing requirements are already been shared with DevOps team. Therefore, create a docker file `/opt/docker/Dockerfile` (please keep `D` capital of Dockerfile) on `App server 3` in `Stratos DC` and configure to build an image with the following requirements:
1.  Use `ubuntu` as the base image
2. Install `apache2` and configure it to work on `8086` port. (do not update any other Apache configuration settings like document root etc).
---
### Answer:
---
### Steps:
-  SSH into the host.
-  vi `/opt/docker/Dockerfile`.

```
FROM ubuntu
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get update -y && apt-get install -y apache2
RUN sed -i "s/80/8085/g" /etc/apache2/ports.conf
EXPOSE 8085
CMD ["apachectl", "-D", "FOREGROUND"]

```

- `docker build -t apache2 /opt/docker/Dockerfile.`