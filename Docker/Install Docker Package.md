
---
### TASK:
---
Last week the Nautilus DevOps team met with the application development team and decided to containerize several of their applications. The DevOps team wants to do some testing per the following:
1. Install `docker-ce` and `docker-compose` packages on `App Server 2`.
2. Start `docker` service.
---
### Answer:
---
### Steps:

For Docker:
-  SSH into the server.
-  `sudo yum install -y yum-utils device-mapper-persistent-data lvm2`
-  `yum-config-manager  --add-repo https://download.docker.com/linux/centos/docker-ce.repo`.
- `yum install docker-ce` and enable docker `systemctl enable docker`.
-  Start docker: `systemctl start docker`

For Docker-compose:
-  `curl -L "https://github.com/docker/compose/releases/download/1.23.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose`.
-  `chmod +x /usr/local/bin/docker-compose`.
-  `ln -s /usr/local/bin/docker-compose /usr/bin/docker-compose`.
-  `docker-compose --version`.
