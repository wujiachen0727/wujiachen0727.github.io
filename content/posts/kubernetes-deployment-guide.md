---
title: "Kubernetes部署实战指南"
date: 2025-09-01T14:30:00+08:00
draft: false
tags: ["Kubernetes", "云原生", "容器化", "DevOps"]
categories: ["云原生技术系列"]
description: "从零开始学习Kubernetes部署，包括集群搭建、应用部署和服务管理"
---

## 概述

Kubernetes作为容器编排的事实标准，已经成为现代云原生应用部署的核心技术。本文将从实战角度介绍如何在生产环境中部署和管理Kubernetes集群。

## 环境准备

### 硬件要求

- **Master节点**：至少2核CPU，4GB内存
- **Worker节点**：至少1核CPU，2GB内存
- **网络**：节点间网络互通，支持容器网络插件

### 软件依赖

```bash
# 安装Docker
curl -fsSL https://get.docker.com | bash

# 安装kubeadm、kubelet、kubectl
apt-get update && apt-get install -y apt-transport-https curl
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
```

## 集群初始化

### Master节点配置

使用kubeadm初始化集群：

```bash
kubeadm init --pod-network-cidr=10.244.0.0/16
```

### 网络插件安装

```bash
kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml
```

## 应用部署

### 创建Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.20
        ports:
        - containerPort: 80
```

### 服务暴露

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
  - port: 80
    targetPort: 80
  type: LoadBalancer
```

## 监控与维护

### 集群状态检查

```bash
# 检查节点状态
kubectl get nodes

# 检查Pod状态
kubectl get pods --all-namespaces

# 查看集群信息
kubectl cluster-info
```

### 日志管理

```bash
# 查看Pod日志
kubectl logs <pod-name>

# 实时查看日志
kubectl logs -f <pod-name>
```

## 最佳实践

1. **资源限制**：为所有容器设置资源请求和限制
2. **健康检查**：配置liveness和readiness探针
3. **安全策略**：使用RBAC控制访问权限
4. **备份策略**：定期备份etcd数据

## 总结

Kubernetes部署虽然复杂，但通过系统的学习和实践，可以掌握其核心概念和操作方法。建议在测试环境中充分验证后再部署到生产环境。

下一篇文章将介绍Kubernetes的高级特性和优化技巧。