# 💾 Helm Charts Repository

[![Static Badge](https://img.shields.io/badge/Helm-Chart-white?style=flat&logo=helm&logoColor=white&logoSize=auto&labelColor=black)](https://helm.sh/)
[![Static Badge](https://img.shields.io/badge/Kubernetes-Deployments-white?style=flat&logo=kubernetes&logoColor=white&logoSize=auto&labelColor=black)](https://kubernetes.io/)

A Helm chart repository for Kubernetes resources.

## 📦 Available Charts

| Chart | Description | Version |
|-------|-------------|---------|
| `gateway-api-crds` | Kubernetes Gateway API CRDs | `1.5.1` |
| `lan-orangutan` | LAN Orangutan network tool | `0.1.0` |

## 🚀 Quick Start

Add the Helm repository:

```bash
helm repo add peterweissdk https://peterweissdk.github.io/helm
helm repo update
```

Install a chart:

```bash
helm install <release-name> peterweissdk/<chart-name>
```

To customize the installation, create a `values.yaml` file and apply it:

```bash
helm install <release-name> peterweissdk/<chart-name> -f values.yaml
```

## 📝 Directory Structure

```
helm/
├── charts/
│   ├── gateway-api-crds/
│   │   ├── Chart.yaml
│   │   ├── templates/
│   │   │   └── crds.yaml
│   │   └── values.yaml
│   └── lan-orangutan/
│       ├── Chart.yaml
│       ├── templates/
│       │   ├── _helpers.tpl
│       │   ├── deployment.yaml
│       │   ├── pvc.yaml
│       │   └── service.yaml
│       └── values.yaml
├── docs/
│   ├── index.yaml
│   └── *.tgz
├── LICENSE
└── README.md
```

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## 🆘 Support

If you encounter any issues or need support, please file an issue on the GitHub repository.

## 📄 License

This project is licensed under the GNU GENERAL PUBLIC LICENSE v3.0 - see the [LICENSE](LICENSE) file for details.