# Raspberry Pi Kubernetes Cluster with Flux
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![FluxCD](https://img.shields.io/badge/GitOps-FluxCD-009688?logo=flux&logoColor=white)](https://fluxcd.io/)
[![MetalLB](https://img.shields.io/badge/Networking-MetalLB-1F97D4)](https://metallb.universe.tf/)
[![cert-manager](https://img.shields.io/badge/Certificates-cert--manager-3ECF8E)](https://cert-manager.io/)
[![Monitoring](https://img.shields.io/badge/Monitoring-kube--prometheus--stack-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![Karma](https://img.shields.io/badge/Alerts-Karma-6D5DF7)](https://github.com/prymitive/karma)
[![Postgres](https://img.shields.io/badge/Database-CloudNativePG-336791?logo=postgresql&logoColor=white)](https://cloudnative-pg.io/)
[![MariaDB](https://img.shields.io/badge/Database-MariaDB-1F5FA8?logo=mariadb&logoColor=white)](https://mariadb.org/)
[![NGINX](https://img.shields.io/badge/Ingress-NGINX-009639?logo=nginx&logoColor=white)](https://kubernetes.github.io/ingress-nginx/)
[![Loki](https://img.shields.io/badge/Logging-Loki-5A2D81?logo=grafana&logoColor=white)](https://grafana.com/oss/loki/)
[![MinIO](https://img.shields.io/badge/Storage-MinIO-9400d3?logo=minio&logoColor=white)](https://min.io/)

This repository contains the GitOps configuration for my personal Raspberry Pi Kubernetes cluster (k3s).
[Flux](https://fluxcd.io/) continuously reconciles the cluster state with the manifests stored here, ensuring a reproducible, self-healing setup.

The Cluster itself is provisioned by using [sfotiadis/ansible-rpi-cluster](https://github.com/sfotiadis/ansible-rpi-cluster), which installs k3s and [Cilium](https://cilium.io/).


## Repository Structure

```text
.
├── clusters
│   ├── rpi-cluster-dev               # Flux Kustomizations for Dev
│   └── rpi-cluster-prod              # Flux Kustomizations for Prod
├── docs                              # Additional docs (SOPS, networking, ...)
├── helm                              # Custom or adapted Helm charts tailored for this cluster
├── infrastructure
│   ├── configs                       # Cluster level config
│   ├── controllers                   # Operators & controllers
│   └── observability                 # Monitoring & logging
└── tenants                           # Application layer (base + dev/prod overlays; non-infrastructure workloads) 
```

### Environments
`clusters/rpi-cluster-dev` and `clusters/rpi-cluster-prod` reference different overlay paths under `infrastructure/*` and `tenants/*`. Patches adjust replica counts and storage classes (`local-path` vs `nfs-rwx`).

## Components (selected)

| Category        | Components |
|-----------------|------------|
| Networking      | MetalLB, Cilium |
| Ingress         | ingress-nginx |
| Certificates    | cert-manager |
| Database        | CloudNativePG, MariaDB Operator |
| Object Storage  | MinIO |
| Monitoring      | kube-prometheus-stack, Karma |
| Logging         | Loki Stack |
| GitOps          | Flux controller metrics + GitHub alerts |
| Secrets/Vault   | OpenBao (experimental), Kratos (WIP) |
| Storage         | NFS Subdir External Provisioner (prod), Local Path Provisioner (dev) |

## Secrets Management

Sensitive data (e.g. certificates, passwords) is stored in this repository in encrypted form using [SOPS](https://github.com/getsops/sops).
This allows secrets to be safely committed to Git while still enabling Flux to decrypt and apply them to the cluster.

## Disclaimer

This repository is a personal homelab project running on a Raspberry Pi cluster.
It is not intended for production use but serves as a playground for experimenting with GitOps and Kubernetes ecosystem tooling.
