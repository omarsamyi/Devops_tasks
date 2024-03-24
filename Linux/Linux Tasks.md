
---

### Task1:
	a. Create a user named `john` on the `App server 1` in Stratos Datacenter.  
	b. Set its UID to `1693` and home directory to `/var/www/john`.
### Answer:
-  SSH into `App server 1`
- `useradd -u UID -d HOME USERNAME`
-  `id USER` 

---
### Task2:
		a. Create a group named `nautilus_sftp_users` in all App servers in `Stratos Datacenter`.
		b. Add the user `mohammed` to `nautilus_sftp_users` group in all App servers. (create the user if doesn't exist).

### Answer:
-  `sudo useradd USERNAME`.
-  `sudo groupadd GROUPNAME`.
-  `sudo usermod -aG GROUPNAME USERNAME`.
-  << `sudo groupadd GROUPNAME` >>.
-  `sudo useradd USERNAME -g GROUPNAME`.
-  << `sudo groupadd GROUPNAME; useradd USERNAME -g GROUPNAME` >>.

---
