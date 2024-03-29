
---
### TASK:
---
The Nautilus DevOps team is testing applications containerization, which is supposed to be migrated on docker container-based environments soon. In today's stand-up meeting one of the team members has been assigned a task to create and test a docker container with certain requirements. Below are more details:
1. On `App Server 1` in `Stratos DC` pull `nginx` image (preferably `latest` tag but others should work too).
2. Create a new container with name `official` from the image you just pulled.
3. Map the host volume `/opt/dba` with container volume `/tmp`. There is an `sample.txt` file present on same server under `/tmp`; copy that file to `/opt/dba`. Also please keep the container in running state.

---
### Answer:
---
### Steps:
- SSH into host.
- `docker pull nginx`
- `docker container run -d --name official -v /opt/dba:/tmp nginx`
- `cp /tmp/sample.txt /opt/dba/`
