One of the DevOps team members was working on to create a new custom docker image on `App Server 1` in `Stratos DC`. He is done with his changes and image is saved on same server with name `ecommerce:datacenter`. Recently a requirement has been raised by a team to use that image for testing, but the team wants to test the same on `App Server 3`. So we need to provide them that image on `App Server 3` in `Stratos DC`.
1. On `App Server 1` save the image `ecommerce:datacenter` in an archive.
2.  Transfer the image archive to `App Server 3`.
3. Load that image archive on `App Server 3` with same name and tag which was used on `App Server 1`.
4. `Note:` Docker is already installed on both servers; however, if its service is down please make sure to start it.

---
### Answer:
---
### Steps:
-  SSH into server 1.
- `docker image save ecommerce:datacenter > ecommerce.tar`.
- `scp ecommerce.tar banner@stapp03:/home/ .
-  SSH into server 3.
- `docker load < ecommerce.tar`