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

## Testing High CPU usage alert
```
kubectl run  high-cpu --image=containerstack/cpustress -- --cpu 4 --timeout 30s --metrics-brief
```


kubectl run -it --rm --restart=Never -n databases busybox --image=gcr.io/google-containers/busybox sh