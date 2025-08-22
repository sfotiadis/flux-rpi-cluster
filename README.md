# Raspberry Pi Kubernetes Cluster with Flux

This repository contains the GitOps configuration for my personal Raspberry Pi Kubernetes cluster (k3s) managed with Flux.

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
