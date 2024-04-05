
---
### TASK:
---
The Nautilus Application development team recently finished development of one of the apps that they want to deploy on a containerized platform. The Nautilus Application development and DevOps teams met to discuss some of the basic pre-requisites and requirements to complete the deployment. The team wants to test the deployment on one of the app servers before going live and set up a complete containerized stack using a docker compose fie. Below are the details of the task:
1. 1. On `App Server 1` in `Stratos Datacenter` create a docker compose file `/opt/security/docker-compose.yml` (should be named exactly).
2. 1. The compose should deploy two services (web and DB), and each service should deploy a container as per details below:
3. After running docker-compose up you can access the app with curl command `curl <server-ip or hostname>:3001/`

For web service:
1. Container name must be `php_web`.
2. Use image `php` with any `apache` tag. Check [here](https://hub.docker.com/_/php?tab=tags/) for more details.
3.  Map `php_web` container's port `80` with host port `3001`
4. Map `php_web` container's `/var/www/html` volume with host volume `/var/www/html`.

For DB service:
1. Container name must be `mysql_web`.
2. Use image `mariadb` with any tag (preferably `latest`). Check [here](https://hub.docker.com/_/mariadb?tab=tags/) for more details.
3. Map `mysql_web` container's port `3306` with host port `3306`
4.  Map `mysql_web` container's `/var/lib/mysql` volume with host volume `/var/lib/mysql`.
5. Set MYSQL_DATABASE=`database_web` and use any custom user ( except root ) with some complex password for DB connections.
----
### Answer:
---
### Steps:
1. SSH into host server.

2. <details>
<summary>Create `docker-compose.yml` file.</summary>

version: '3'

services:

  php_web:

    container_name: php_web

    image: php:apache

    ports:

      - "3001:80"

    volumes:

      - /var/www/html:/var/www/html

  mysql_web:

    container_name: mysql_web

    image: mariadb:latest

    ports:

      - "3306:3306"

    volumes:

      - /var/lib/mysql:/var/lib/mysql

    environment:

        - MYSQL_ROOT_PASSWORD=P@ssw0rd

          MYSQL_DATABASE=database_web

          MYSQL_USER=kkloud

          MYSQL_PASSWORD=P@ssw0rd

</details>
