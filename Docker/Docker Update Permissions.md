
---
### TASK:
---
One of the Nautilus project developers need access to run docker commands on `App Server 1`. This user is already created on the server. Accomplish this task as per details given below:  
User `javed` is not able to run docker commands on `App Server 1` in Stratos DC, make the required changes so that this user can run docker commands without `sudo`.

---
### Answer:
---
### Steps:
-  SSH into host.
-  `cat /etc/group | grep docker`
-  `usermod -aG docker javed`
-   Verify`su javed` and `docker ps`.
