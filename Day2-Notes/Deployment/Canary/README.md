Step1:

Deploy the v1 of the app. It willc reate deployment and service

# kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/Deployment/Canary/deploy-v1.yml

Step 2:

Deploy only pods of v2. In this strategy we dont create a new service

# kubectlc reate -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day2-Notes/Deployment/Canary/deploy-v2.yml

Step 3:

Edit the service yaml and reve metadata version:v1 and selector varion: v1

New service yaml should be link this:

---
kind: Service
apiVersion: v1
metadata:
   name: service-canary1
spec:
  type: NodePort
  ports:
    - port: 80
      targetPort: 80
  selector: 
    app: kubeserve
