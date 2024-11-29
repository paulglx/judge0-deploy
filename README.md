# Judge0 deployment for Arbitre

## Deploy

```bash
kubectl create secret generic judge0-secrets \
  --from-literal=postgres-password=$(openssl rand -base64 32) \
  --from-literal=redis-password=$(openssl rand -base64 32)

kubectl apply -f judge0.yaml
```

Judge0 config : [Judge0 documentation](https://github.com/judge0/judge0/blob/master/judge0.conf)

Useful : port forwarding

```bash
kubectl port-forward service/judge0 8080:80
```
