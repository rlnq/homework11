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







#### To verify that the installation was successful, we run the command below. If all the pods are in RUNNING or COMPLETED mode then the deployment was successful:

<img width="1260" alt="Screenshot 2023-01-28 at 22 51 59" src="https://user-images.githubusercontent.com/117667360/215290620-6c4227df-dce1-4ba1-87ee-dfaf9a17a06e.png">

#### Get a list of all Nodes in Kubernetes:


<img width="1231" alt="Screenshot 2023-01-30 at 12 18 37" src="https://user-images.githubusercontent.com/117667360/215450162-c6621371-5f1b-4f7f-b8da-74cf5c43d0c1.png">

