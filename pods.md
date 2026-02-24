# Kubernetes Pods – Inspection and Troubleshooting

This document covers practical workflows for inspecting, debugging, and managing pods based on my experience deploying 
containerized applications in Minikube.

---

## 1. Inspecting Pod Status

Pods are the first point of investigation when applications fail.

### List all pods

```bash
kubectl get pods
```

### Describe a pod

when a pod fails this command helps you give a detail inspection of the pod like image pull errors.

```bash
kubectl describe pods <pod-name>
```

### Viewing logs

Logs are used for diagnosing runtime errors. This helps you identify crashes, database connectivity issues or configuration issues.

```bash
kubectl logs <pod-name>
```
### Resource Usage and Performance

This helps monitor CPU and memory usage

```bash
kubectl top pods
```

## Self-Healing and Restart Behavior

The application I deployed using a Kubernetes Deployment ensures that failed containers are automatically restarted.
When the container exited with a non-zero status code, Kubernetes restarted the pod automatically, maintaining the desired state.
This behavior improves system reliability and reduces manual intervention.
