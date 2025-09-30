# 🚀 Kubernetes with Minikube – Nginx Deployment

This project demonstrates how to build a **local Kubernetes cluster using Minikube**, deploy an **Nginx application**, expose it via a **Service**, and test it locally.

---

## Install & Start Minikube

```bash
# Install Minikube (Linux example)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

# Start a local cluster (using Docker as driver)
minikube start --driver=docker

# Verify minikube config
minikube status
```

## Create a Deployment

Apply the deployment:
```bash
kubectl apply -f deployment.yaml
kubectl get pods
```
## Scale Down the Deployment
```bash
kubectl scale deployment k8s-web-to-nginx --replicas=2
kubectl get pods
```
## Inspect Resources
Describe a pod
```bash
kubectl describe pod <pod-name>
```
## View logs from a pod
```bash
kubectl logs <pod-name>
```

## Deliverables

>Note: deployment.yaml and service.yaml files in separated would be way better.


## Screenshots of:

Installation
  ![Bundle Image](images/1.png)

  ![Bundle Image](images/1.1.png)


---

kubectl get pods<br>
kubectl get svc
  ![Bundle Image](images/3.png)

  ![Bundle Image](images/2.png)


---

Curl showing Nginx webpage (minikube service nginx-service)
  ![Bundle Image](images/4.png)


---
Screenshot after scaling to 2 replicas.
  ![Bundle Image](images/5.png)


---
Screenshot of kubectl describe pod output.
  ![Bundle Image](images/6.png)

  ![Bundle Image](images/7.png)


# Troubleshooting

If curl inside a pod is missing:
```bash
kubectl run curlpod --rm -it --image=radial/busyboxplus:curl -- /bin/sh
curl http://nginx-service
```

If NodePort is not accessible directly, use:
```
minikube service nginx-service --url
```

> You now have a fully working Kubernetes cluster on Minikube with Nginx deployed and exposed! 🎉
