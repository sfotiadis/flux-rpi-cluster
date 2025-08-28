# Raspberry Pi Kubernetes Cluster with Flux

[![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?logo=kubernetes&logoColor=white)](https://kubernetes.io/)
[![FluxCD](https://img.shields.io/badge/GitOps-FluxCD-009688?logo=flux&logoColor=white)](https://fluxcd.io/)
[![Prometheus](https://img.shields.io/badge/Monitoring-Prometheus-E6522C?logo=prometheus&logoColor=white)](https://prometheus.io/)
[![Grafana](https://img.shields.io/badge/Dashboard-Grafana-F46800?logo=grafana&logoColor=white)](https://grafana.com/)
[![RabbitMQ](https://img.shields.io/badge/Messaging-RabbitMQ-FF6600?logo=rabbitmq&logoColor=white)](https://www.rabbitmq.com/)
[![MetalLB](https://img.shields.io/badge/Networking-MetalLB-1F97D4)](https://metallb.universe.tf/)
[![cert-manager](https://img.shields.io/badge/Certificates-cert--manager-3ECF8E)](https://cert-manager.io/)
[![Karma](https://img.shields.io/badge/Alerts-Karma-6D5DF7)](https://github.com/prymitive/karma)

This repository contains the GitOps configuration setup for my personal Raspberry Pi Kubernetes cluster (k3s), managed fully declaratively with Flux.

## Overview

- **Cluster type:** [k3s](https://github.com/k3s-io/k3s) on 2 Raspberry Pi 5 devices
  - 1 Control Plane
  - 1 Worker Node
- **GitOps:** [Flux](https://fluxcd.io/)
- **Networking (CNI):** Cilium
- **Load Balancer:** MetalLB

## Goals

- Fully declarative cluster management
- Automatic synchronization via Flux
- Easy addition/removal of components
- Publicly readable configuration for learning
