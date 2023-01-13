## Create an NFS server       

...

sudo su
mkdir -p /data
ls -alrt /data/

...

## Install the NFS kernel server on the machine

...

sudo apt install nfs-kernel-server

...

## Change the owner user and group to nobody and nogroup

...

sudo chown nobody:nogroup /data/

Set permissions to 777 to allow everyone to read, write, and execute files in this directory

sudo chmod 777 /data/

...

## Open the exports file in the /etc directory for permission to access the host server machine

...

sudo vi /etc/exports

Add the following code to the file:

/data 	*(rw,sync,no_root_squash)

Note: Exit the file and save the changes

...

Here:
/data – is the share folder which server wants to share
rw – This will all the clients to read and write the files to the share directory.
sync – which will confirm the shared directory once the changes are committed.
no_root_squash – This will all the root user to connect to the designated directory.

## Use the exportfs command to export all shared folders you registered in the /etc/exports file after making the appropriate changes

sudo exportfs -rv

## Restart the NFS kernel server to apply the configuration changes

sudo systemctl restart nfs-kernel-server

## Deploy NFS client on worker nodes

sudo apt install nfs-common

## Create a MySQL manifest file and deploy it using NFS-based persistent volume

...

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day5-Notes/mysql.yml

...

Note: The below section may change if you have a different NFS server and share folder available:

  nfs:
    path: /data
    server: 172.31.58.69


kubectl get all

kubectl get pv

kubectl get pvc

kubectl get pods

## Create a WordPress manifest file and deploy it using host-path-based persistent volume

...

kubectl apply -f https://raw.githubusercontent.com/Sonal0409/Container-Orchestration-using-Kubernetes/main/Day5-Notes/wordpress.yml

...

kubectl get all

kubectl get pv

kubectl get pvc

kubectl get pods

Then, open the browser and put the below URL to access the WordPress application
http://localhost:<node_port>



