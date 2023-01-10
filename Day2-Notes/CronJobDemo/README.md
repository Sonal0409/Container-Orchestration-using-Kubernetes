Lab Execution steps:
===========================

Create a new cron job that will create a job every minute

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/CronJobDemo/cronjob.yml

Validate
========

kubectl get cronjob

kubectl get cronjob hello

You should see that the cron job hello successfully scheduled a job at the time specified in LAST SCHEDULE. 

kubectl delete cronjob hello
