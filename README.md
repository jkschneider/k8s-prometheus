# Prometheus on K8S

Modified from [this](https://medium.com/devopslinks/production-grade-kubernetes-monitoring-using-prometheus-78144b835b60) Medium post

## Steps to install

1. `gcloud compute disks create prometheus-volume --size=250GB --type=pd-ssd`, enter `list` and then the correct zone number.
2. `kubectl apply -f monitoring/prometheus/` (`kubectl get svc -n monitoring` to see external IP).
3. `kubectl apply -f monitoring/proxy/`
4. `kubectl create deployment grafana --image=docker.io/grafana/grafana:6.1.6 -n monitoring`
5. `kubectl expose deploy grafana --type=LoadBalancer --name=grafana --port=3000 -n monitoring`
