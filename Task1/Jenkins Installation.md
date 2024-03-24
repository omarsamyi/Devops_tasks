
---

## Task1:
#### 1. Install `jenkins` on jenkins server using `yum` utility only, and start its `service`. You might face timeout issue while starting the Jenkins service, please refer [this](https://www.jenkins.io/doc/book/system-administration/systemd-services/#starting-services) link for help.  

#### 2. Jenkin's admin user name should be `theadmin`, password should be `Adm!n321`, full name should be `Ammar` and email should be `ammar@jenkins.stratos.xfusioncorp.com`.



---
## Answer:

#### Step 1:  Update and install jenkins package

````
sudo wget -O /etc/yum.repos.d/jenkins.repo \
    https://pkg.jenkins.io/redhat-stable/jenkins.repo
````
````
sudo rpm --import https://pkg.jenkins.io/redhat/jenkins.io-2023.key
````
````
sudo yum upgrade
````
````
# Add required dependencies for the jenkins package
sudo yum install fontconfig java-17-openjdk
sudo yum install jenkins
````

#### Step2: Start Jenkins

`sudo systemctl enable jenkins`
`sudo systemctl start jenkins`
`sudo systemctl status jenkins`

// Default port : `8080`
// Admin Password : `cat /var/lib/jenkins/secrets/initialAdminPassword`

---


#### Screenshots
![[Jenkins Installation-20240324201001894.webp]]

![[Jenkins Installation-20240324201002015.webp]]