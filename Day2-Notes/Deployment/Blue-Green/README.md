Steps for Lab

Step1:

...
Execute the below command to deploy v1 of the application in the blue environment.
...

# kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/Deployment/Blue-Green/deployment-blue.yml

Check if deployment and service is created or not

# kubectl get all

Access the application from browser, you will see v1.

Step 2:

...
Execute the below command to deploy v2 of the application in green environment.
...

# kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/Deployment/Blue-Green/deployment-green.yml

Check if v2 deployment and service is created or not

# kubectl get all

Access the application from browser, you will see v2.


Step 3: 

...
Now Change the service YAMl file of blue deployment and update the label version: v2
...

kubectl apply -f deployment-blue.yml

You will observe that service-blue is now sending traffic to v2 of the application.

Step 4:

Go ahead and delete deployment for v1 and service of v2
