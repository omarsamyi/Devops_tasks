
---
### Task:
---
The devops team of xFusionCorp Industries is working on to setup centralised logging management system to maintain and analyse server logs easily. Since it will take some time to implement, they wanted to gather some server logs on a regular basis. At least one of the app servers is having issues with the Apache server. The team needs Apache logs so that they can identify and troubleshoot the issues easily if they arise. So they decided to create a Jenkins job to collect logs from the server. Please create/configure a Jenkins job as per details mentioned below:
1. Create a Jenkins jobs named `copy-logs`.  
2. Configure it to periodically build `every 10 minutes` to copy the Apache logs (`both access_log and error_logs`) from `App Server 2` (`from default logs location`) to location `/usr/src/itadmin` on `Storage Server`.

---
### Answer:
---
### Steps:
-  