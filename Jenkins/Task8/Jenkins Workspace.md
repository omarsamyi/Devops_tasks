
---
### Task:
Some developers are working on a common repository where they are testing some features for an application. They are having three branches (excluding the master branch) in this repository where they are adding changes related to these different features. They want to test these changes on Stratos DC app servers so they need a Jenkins job using which they can deploy these different branches as per requirements. Configure a Jenkins job accordingly.

1. There is a Git repository named `web_app` on Gitea where developers are pushing their changes. It has three branches `version1`, `version2` and `version3` (excluding the `master` branch). You need not to make any changes in the repository.  
2. Create a Jenkins job named `app-job`.  
3. Configure this job to have a choice parameter named `Branch` with choices as given below:  `version1`  `version2`  `version3`  
4. Configure the job to fetch changes from above mentioned Git repository and make sure it should fetches the changes from the respective branch which you are passing as a choice in the choice parameter while building the job. For example if you choose `version1` then it must fetch and deploy the changes from branch `version1`.
5. Configure this job to use custom workspace rather than a default workspace and custom workspace directory should be created under `/var/lib/jenkins` (for example `/var/lib/jenkins/version1`) location rather than under any sub-directory etc. The job should use a workspace as per the value you will pass for `Branch` parameter while building the job. For example if you choose `version1` while building the job then it should create a workspace directory called `version1` and should fetch Git repository etc within that directory only.
6. Configure the job to deploy code (fetched from Git repository) on storage server (in Stratos DC) under `/var/www/html` directory. Since its a shared volume.
7. You can access the website by clicking on `App` button.

---
### Answer:
---
### Steps:
-  Install Plugins `Git, SSH, Publish over ssh`.
-  Add require credentials users `Gitea & SSH host`.
-  [System Configure] Add SSH server.
-  Create New job called `app-job`.
-  Add parameterized job and choices.
-  Use custom workspace `$JENKINS_HOME/$Branch`.
-  Add git repo and user credentials with branch `*/$Branch`.
-  On remote ssh host `chmod 777 /var/www/html/`
-  Configure the SSH publish to transfer files`**/*`.