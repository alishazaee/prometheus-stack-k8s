# Redis and Redis Exporter Setup

This repository provides instructions on how to set up Redis and the Redis Exporter for monitoring using Prometheus.

## Table of Contents
- [Prerequisites](#prerequisites)
- [Redis Installation](#redis-installation)
- [Redis Exporter Installation](#redis-exporter-installation)
- [Accessing Prometheus and Grafana](#accessing-prometheus-and-grafana)
- [Additional Resources](#additional-resources)

## Prerequisites
Before starting, ensure that you have the following prerequisites in place:
- A running Kubernetes cluster.
- `kubectl` configured to interact with the cluster.
- Helm installed and configured locally.
- Proper permissions to create namespaces, install Helm charts, and manage resources in Kubernetes.

## Redis Installation
To install Redis, follow these steps:

### 1. Create the Databases Namespace
```bash
kubectl create ns databases
```
This command creates a new Kubernetes namespace named `databases`.

### 2. Install Redis
```bash
helm install redis oci://registry-1.docker.io/bitnamicharts/redis -f values-redis.yaml -n databases
```
This command installs Redis using the provided Helm chart and custom values file (`values-redis.yaml`). The Redis deployment will be set up in the `databases` namespace.

## Redis Exporter Installation
To install the Redis Exporter for monitoring Redis metrics with Prometheus, follow these steps:

### 1. Add the Prometheus Helm Repository and Update
```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```
These commands add the Prometheus Helm repository and update your local repository cache.

### 2. Install the Redis Exporter
```bash
helm install redis-exporter prometheus-community/prometheus-redis-exporter -f values-redis-exporter.yaml -n databases
```
This command installs the Redis Exporter using the provided Helm chart and custom values file (`values-redis-exporter.yaml`). The exporter will be deployed in the `databases` namespace.

## Accessing Prometheus and Grafana
To access Prometheus and Grafana to view the collected metrics, follow these steps:

### 1. Port Forward Prometheus-Grafana Service
```bash
kubectl port-forward service/prometheus-grafana -n monitoring 8080:80 &
```
This command sets up port forwarding to access the Grafana dashboard on `http://localhost:8080`.

### 2. Port Forward Prometheus-Kube-Prometheus-Prometheus Service
```bash
kubectl port-forward service/prometheus-kube-prometheus-prometheus -n monitoring 9090:9090 &
```
This command sets up port forwarding to access the Prometheus web UI on `http://localhost:9090`.

Now you can access Grafana and Prometheus locally using the provided ports.

## Additional Resources
- [Redis Documentation](https://redis.io/documentation)
- [Redis Exporter GitHub Repository](https://github.com/oliver006/redis_exporter)
- [Prometheus Documentation](https://prometheus.io/docs/)
- [Grafana Documentation](https://grafana.com/docs/)
- [Helm Documentation](https://helm.sh/docs/)
