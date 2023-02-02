# Homework 11 - Docker. Setup Kubernetes

## Task - Setup Kubernetes

Prepare 2 VMs (kubemaster and kubenode) with the same parametrs

Requirements:
* 4 CPU
* 8 GB RAM
* Ubuntu (only for this task)
 
## Part 1 - prepare 2 VMs

#### I created a 2 VMs in digitalocean with the following settings:

<img width="1236" alt="Screenshot 2023-01-30 at 12 21 34" src="https://user-images.githubusercontent.com/117667360/215450915-da624009-bf2b-4bca-a87c-2226644ec567.png">



#### First of all I added a new user "kubeuser" to the system and added him to the sudo group.

## Part 2 - Setup Kubernetes

### Steps:

* Run commands in two VMs (kubemaster and kubenode)
```
sudo apt update
sudo apt upgrade -y
```

* Edit the hosts file with the command:
```
sudo nano /etc/hosts

Put your private IP address and hostname
```
![image](https://user-images.githubusercontent.com/117667360/216337564-b9cc4d83-9059-42ca-abdc-60512b6f38af.png)

* Save and exit

* Install the first dependencies with:
```
sudo apt install curl apt-transport-https -y
```
* Next, add the necessary GPG key with the command:
```
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
```
* Add the Kubernetes repository with:
```
echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
* Update apt:
```
sudo apt update
```
* Install the required software with the command:
```
sudo apt -y install vim git curl wget kubelet kubeadm kubectl
```
* Place kubelet, kubeadm, and kubectl on hold with:
```
sudo apt-mark hold kubelet kubeadm kubectl
```
* Start and enable the kubelet service with:
```
sudo systemctl enable --now kubelet
```
* Next, we need to disable swap on both kubemaster. Open the fstab file for editing with:
```
sudo nano /etc/fstab
```
* Save and close the file. You can either reboot to disable swap or simply issue the following command to finish up the job:
```
sudo swapoff -a
```
* Enable Kernel Modules and Change Settings in sysctl:
```
sudo modprobe overlay
sudo modprobe br_netfilter
```
* Change the sysctl settings by opening the necessary file with the command:
```
sudo nano /etc/sysctl.d/kubernetes.conf
```
* Look for the following lines and make sure they are set as you see below:
```
net.bridge.bridge-nf-call-ip6tables = 1
net.bridge.bridge-nf-call-iptables = 1
net.ipv4.ip_forward = 1
```
![image](https://user-images.githubusercontent.com/117667360/216338378-79ec0c19-b6fa-43bb-8f71-7025db157166.png)

Save and close the file. Reload sysctl with:

sudo sysctl --system

Install containerd

Install the necessary dependencies with:

sudo apt install curl gnupg2 software-properties-common apt-transport-https ca-certificates -y

Add the GPG key with:

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

Add the required repository with:

sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

Install containerd with the commands:

sudo apt update
sudo apt install containerd.io -y





#### To verify that the installation was successful, we run the command below. If all the pods are in RUNNING or COMPLETED mode then the deployment was successful:

<img width="1260" alt="Screenshot 2023-01-28 at 22 51 59" src="https://user-images.githubusercontent.com/117667360/215290620-6c4227df-dce1-4ba1-87ee-dfaf9a17a06e.png">

#### Get a list of all Nodes in Kubernetes:


<img width="1231" alt="Screenshot 2023-01-30 at 12 18 37" src="https://user-images.githubusercontent.com/117667360/215450162-c6621371-5f1b-4f7f-b8da-74cf5c43d0c1.png">

