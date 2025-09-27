# Raspberry Pi Kubernetes Cluster with Flux
[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![FluxCD](https://img.shields.io/badge/GitOps-FluxCD-009688?logo=flux&logoColor=white)](https://fluxcd.io/)
[![MetalLB](https://img.shields.io/badge/Networking-MetalLB-1F97D4)](https://metallb.universe.tf/)
[![cert-manager](https://img.shields.io/badge/Certificates-cert--manager-3ECF8E)](https://cert-manager.io/)
[![Monitoring](https://img.shields.io/badge/Monitoring-kube--prometheus--stack-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![Karma](https://img.shields.io/badge/Alerts-Karma-6D5DF7)](https://github.com/prymitive/karma)
[![Postgres](https://img.shields.io/badge/Database-CloudNativePG-336791?logo=postgresql&logoColor=white)](https://cloudnative-pg.io/)
[![NGINX](https://img.shields.io/badge/Ingress-NGINX-009639?logo=nginx&logoColor=white)](https://kubernetes.github.io/ingress-nginx/)
[![Loki](https://img.shields.io/badge/Logging-Loki-5A2D81?logo=grafana&logoColor=white)](https://grafana.com/oss/loki/)

This repository contains the GitOps configuration for my personal Raspberry Pi Kubernetes cluster (k3s).  
[Flux](https://fluxcd.io/) continuously reconciles the cluster state with the manifests stored here, ensuring a reproducible, self-healing setup.

The Cluster is provisioned by using [sfotiadis/ansible-rpi-cluster](https://github.com/sfotiadis/ansible-rpi-cluster) to install k3s and Cilium.
