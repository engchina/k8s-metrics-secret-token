# k8s-metrics-secret-token
```
kubectl apply -f monitoring-secret-token.yaml
TOKEN=$(kubectl -n kube-system get secrets monitoring-secret-token -ojsonpath='{.data.token}' | base64 -d)
curl -k --header "Authorization: Bearer $TOKEN"  https://[k8s_ip]:10250/metrics/cadvisor
```

or

```
curl -s --cert /etc/kubernetes/pki/apiserver-kubelet-client.crt --key /etc/kubernetes/pki/apiserver-kubelet-client.key https://[k8s_ip]:10250/metrics -k
```
