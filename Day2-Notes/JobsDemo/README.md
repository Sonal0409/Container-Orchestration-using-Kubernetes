Lab Execution Steps:
=====================

Create a job using below yaml file:
====================================

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/JobsDemo/job.yml

Validate:
====================================

kubectl apply -f job.yaml

kubectl get jobs -o wide

kubectl get pods -o wide

kubectl describe pod pi-wf7bm
