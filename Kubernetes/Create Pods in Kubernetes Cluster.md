The Nautilus DevOps team has started practicing some pods and services deployment on Kubernetes platform as they are planning to migrate most of their applications on Kubernetes platform. Recently one of the team members has been assigned a task to create a pod as per details mentioned below:
1. Create a pod named pod-nginx using nginx image with latest tag only and remember to mention the tag i.e nginx:latest.
2. Labels app should be set to nginx_app, also container should be named as nginx-container.
---
### Answer:
---
<details>
  <summary>Create Nginx Pod</summary>

  Create a Pod definition file in `vi`, e.g. `nginx-pod.yaml` with the following YAML:

  ```yaml
  apiVersion: v1
  kind: Pod
  metadata:
    creationTimestamp: null
    labels:
      app: nginx_app
    name: pod-nginx
  spec:
    containers:
    - image: nginx:latest
      name: nginx-container
      resources: {}
    dnsPolicy: ClusterFirst
    restartPolicy: Always
  status: {}
  ```

</details>
<details>
  <summary>Run Nginx Pod</summary>

  Run the Pod using `kubectl apply -f nginx-pod.yaml` command.

</details>
<details>
  <summary>Verify Nginx Pod</summary>

  Verify the Pod using `kubectl get pods` command.  The pod should be running.

</details>