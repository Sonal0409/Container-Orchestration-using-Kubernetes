Lab Execution Steps:
====================

Delete all exisitng replicaSet
==============================

kubectl delete all --all

Create new replicaSet and Nodeport Service
===============================

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/ServicesDemo/NodePortDemo/Service2.yml

Validate:
===============================

kubectl get all

kubectl get svc

service/mysvc        NodePort    10.105.31.132    <none>        80:32111/TCP
  
Copy the node port.

  
Access the pod application by using MASTER VM desktop and node port
========================================

Go to Matser VM, and click on Desktop

Open the browser and give:

localhost:32111

You will see the request sent to your pod.


  
  
