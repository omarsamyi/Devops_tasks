
---
Welcome to the `terraform challenge` series.  
In this challenge we will deploy several **Kubernetes resources** using **terraform**.  
Utilize `/root/terraform_challenge` directory to store your Terraform configuration files.

### TASKS:
-  Terraform version: `1.1.5` installed on controlplane?
-  Configure `terraform and provider` settings within `provider.tf` file with following specifications:  
	1. Configure terraform to use `hashicorp/kubernetes` provider.
	2. Specify the provider's local name: `kubernetes`.
	3. Provider version: `2.11.0`.
	4. Configure kubernetes provider with path to your `kubeconfig` file: `/root/.kube/config`.
-  Create a terraform resource `webapp-service` for kubernetes service with following specs:
	1.  Service name: `webapp-service`
	2.  Service Type: `NodePort`
	3.  Ports: Port: `8080`, NodePort: `30080`.
-  Create a terraform resource `frontend` for kubernetes deployment with following specs:  
	1. Deployment Name: `frontend` 
	2. Deployment Labels = `name: frontend`
	3. Replicas: `4`
	4. Pod Labels = `name: webapp`
	5. Image: `kodekloud/webapp-color:v1`
	6. Container name: `simple-webapp`
	7. Container port: `8080`

----
### Answer:
---
### Steps:
-  Install terraform version 1.1.5.
-  Create` provider.tf` configuration fille.
```
terraform{
	required_providers {
    kubernetes = {
      source = "hashicorp/kubernetes"
      version = "2.11.0"
    }
  }
}

provider "kubernetes" {
  config_path    = "/root/.kube/config"

}
```
-  Create `main.tf` configuration file.
```
resource "kubernetes_service" "webapp-service" {

  metadata {

    name = "webapp-service"

  }

  spec {

    type = "NodePort"

    port {

      port = 8080

      node_port = 30080

    }

  }

}

  

resource "kubernetes_deployment" "frontend" {

  metadata {

    name = "frontend"

    labels = {

      name = "frontend"

    }

  }

  spec {

    replicas = 4

    selector {

      match_labels = {

        name = "webapp"

    }

  }

    template {

      metadata {

        labels = {

          name = "webapp"

        }

      }

  

      spec {

        container {

          image = "kodekloud/webapp-color:v1"

          name  = "simple-webapp"

  

          port {

            container_port = 8080

          }

  

        }

      }

    }

  }

}
```
-  `terraform init, plan then apply`.