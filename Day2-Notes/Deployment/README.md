Lab execution steps:
===================

Execute below steps:

Create the deployment object and Nodeport service:
===============================================

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/Deployment/deployment.yml

Validate:
===============================================

 kubectl get all
 
 kubectl get deployment kubeserve -o wide
 
 kubectl set image deploy kubeserve app=leaddevops/kubeserve:v2
 
 kubectl rollout status deploy kubeserve 
 
  kubectl get all
 
 kubectl get deployment kubeserve -o wide
 
 kubectl set image deploy kubeserve app=leaddevops/kubeserve:v3
  
  
lets rollback to older version of image:
====================================

 kubectl rollout undo  deploy kubeserve
 
Delete the deployment:
=================================

 kubectl delete deploy kubeserve
 
 kubectl get all
 
 
  
  
