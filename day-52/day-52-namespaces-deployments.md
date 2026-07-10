kubectl get namespaces -> list all namespaces
kubectl get pods -n kube-system -> check the kubernetes system pods

create the custom namespace
============================
kubectl create namaspace dev 
kubectl create namespace staging 

create a namespace  using yml
=============================

apiVersion: v1
kind: Namespace
metadata:
    name: production

kubectl apply -f namespace.yml


kubectl get ns -> to list all the namespace

deployment pods
===============
kubectl run nginx-dev --image=nginx:latest -n dev
kubectl run nginx-staging --image=nginx:latest -n staging



kubectl get pods -n dev - to verify the dev pod

kubectl get pods -n staging - to verify the staging pod


kubectl get pods -A - to list all namespaces



kubectl get pods - check all default namespace


Q1. Does kubectl get pods show the nginx pods?
----------------------------------------------
Ans: No
Because it only shows resources in the default namespace.

Q2. Does kubectl get pods -A show them?
----------------------------------------
Ans: Yes


It lists pods from all namespaces, including:

dev
staging
kube-system
default
kube-public
kube-node-lease

