# 💾 Helm Charts Repository

A Helm chart repository for Kubernetes resources, currently hosting the Gateway API CRDs chart.

## 🚀 Quick Start

Add the Helm repository:

```bash
helm repo add peterweissdk https://peterweissdk.github.io/helm
helm repo update
```

Install the Gateway API CRDs:

```bash
helm install gateway-api-crds peterweissdk/gateway-api-crds
```

## 🔧 Configuration

### Gateway API CRDs

| Parameter | Description | Default |
|-----------|-------------|---------|
| `appVersion` | Gateway API version | `1.5.1` |

To customize the installation:

```bash
helm install gateway-api-crds peterweissdk/gateway-api-crds -f values.yaml
```

## 📝 Directory Structure

```
helm/
├── charts/
│   └── gateway-api-crds/      # Gateway API CRDs Helm chart
│       ├── Chart.yaml         # Chart metadata
│       ├── templates/         # Kubernetes manifests
│       │   └── crds.yaml      # Gateway API CRD definitions
│       └── values.yaml        # Default configuration values
├── docs/                      # Helm repository index and packages
│   ├── index.yaml             # Repository index
│   └── *.tgz                  # Packaged charts
└── LICENSE                    # GPL-3.0 License
```
