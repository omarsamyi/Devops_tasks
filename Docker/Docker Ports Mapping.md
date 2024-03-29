
---
### TASK:
---
The Nautilus DevOps team is planning to host an application on a nginx-based container. There are number of tickets already been created for similar tasks. One of the tickets has been assigned to set up a nginx container on `Application Server 1` in `Stratos Datacenter`. Please perform the task as per details mentioned below:
1. Pull `nginx:stable` docker image on `Application Server 1`
2. Create a container named `news` using the image you pulled
3. Map host port `8085` to container port `80`. Please keep the container in running state.

---
### Answer:
---
### Steps:
 - SSH into the host.
 - `docker pull nginx:stable`.
 - `docker container run -d --name news -p 8085:80 nginx:stable`