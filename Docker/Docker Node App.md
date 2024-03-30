
---
### TASK:
---
There is a requirement to Dockerize a Node app and to deploy the same on `App Server 3`. Under `/node_app` directory on `App Server 3`, we have already placed a `package.json` file that describes the app dependencies and `server.js` file that defines a web app framework:
1. Create a `Dockerfile` (name is case sensitive) under `/node_app` directory:
	- Use any `node` image as the base image.
	- Install the dependencies using `package.json` file.
	- Use `server.js` in the `CMD`.
	- Expose port `6400`
2.  The build image should be named as `nautilus/node-web-app`.
3. Now run a container named `nodeapp_nautilus` using this image
	- Map the container port `6400` with the host port `8092`.
---
### Answer:
---
### Steps:
-  SSH into host.
-  Create `Dockerfile` inside the directory.
```
FROM node

COPY . .

RUN npm install

CMD ["node", "server.js"]

EXPOSE 6400
```
-  `docker build -t nautilus/node-web-app .`
-  `docker container run -d --name nodeapp_nautilus -p 8092:6400 nautilus/node-web-app`
-  Verify `curl http://localhost:8092`
