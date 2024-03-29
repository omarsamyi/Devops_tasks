
---
### TASK:
---
The Nautilus DevOps team is working to deploy one of the applications on `App Server 1` in `Stratos DC`. Due to a misconfiguration in the docker compose file, the deployment is failing. We would like you to take a look into it to identify and fix the issues. More details can be found below:
1. `docker-compose.yml` file is present on `App Server 1` under `/opt/docker` directory
2. Try to run the same and make sure it works fine.
3.  Please do not change the `container names` being used. Also, do not update or alter any other valid config settings in the compose file or any other relevant data that can cause app failure.
4. `Note:` Please note that once you click on `FINISH` button all existing running/stopped containers will be destroyed, and your compose will be run.

---
### Answer:
---
### Steps:
-  Make sure docker-compose file is in the same of app folder.
-  Fix typos
```
version: '3'
services:
    web:
        build: .
        container_name: python
        ports:
            - "5000:5000"
        volumes:
            - .:/code
        depends_on:
            - redis
    redis:
        image: redis
        container_name: redis
```