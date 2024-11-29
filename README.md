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

## Cgroup problem (unable to open rb sysfile ...)

1. Locate the settings.json file

The file is located at:
`~/Library/Group Containers/group.com.docker/settings.json`

2. Edit the settings.json file:

Open the settings.json file in a text editor. You may need to add or modify the following line to disable cgroup v2:

```json
{
    "deprecatedCgroupv1": true
}```

3. Restart Docker Desktop:

After saving your changes, restart Docker Desktop for the changes to take effect.
