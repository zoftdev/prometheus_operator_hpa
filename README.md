```bash
k apply -f kube-prometheus/manifests/
k apply -f servicemonitor-envoy.yaml 
k apply -f PrometheusRule-envoy-metrics.yml 
k apply -f clusterrole-prometheus-k8s.yaml 
sudo apt install make
make certs
k apply -f custom-metrics-api/
kubectl get --raw "/apis/custom.metrics.k8s.io/v1beta1/namespaces/aoc-dev/pods/*/http_requests" | jq .
k apply -f demo-dev-hpa-custom.yaml  -n aoc-dev
k -n aoc-dev get hpa

