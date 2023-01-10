LAB Execution Steps:
==========================

Step1:

Delete all exisitng Pods
===========================

kubectl delete pods --all


Step2:

Create Replicas using ReplicaSet YAML file
=============================================

kubectl create -f  https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/ReplicaSet-Demo/ReplicaSet.yml


Step3:

Validate the creation of Replicas
===================================

 kubectl get all

 kubectl get pods

kubectl get pods -o wide

Scale up the replicas for the current replicaSet
=================================================

kubectl scale --replicas=5 replicaset rsname

Scale down the replicas for the current replicaSet
===================================================

 kubectl scale --replicas=2 replicaset rsname

  
  
