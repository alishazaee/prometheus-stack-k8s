# Redis

kubectl create ns databases
helm install redis oci://registry-1.docker.io/bitnamicharts/redis -f values-redis.yaml -n databases



## Redis Exporter
```
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

helm install redis-exporter prometheus-community/prometheus-redis-exporter -f values-redis-exporter.yaml -n databases

kubectl port-forward service/prometheus-grafana -n monitoring 8080:80 &
kubectl port-forward service/prometheus-kube-prometheus-prometheus -n monitoring 9090:9090 & 
```


result : 
```
ali@ali-shazaei ~/prometheus $ kubectl get servicemonitor -n databases 
NAME                                       AGE
redis-exporter-prometheus-redis-exporter   32h
```