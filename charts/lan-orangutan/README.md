# lan-orangutan

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 3.3.8](https://img.shields.io/badge/AppVersion-3.3.8-informational?style=flat-square)

A Helm chart for deploying LAN Orangutan - a network monitoring and management tool for local networks

**Homepage:** <https://github.com/291-group/lan-orangutan>

## Source Code

* <https://github.com/291-group/lan-orangutan>
* <https://github.com/peterweissdk/helm>

## 🚀 Quick Start

```bash
helm repo add peterweissdk https://peterweissdk.github.io/helm
helm repo update
helm install lan-orangutan peterweissdk/lan-orangutan
```

## ✨ Features

- **Host Network Support** - Run with host network for direct LAN access
- **Flexible Persistence** - Choose between PVC, hostPath, or emptyDir storage
- **Security Capabilities** - Pre-configured with NET_RAW, NET_ADMIN, and NET_BIND_SERVICE
- **Pod Anti-Affinity** - Optional scheduling rules to spread pods across nodes
- **Health Probes** - Configurable liveness and readiness probes

## 📦 Installing the Chart

To install the chart with the release name `lan-orangutan`:

```bash
helm install lan-orangutan peterweissdk/lan-orangutan
```

To install with custom values:

```bash
helm install lan-orangutan peterweissdk/lan-orangutan -f values.yaml
```

## 🗑️ Uninstalling the Chart

```bash
helm uninstall lan-orangutan
```

## ⚙️ Configuration

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | See values.yaml | Affinity rules for pod scheduling |
| affinity.podAntiAffinity | object | `{"enabled":false,"preferredDuringSchedulingIgnoredDuringExecution":[{"podAffinityTerm":{"labelSelector":{"matchLabels":{"app.kubernetes.io/name":"lan-orangutan"}},"topologyKey":"kubernetes.io/hostname"},"weight":100}]}` | Pod anti-affinity configuration (prefers scheduling pods on different nodes) |
| affinity.podAntiAffinity.enabled | bool | `false` | Enable pod anti-affinity |
| env | object | `{"ORANGUTAN_PORT":"291","TZ":"UTC"}` | Environment variables passed to the container |
| env.ORANGUTAN_PORT | string | `"291"` | Port for the Orangutan service |
| env.TZ | string | `"UTC"` | Timezone |
| fullnameOverride | string | `""` | Override the full resource name (ignores release name) |
| hostNetwork | bool | `true` | Use the host's network namespace |
| image | object | `{"pullPolicy":"IfNotPresent","repository":"ghcr.io/291-group/lan-orangutan","tag":""}` | Container image configuration |
| image.pullPolicy | string | `"IfNotPresent"` | Image pull policy |
| image.repository | string | `"ghcr.io/291-group/lan-orangutan"` | Image repository |
| image.tag | string | `""` | Image tag (defaults to appVersion) |
| imagePullSecrets | list | `[]` | Secrets for pulling images from private registries |
| livenessProbe | object | See values.yaml | Liveness probe configuration (restarts container if it fails) |
| livenessProbe.enabled | bool | `true` | Enable liveness probe |
| livenessProbe.failureThreshold | int | `3` | Number of failures before restart |
| livenessProbe.httpGet.path | string | `"/static/orangutan.svg"` | Path for HTTP probe |
| livenessProbe.httpGet.port | int | `291` | Port for HTTP probe |
| livenessProbe.initialDelaySeconds | int | `5` | Initial delay before probe starts |
| livenessProbe.periodSeconds | int | `30` | How often to perform the probe |
| livenessProbe.timeoutSeconds | int | `3` | Probe timeout |
| nameOverride | string | `""` | Override the chart name |
| nodeSelector | object | `{}` | Node labels for pod assignment |
| persistence | object | See values.yaml | Persistence configuration |
| persistence.accessMode | string | `"ReadWriteOnce"` | Access mode for PVC |
| persistence.enabled | bool | `true` | Enable persistence (uses PVC when hostPath.enabled=false) |
| persistence.existingClaim | string | `""` | Use existing PVC instead of creating one |
| persistence.hostPath | object | `{"enabled":false,"path":"/var/lib/lan-orangutan","type":"DirectoryOrCreate"}` | hostPath volume configuration |
| persistence.hostPath.enabled | bool | `false` | Use hostPath instead of PVC |
| persistence.hostPath.path | string | `"/var/lib/lan-orangutan"` | Path on the host |
| persistence.hostPath.type | string | `"DirectoryOrCreate"` | hostPath type |
| persistence.name | string | `""` | Custom PVC name (defaults to fullname) |
| persistence.size | string | `"1Gi"` | Size of PVC |
| persistence.storageClass | string | `""` | Storage class for PVC |
| readinessProbe | object | See values.yaml | Readiness probe configuration (removes pod from service if it fails) |
| readinessProbe.enabled | bool | `false` | Enable readiness probe |
| readinessProbe.failureThreshold | int | `3` | Number of failures before marking unready |
| readinessProbe.httpGet.path | string | `"/static/orangutan.svg"` | Path for HTTP probe |
| readinessProbe.httpGet.port | int | `291` | Port for HTTP probe |
| readinessProbe.initialDelaySeconds | int | `5` | Initial delay before probe starts |
| readinessProbe.periodSeconds | int | `10` | How often to perform the probe |
| readinessProbe.timeoutSeconds | int | `3` | Probe timeout |
| replicaCount | int | `1` | Number of pod replicas |
| resources | object | See values.yaml | Container resource requests and limits |
| resources.limits.cpu | string | `"100m"` | CPU limit |
| resources.limits.memory | string | `"64Mi"` | Memory limit |
| resources.requests.cpu | string | `"10m"` | CPU request |
| resources.requests.memory | string | `"32Mi"` | Memory request |
| securityContext | object | `{"capabilities":{"add":["NET_RAW","NET_ADMIN","NET_BIND_SERVICE"]}}` | Container security context with network capabilities |
| service | object | `{"enabled":true,"port":291,"targetPort":291,"type":"ClusterIP"}` | Service configuration |
| service.enabled | bool | `true` | Enable service creation |
| service.port | int | `291` | Service port |
| service.targetPort | int | `291` | Container target port |
| service.type | string | `"ClusterIP"` | Service type |
| tolerations | list | `[]` | Tolerations for pod scheduling |

### Persistence Options

| Configuration | Description |
|---------------|-------------|
| `persistence.enabled=true` + `persistence.hostPath.enabled=false` | Use PVC with optional storageClass |
| `persistence.hostPath.enabled=true` | Use hostPath volume |
| Both disabled | Use emptyDir (data lost on pod restart) |

### Example: Using PVC with StorageClass

```yaml
persistence:
  enabled: true
  name: "lan-orangutan-data"
  storageClass: "local-path"
  size: 5Gi
  hostPath:
    enabled: false
```

### Example: Using Existing PVC

```yaml
persistence:
  enabled: true
  existingClaim: "my-existing-pvc"
  hostPath:
    enabled: false
```

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| peterweissdk | <peterweissdk@gmail.com> |  |
