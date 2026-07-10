### Task 1: Deploy the Application
First, create a Deployment that you will expose with Services. Create `app-deployment.yaml`:


apiVersion: apps/v1
kind: Deployment
metadata:
  name: web-app
  labels:
    app: web-app
spec:
  replicas: 3
  selector:
    matchLabels:
      app: web-app
  template:
    metadata:
      labels:
        app: web-app
    spec:
      containers:
      - name: nginx
        image: nginx:1.25
        ports:
        - containerPort: 80

kubectl apply -f app-deployment.yaml
kubectl get pods -o wide

output
------
ubuntu@ip-172-31-12-108:~/task$ kubectl apply -f app-deployment.yml
deployment.apps/web-app created
ubuntu@ip-172-31-12-108:~/task$ kubectl get pods
NAME                       READY   STATUS    RESTARTS   AGE
web-app-5c44989c65-7tpk7   1/1     Running   0          9s
web-app-5c44989c65-lf4xt   1/1     Running   0          9s
web-app-5c44989c65-zzsqf   1/1     Running   0          9s
ubuntu@ip-172-31-12-108:~/task$ kubectl get pods -o wide
NAME                       READY   STATUS    RESTARTS   AGE   IP            NODE                           NOMINATED NODE   READINESS GATES
web-app-5c44989c65-7tpk7   1/1     Running   0          27s   10.244.0.23   devops-cluster-control-plane   <none>           <none>
web-app-5c44989c65-lf4xt   1/1     Running   0          27s   10.244.0.22   devops-cluster-control-plane   <none>           <none>
web-app-5c44989c65-zzsqf   1/1     Running   0          27s   10.244.0.24   devops-cluster-control-plane   <none>           <none>
