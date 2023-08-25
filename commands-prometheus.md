# Prometheus

```
kubectl create ns monitoring
kubectl config set-context kind-kind  --namespace=monitoring
```

## Installing Prometheus Stack
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update
```

```
helm install prometheus prometheus-community/kube-prometheus-stack -n monitoring
```

