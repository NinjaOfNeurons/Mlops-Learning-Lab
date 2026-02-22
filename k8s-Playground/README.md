# Kubernetes — Notes & Hands-On Learning ☸️

This repository contains **my personal notes, experiments, YAML files, and hands-on learnings** related to **Kubernetes**, starting from **absolute basics** and gradually moving towards **advanced concepts**.

The goal of this repo is simple:
👉 **Document everything I learn about Kubernetes in one place**, in a practical and revisable format.

---

## 📌 What is Kubernetes?

Kubernetes (K8s) is a container orchestration platform used to:

- Deploy containerized applications
- Scale applications automatically
- Manage application lifecycle
- Handle networking, storage, and self-healing

Instead of manually managing containers, Kubernetes lets you **declare the desired state**, and it continuously works to maintain it.

---

##  What This Repository Contains

This repo is structured as **learning notes + practice**, not polished tutorials.

You will find:
-  Concept notes (easy to revise)
-  YAML manifests (real examples)
-  Hands-on experiments
-  Mistakes, learnings, and fixes
-  Revisions and updates as my understanding improves

Everything here reflects **what I actually learned and practiced**, not copied docs.

---

## 🗿 Topics Covered (Growing Over Time)

### Core Concepts
- Containers & container orchestration
- Kubernetes architecture
- Control plane & worker nodes
- kubelet, kube-apiserver, etcd, scheduler

### Workloads
- Pods
- ReplicaSets
- Deployments
- Scaling & rolling updates
- Rollbacks

### Networking
- Services (ClusterIP, NodePort, LoadBalancer)
- Pod-to-Pod communication
- Service discovery

### Configuration & Storage
- ConfigMaps
- Secrets
- Volumes
- Persistent Volumes (PV)
- Persistent Volume Claims (PVC)

### Resource Management
- CPU & memory requests
- Limits
- QoS classes

### Advanced (WIP 🚧)
- Namespaces
- Health checks (liveness/readiness)
- Init containers
- Troubleshooting
- Basic security concepts

> This list will expand as I continue learning.

---

## How I Use This Repo

- Write notes after learning a concept
- Add YAML files after practicing locally
- Revise concepts by reading my own notes
- Track progress over time

This is **not a tutorial repo**, it’s a **learning journal**.

---

##  Tools Used

- `kubectl`
- Minikube / Kind / k3s (local clusters)
- Docker
- YAML

---

## Status

🚧 **Actively maintained**  
This repo will keep evolving as I go deeper into Kubernetes.

---

## Why This Repo Exists

- To solidify my understanding by writing
- To have a single revision source
- To track real progress, not just course completion
- To help others who learn the same way

---

## ⭐ Notes

- Content may change as my understanding improves
- Some explanations may be simplified intentionally
- Corrections and refactors are part of the learning process

---

**Learning in public. Breaking things. Fixing them. Repeating.** ☸️
