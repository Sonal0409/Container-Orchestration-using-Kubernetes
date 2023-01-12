## Deploy MySQL Using Azure Dynamic Storage Class

## Creating an AKS cluster 

kubectl get nodes

kubectl get sc

## Create an Azure disk for dynamic persistent volume.

Create a persistent volume clam:

...

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day4-Notes/Volumes/azure-pvc.yml

...

## Deploy MySQL Pods with Azure disk as PVC.

...

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day4-Notes/Volumes/mysql-deployment.yml

...

## Validate:

kubectl get all

kubectl get pvc

kubectl get pvc

kubectl logs podName
