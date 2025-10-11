# Networking Overview

## Overview

This document describes the IP address allocation strategy for the **production** and **development** Kubernetes clusters.
Each cluster uses **MetalLB** for LoadBalancer service IP management.
Static IPs are assigned to cluster nodes, while a defined IP range (pool) is reserved for MetalLB to dynamically allocate service addresses.

## Production Environment

**Cluster Nodes**

| Role | IP Address  | Description |
|------|--------------|-------------|
| Node 1 | x.x.x.100 | control plane |
| Node 2 | x.x.x.101 | worker node |
| Node 3 | x.x.x.102 | worker node |

**MetalLB Address Pool**

| Range | Purpose | Notes |
|--------|----------|-------|
| `x.x.x.113 - x.x.x.129` | MetalLB LoadBalancer IP pool | Only unused IPs are included to avoid conflicts. |


## Development Environment

**Cluster Nodes**

| Role | IP Address  | Description |
|------|--------------|-------------|
| Node 1 | x.x.x.130 | control plane |
| Node 2 | x.x.x.131 | worker node |
| Node 3 | x.x.x.132 | worker node |

**MetalLB Address Pool**

| Range | Purpose | Notes |
|--------|----------|-------|
| `x.x.x.133 - x.x.x.149` | MetalLB LoadBalancer IP pool | Only unused IPs are included to avoid conflicts. |

