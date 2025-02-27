
# Commands to install Docker in RHEL



## Install Yum-utils Package
```bash
yum install yum-utils -y
```
**Expected Output:** Installs the yum-utils package with all dependencies.

## Connect to Red Hat Subscription (if needed)
```bash
rhc connect --username yourusername --password yourpassword
```
**Expected Output:** Successfully connects your system to Red Hat subscription management.

## Set up Docker Repository
```bash
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```
**Expected Output:** Docker repository added successfully.

## Install Docker Engine
```bash
sudo yum install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
**Expected Output:** Installs Docker and related plugins.

## Start Docker Service
```bash
sudo systemctl start docker
```
**Expected Output:** Docker service started.

## Enable Docker Service
```bash
sudo systemctl enable docker
```
**Expected Output:** Docker service enabled at boot.

## Install Required Dependencies
```bash
sudo yum install -y curl conntrack
```
**Expected Output:** Installs curl and conntrack.

## Download and Install kubectl
```bash
curl -LO "https://dl.k8s.io/release/$(curl -sL https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
chmod +x kubectl
sudo mv kubectl /usr/local/bin/
```
**Expected Output:** kubectl downloaded, made executable, and moved to /usr/local/bin.

## Verify kubectl Installation
```bash
kubectl version --client
```
**Expected Output:** Displays the kubectl client version.

## Download and Install Minikube
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
chmod +x minikube-linux-amd64
sudo mv minikube-linux-amd64 /usr/local/bin/minikube
```
**Expected Output:** Minikube binary downloaded, made executable, and moved to /usr/local/bin.

## Update PATH (Optional, if needed)
```bash
echo 'export PATH=$PATH:/usr/local/bin' >> ~/.bashrc
source ~/.bashrc
```
**Expected Output:** PATH updated for current user.

## Start Minikube (As Root - Not Recommended)
```bash
sudo minikube start --driver=docker --force
```
**Expected Output:** Minikube cluster starts using Docker driver with root privileges (force flag required).

## Verify Minikube Status
```bash
minikube status
```
**Expected Output:** Shows the status of Minikube (Running / Stopped / etc.).

## Check Kubernetes Node Status
```bash
kubectl get nodes
```
**Expected Output:** Lists Minikube node, showing status as Ready if everything is set up correctly.

## (Optional) Use None Driver for Root (Recommended for Root Users)
```bash
sudo minikube start --driver=none
```
**Expected Output:** Minikube starts using the "none" driver, running Kubernetes components as system services.

## Verify Cluster Info (Optional Check)
```bash
kubectl cluster-info
```
**Expected Output:** Displays cluster control plane URL and services.

## Apply Sample YAML (When Cluster is Ready)
```bash
kubectl apply -f your-file.yaml
```
**Expected Output:** Resources from the YAML file are created.

## Check All Running Pods
```bash
kubectl get pods -A
```
**Expected Output:** Lists all pods in all namespaces, including system pods.
