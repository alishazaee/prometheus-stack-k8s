# Prometheus Stack

This repository provides instructions on how to install the Prometheus monitoring stack and test high CPU usage alerts. 

## Table of Contents
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Testing High CPU Usage Alert](#testing-high-cpu-usage-alert)
- [Additional Resources](#additional-resources)

## Prerequisites
Before proceeding, ensure that you have the following prerequisites set up:
- Kubernetes cluster is running and `kubectl` is properly configured.
- Helm is installed and configured on your local machine.
- You have the necessary permissions to create namespaces, install Helm charts, and create and manage resources in Kubernetes.

## Installation
To set up the Prometheus monitoring stack, follow these steps:

### 1. Create the Monitoring Namespace
```bash
kubectl create ns monitoring
kubectl config set-context kind-kind --namespace=monitoring
```
This will create a new Kubernetes namespace called `monitoring` and set it as the active namespace for further commands.

### 2. Add Prometheus Helm Repository and Update
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```
This adds the Prometheus Helm repository and updates your local repository cache with the latest charts.

### 3. Install Prometheus Stack
```bash
helm install prometheus prometheus-community/kube-prometheus-stack -n monitoring
```
This installs the Prometheus stack using the `kube-prometheus-stack` Helm chart from the Prometheus Community repository into the `monitoring` namespace.

## Testing 
To test high CPU usage alerting, follow these steps:

### 1. Launch a High CPU Usage Container
```bash
kubectl run high-cpu --image=containerstack/cpustress -- --cpu 4 --timeout 30s --metrics-brief
```
This command deploys a container with high CPU usage using the `containerstack/cpustress` image, stressing the CPU for 4 seconds and a timeout of 30 seconds.

### 2. Spawn a Busybox Pod
you can check the network connectivity by the following command
```bash
kubectl run -it --rm --restart=Never -n databases busybox --image=gcr.io/google-containers/busybox sh
```
This opens an interactive shell within a Busybox pod in the `databases` namespace, allowing you to interact with the Kubernetes cluster.

## Additional Resources
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Prometheus Community Helm Charts](https://prometheus-community.github.io/helm-charts/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Helm Documentation](https://helm.sh/docs/)
