Lab Execution Steps
====================

Deploy Spring Java Application & MongoDB Pods
===========================================

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day%203%20-%20Notes/Networking/policies/springboot-mongo-app.yml

Access the Sping Java Application & write some data to mongo db
================================================

kubectl get services springboot-app-svc

use the NodPort to access the springboot java in the browser 

this proves that the You are able to access application from app pods

app is able to communicate to mongodb pods & write the data to it


Now lets block the request / traffic to springa app & mongo db using Network Policies
===================================================

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day%203%20-%20Notes/Networking/policies/deny-ingress-to-mongodb-and-springapp.yaml

kubectl get netpol

Now try to access application from browser it shoudn't respond
====================================================

kubectl get services springboot-app-svc

use the NodPort to access the springboot java in the browser 

This proves we successfully block all ingress (incoming) traffic to spring app

Now lets allows ingress(incoming) traffic to spring java app fromm all using Network Policies
========================================================

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day%203%20-%20Notes/Networking/policies/allow-ingress-to-springapp-from-all.yaml

kubectl get services springboot-app-svc

use the NodPort to access the springboot java in the browser

This should allow the traffic to Spring java App & you should see the app in browser

But if you try to submit the data to DB it will not respond, we still need to allow traffic to mongodb

Now lets allow ingress(incoming) traffic to mongodb only from spring app pods using Network Policies
==================================================================

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day%203%20-%20Notes/Networking/policies/allow-ingress-to-mongodb-from-springapp.yaml

Now we should be able to write the data to mongodb from spring java app
