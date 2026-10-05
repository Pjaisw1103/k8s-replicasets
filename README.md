# 🔄 Kubernetes ReplicaSet Controller

[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)](#)

Declarative Kubernetes **ReplicaSet** configuration for maintaining a guaranteed pool of high-availability, identical Pod replicas (`Nginx 1.29`).

---

## 📌 Resource Specs

- **Replica Count**: `3` active Pod instances
- **Label Selector**: `app: nginx`
- **Image**: `nginx:1.29`
- **Container Port**: `80`

---

## 📂 Repository Structure

```text
k8s-replicasets/
├── replicaset.yaml     # ReplicaSet object specification
└── README.md           # Repository Documentation
```

---

## 🚀 Usage Guide

### Prerequisites
- Active Kubernetes cluster and configured `kubectl` CLI tool.

### Apply Manifest

```bash
# Create ReplicaSet
kubectl apply -f replicaset.yaml

# Verify ReplicaSet status
kubectl get rs

# List managed pods
kubectl get pods -l app=nginx
```

### Self-Healing Test & Scaling

```bash
# Test self-healing (delete one pod; ReplicaSet immediately resurrects it)
kubectl delete pod -l app=nginx --field-selector=status.phase=Running --limit=1

# Scale replicas dynamically
kubectl scale rs nginx-rs --replicas=5
```

### Cleanup

```bash
kubectl delete -f replicaset.yaml
```

---

## 👩‍💻 Author

**Priya Jaiswal**  
[GitHub Profile](https://github.com/Pjaisw1103)
