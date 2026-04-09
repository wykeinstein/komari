# komari-server Helm Chart

该 Helm Chart 用于在 Kubernetes 中部署 Komari Server，工作负载类型为 **StatefulSet**（非 Deployment）。

## 安装

```bash
helm install komari ./charts/komari-server
```

## 常用自定义

```bash
helm upgrade --install komari ./charts/komari-server \
  --set service.type=LoadBalancer \
  --set env.ADMIN_USERNAME=admin \
  --set env.ADMIN_PASSWORD='<your-password>'
```

## 持久化存储

默认启用 `volumeClaimTemplates`，每个 Pod 自动创建 PVC。

如果你已有 PVC，可以：

```bash
helm upgrade --install komari ./charts/komari-server \
  --set persistentVolume.existingClaim=komari-data
```

## 卸载

```bash
helm uninstall komari
```
