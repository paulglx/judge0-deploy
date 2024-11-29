# Judge0 deployment for Arbitre

## Install

```bash
kubectl create secret generic judge0-secrets \
  --from-literal=postgres-password=$(openssl rand -base64 32) \
  --from-literal=redis-password=$(openssl rand -base64 32)

kubectl apply -f configmap.yaml
kubectl apply -f judge0.yaml
```

## Develop

Useful : port forwarding

```bash
kubectl port-forward service/judge0 8080:80
```
