
# Kubernetes Security Practices

This document summarizes practical Kubernetes security concepts based on my experience deploying secure applications in Minikube. The focus is on protecting secrets, securing communication, and reducing data theft

---

## 1. Secret Management

Sensitive data such as database credentials, TLS certificates, and API keys should never be stored in plain text inside application images or configuration files.

### Create a secret directly

```bash
kubectl create secret generic <filename> --from-literal=password=my-password
```

### Create a secret from yaml file

```bash
kubectl apply -f <filename>.yaml
```
### TLS and Secure Communication

Configur HTTPS communication between services using TLS certificates.

'''bash

kubectl create secret tls tls-secret \
  --cert=cert.pem \
  --key=key.pem
'''
TLS can be used in deployments to ensure encrypted communication and secure service exposure.


### Resource Limits and Stability

Resource constraints also improve security by preventing denial of service attacks, resource exhaustion and unstable workloads

'''yaml
resources:
  limits:
    memory: "256Mi"
    cpu: "500m"
'''
