
---
### TASK:
---
A python app needed to be Dockerized, and then it needs to be deployed on `App Server 3`. We have already copied a `requirements.txt` file (having the app dependencies) under `/python_app/src/` directory on `App Server 3`. Further complete this task as per details mentioned below:
1. Create a `Dockerfile` under `/python_app` directory:
	- Use any `python` image as the base image.
	- Install the dependencies using `requirements.txt` file.
	- Expose the port `8085`.
	- Run the `server.py` script using `CMD`.
2.  Build an image named `nautilus/python-app` using this Dockerfile
3.  Once image is built, create a container named `pythonapp_nautilus`:
    - Map port `8085` of the container to the host port `8092`.
4. Once deployed, you can test the app using `curl` command on `App Server 3`.

---
### Answer:
---
### Steps:
-  SSH into host.
-  Create `Dockerfile`.
```
FROM python:3

WORKDIR /usr/src/app

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD [ "python", "./server.py" ]

EXPOSE 8085
```
-  `docker build -t nautilus/python-app .`
-  `docker container run -d --name pythonapp_nautilus -p 8092:8085 nautilus/python-app`