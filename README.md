# 💾 Helm Charts Repository

[![Static Badge](https://img.shields.io/badge/Helm-Chart-white?style=flat&logo=helm&logoColor=white&logoSize=auto&labelColor=black)](https://helm.sh/)
[![Static Badge](https://img.shields.io/badge/Kubernetes-Deployments-white?style=flat&logo=kubernetes&logoColor=white&logoSize=auto&labelColor=black)](https://kubernetes.io/)

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
│   └── gateway-api-crds/
│       ├── Chart.yaml
│       ├── templates/
│       │   └── crds.yaml
│       └── values.yaml
├── docs/
│   ├── index.yaml
│   └── *.tgz
├── LISENCE
└── README.md
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🆘 Support

If you encounter any issues or need support, please file an issue on the GitHub repository.

## 📄 License

This project is licensed under the GNU GENERAL PUBLIC LICENSE v3.0 - see the [LICENSE](LICENSE) file for details.