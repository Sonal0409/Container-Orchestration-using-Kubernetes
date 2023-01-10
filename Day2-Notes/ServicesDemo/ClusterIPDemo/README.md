Lab Execution Steps:
======================

Delete all exisitng replicaSet
========================
kubectl delete replicaset myrs

Create Replicas using ReplicaSet YAML file
===========================================
kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/ReplicaSet-Demo/ReplicaSet.yml

kubectl get pods

kubectl get pods --show-labels

Create ClusterIp service
=============================

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/ServicesDemo/ClusterIPDemo/Service1.yml

Validate:
==============

kubectl get svc

Note down the service details:

mysvc1       ClusterIP   10.102.177.192   <none>        80/TCP    6m2s

Validate if a new pod is able to communicate with ngix replicas using cluster IP
================

create a new ubuntu pod for testing:

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/ServicesDemo/ClusterIPDemo/ubuntupod.yml

Check ubuntu pod is running:

kubectl get pods 

Log into Ubuntu pod

kubectl exec -it ubuntupod -- bash

Execute command to install curl package

apt-get update && apt-get install curl -y

Send a request to cluster ip, it will forward the request to any of the pod with target port as 80 and label as type=webserver
  
curl 10.102.177.192:80
