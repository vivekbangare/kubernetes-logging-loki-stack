# Kubernetes logging with Loki and Grafana

- Grafana loki is a log aggregation tool that used to store and query logs.
- Designed to be cost effective and easy to operate
- Loki does not index full text from logs(like elasticsearch)
- Loki only indexes labels(metadata) from logs.
- Make it more cost effective and performant.
- Configuration and query language similar to prometheus.


```
helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm search repo loki
helm show values grafana/loki-stack > values.yaml
helm install --values values.yaml loki grafana/loki-stack
```

```
kubectl get secrets
kubectl describe secrets loki-grafana
kubectl get secrets loki-grafana -o jsonpath="{.data.admin-pasword}" | base64 --decode
```

### Viewing kubernetes logs

- Login to grafana dashboards
- add datasource as Loki
- expore 
- label_filter
for example: pod=etcd-minikube

### To view config for promtail

kubectl get secret loki-prometheus -o jsonpath="{.data.promtail\.yaml}" | base64 --decode
