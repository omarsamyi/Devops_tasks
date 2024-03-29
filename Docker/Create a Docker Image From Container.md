
---
### TASK:
---
One of the Nautilus developer was working to test new changes on a container. He wants to keep a backup of his changes to the container. A new request has been raised for the DevOps team to create a new image from this container. Below are more details about it:
a. Create an image `ecommerce:xfusion` on `Application Server 3` from a container `ubuntu_latest` that is running on same server.

---
### Answer:
---
### Steps:
-  SSH into host.
-  `docker commit -a "Developer" ubuntu_latest ecommerce:xfusion`
-  Verify: `docker image ls`
