# gateway-api-crds

![Version: 1.5.1](https://img.shields.io/badge/Version-1.5.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 1.5.1](https://img.shields.io/badge/AppVersion-1.5.1-informational?style=flat-square)

A Helm chart to install and manage Kubernetes Gateway API Custom Resource Definitions (CRDs)

**Homepage:** <https://gateway-api.sigs.k8s.io/>

## Source Code

* <https://github.com/kubernetes-sigs/gateway-api>
* <https://github.com/peterweissdk/helm>

## 🚀 Quick Start

```bash
helm repo add peterweissdk https://peterweissdk.github.io/helm
helm repo update
helm install gateway-api-crds peterweissdk/gateway-api-crds
```

## ✨ Features

- **Gateway API CRDs** - Installs all Gateway API Custom Resource Definitions
- **Easy Updates** - Simple Helm upgrade to update CRDs to new versions
- **No Configuration Required** - Works out of the box with sensible defaults

## 📦 Installing the Chart

To install the chart with the release name `gateway-api-crds`:

```bash
helm install gateway-api-crds peterweissdk/gateway-api-crds
```

## 🗑️ Uninstalling the Chart

```bash
helm uninstall gateway-api-crds
```

> **Note:** Uninstalling the chart will remove the CRDs. Any Gateway API resources (Gateway, HTTPRoute, etc.) will also be deleted.

## ⚙️ Configuration

This chart has no configurable values. It installs the Gateway API CRDs as-is from the upstream project.

## 📚 Gateway API Resources

After installation, the following CRDs will be available:

| CRD | Description |
|-----|-------------|
| `GatewayClass` | Defines a class of Gateways with common configuration |
| `Gateway` | Defines a load balancer or proxy |
| `HTTPRoute` | HTTP routing rules |
| `GRPCRoute` | gRPC routing rules |
| `TCPRoute` | TCP routing rules |
| `UDPRoute` | UDP routing rules |
| `TLSRoute` | TLS routing rules |
| `ReferenceGrant` | Cross-namespace reference permissions |

For more information, see the [Gateway API documentation](https://gateway-api.sigs.k8s.io/).

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| peterweissdk | <peterweissdk@gmail.com> |  |
