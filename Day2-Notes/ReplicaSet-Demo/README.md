## ReplicaSet

> A ReplicaSet's purpose is to maintain a stable set of replica Pods running at any given time. 

> As such, it is often used to guarantee the availability of a specified number of identical Pods.

> **A ReplicaSet is defined with fields, including** 

* a selector that specifies how to identify Pods it can acquire, 
* a number of replicas indicating how many Pods it should be maintaining, 
* and a pod template specifying the data of new Pods it should create to meet the number of replicas criteria. 

> A ReplicaSet then fulfills its purpose by creating and deleting Pods as needed to reach the desired number. When a ReplicaSet needs to create new Pods, it uses its Pod template.


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

kubectl scale --replicas=5 replicaset myrs

kubectl get pods -o wide

Scale down the replicas for the current replicaSet
===================================================

 kubectl scale --replicas=2 replicaset myrs
 
 kubectl get pods -o wide

 Delete Replicaset
 ==============================
 
 kubectl delete replicaset myrs
  
