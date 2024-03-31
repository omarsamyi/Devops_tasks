
---
## Task5:

---

Some new requirements have come up to install and configure some packages on the Nautilus infrastructure under Stratos Datacenter. The Nautilus DevOps team installed and configured a new Jenkins server so they wanted to create a Jenkins job to automate this task. Find below more details and complete the task accordingly:  
  
Click on the `Jenkins` button on the top bar to access the Jenkins UI. Login using username `admin` and `Adm!n321` password.  

Create a Jenkins job named `install-packages` and configure it to accomplish below given tasks.  

- Add a string parameter named `PACKAGE`.
- Configure it to install a package on the `storage server` in `Stratos Datacenter` provided to the `$PACKAGE` parameter.


---

## Answer:

---

#### Steps:
 -  Install `SSH Credentials`, `SSH`, `SSH agent` plugin.
 -  [Security]  > `Credentials` > `Global` add credentials.
 - [ Configure System] > add `SSH remote hosts`.
 -  Create `New Item` called `install-packages`.
 -  Under `Configure`: 
		 -  [x] This project is parameterized.
		 -  Add `String Parameter` `PACKAGE`.
		 -  [Build Environment] : Execute Shell.
		 - [Pre Build Script] : `echo "P@SS" | sudo -S yum -y install $PACKAGE` .
		 - Build with Parameters > ex. `curl`.