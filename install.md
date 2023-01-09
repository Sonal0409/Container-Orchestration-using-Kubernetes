Go to the lab Master machine:

STEP 1: On Master Node Only:

Execute below commands to Configure Docker Daemon: 

sudo su –
 
sudo wget https://raw.githubusercontent.com/lerndevops/labs/master/kubernetes/0-install/daemon.json -P /etc/docker
   sudo systemctl restart docker.service
   sudo service docker status
## Initialize kubernetes Master Node
 
   sudo kubeadm init 
 
To fix the problem of The connection to the server localhost:8080 was refused - did you specify the right host or port?
 
 Run the below commands 
 
   sudo mkdir -p $HOME/.kube
   sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
   sudo chown $(id -u):$(id -g) $HOME/.kube/config
 
   ## install networking driver -- Weave/flannel/canal/calico etc... 
 
    sudo kubectl apply -f https://raw.githubusercontent.com/projectcalico/calico/v3.24.1/manifests/calico.yaml 
   
   # Validate:  kubectl get nodes


Step 2: ON ALL Worker Nodes


Configure Docker Daemon: 
sudo su - 
   sudo wget https://raw.githubusercontent.com/lerndevops/labs/master/kubernetes/0-install/daemon.json -P /etc/docker
   sudo systemctl restart docker.service
   sudo service docker status
## Run Below on Master Node to get join token 
 
sudo kubeadm token create --print-join-command 
 
    copy the kubeadm join token from master & run it on all nodes
 
    Ex: sudo kubeadm join 10.128.15.231:6443 --token mks3y2.v03tyyru0gy12mbt \
           --discovery-token-ca-cert-hash sha256:3de23d42c7002be0893339fbe558ee75e14399e11f22e3f0b34351077b7c4b56
 
Validate on master node

kubectl get nodes

kubectl get nodes -o wide
