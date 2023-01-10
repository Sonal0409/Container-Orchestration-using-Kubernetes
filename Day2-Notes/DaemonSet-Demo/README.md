
Lab execution Steps for DaemonSet demo:
========================================


Create Daemon Set in the cluster
===================================

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/DaemonSet-Demo/daemonset.yml

Validate if single pod is created on every worker node
====================================

kubectl get pods -o wide

   You will see 2 pods hasve been created on each Node
 
 kubectl get ds
 
    A daemonset is created with desired pods as 2
    
 
 Note:
 ========
 If a new node is added to the cluster,a new pod will be created on the new node also.
 Desired count would have increased to 3.
 
 Delete the DaemonSets:
 ====================
 
 kubectl delete daemonset myds
