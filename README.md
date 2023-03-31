# test

Objective
Join 2 worker nodes to a Kubeadm cluster with 3 master nodes.

Prerequisites
3 Ubuntu 20.04 servers with at least 2 CPU and 4 GB RAM each.
The 3 servers must have unique hostname, IP address, and SSH access enabled.
A load balancer must be set up to distribute traffic among the 3 master nodes.
You must have root or sudo privileges on all servers.
Steps
On all 5 nodes:
SSH into each node using the command ssh <username>@<node-IP> and enter your password when prompted.

Update the package index and install the necessary packages by running the following command:

sql
Copy code
sudo apt-get update && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
Add the Kubernetes signing key by running the following command:

arduino
Copy code
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
Add the Kubernetes repository by running the following command:

csharp
Copy code
sudo add-apt-repository "deb https://apt.kubernetes.io/ kubernetes-xenial main"
Install Kubernetes by running the following command:

sql
Copy code
sudo apt-get update && sudo apt-get install -y kubelet kubeadm kubectl
On any of the 3 master nodes:
Initialize the cluster by running the following command:

php
Copy code
sudo kubeadm init --control-plane-endpoint "<LOAD_BALANCER_DNS>:<LOAD_BALANCER_PORT>" --upload-certs --apiserver-advertise-address=<MASTER_NODE_IP>
Replace <LOAD_BALANCER_DNS> with the DNS name or IP address of the load balancer, <LOAD_BALANCER_PORT> with the port number used for the load balancer, and <MASTER_NODE_IP> with the IP address of the current master node.

The output of this command will include a token and the command to join worker nodes to the cluster.

Copy the command generated in the output of the previous step to join worker nodes to the cluster.

On the 2 worker nodes:
Paste the command copied in step 7 to join the worker nodes to the cluster.

Verify that the worker nodes have joined the cluster by running the following command on any of the master nodes:

arduino
Copy code
kubectl get nodes
The output should show all the nodes in the cluster, including the 2 worker nodes.

Congratulations! You have successfully joined 2 worker nodes to a Kubeadm cluster with 3 master nodes.
