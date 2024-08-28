# Create a namespace by using the following command:
...

kubectl create namespace role

# Create a directory role.
...

mkdir role
cd role

# Generating an RSA private key and certificate requests

# To generate an RSA private key, run the following command:
...

sudo openssl genrsa -out user3.key 2048

# 	Use the following command to generate certificate requests:

...

sudo openssl req -new -key user3.key -out user3.csr

Enter any details like:

•	Organization Name: namespace

•	Common Name: user3

# Run the following command to link an identity to a private key using a digital signature.

sudo openssl x509 -req -in user3.csr -CA /etc/kubernetes/pki/ca.crt -CAkey /etc/kubernetes/pki/ca.key -CAcreateserial -out user3.crt -days 500

# Creating role

To create a role, 

...

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day4-Notes/RBAC/role.yml

kubectl get roles -n role

# Creating a rolebinding

Create rolebinding by using the following command:

kubectl create -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day4-Notes/RBAC/rolebinding.yml

kubectl get rolebinding -n role


# Setting credentials to the user
Set credentials to user3.

kubectl config set-credentials user3 --client-certificate=/root/role/user3.crt --client-key=/root/role/user3.key

# Set context to user3.

kubectl config set-context user3-context --cluster=kubernetes --namespace=role --user=user3


# Run the following command to display current contexts:

kubectl config get-contexts


# Copying the config file to the client machine

Copy the config file from the master node in the home directory to the worker node.

cd ..

cat .kube/config

# Paste the copied config file into the client machine in root directory iteself.

vi myconf

copy the master config file contents to this file

# In the worker node

create a role directory

mkdir role

cd role

Copy the crt and key files from the master node to the worker  node in the /role directory.

keep the filename same as on master node

vim user3.crt

vim user3.key

# Locate the home directory.
cd ..

# Run the following commands to verify roles we have generated:

kubectl get pods --kubeconfig=myconf

Change context to make use of user3
...
kubectl config use-context user3-context --kubeconfig=myconf
...
Check the context
...
kubectl config get-contexts --kubeconfig=myconf
...

kubectl create deployment test --image=docker.io/httpd -n role --kubeconfig=myconf

kubectl get pods --kubeconfig=myconf

kubectl get deployment --kubeconfig=myconf


The worker node can create, update, remove, and list pods, services, and deployments after using the master config settings.






