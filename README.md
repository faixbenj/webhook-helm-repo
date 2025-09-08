# ⎈ Webhook Monitor Helm Charts

Official Helm charts for the [Webhook Monitor](https://github.com/faixbenj/webhook-monitor) appli- 🏠 [Main Application](https://github.com/faixbenj/webhook-monitor)
- 📜 [Chart Documentation](./charts/webhook-monitor/README.md)
- 🌐 [Helm Repository](https://faixbenj.github.io/webhook-helm-repo/)
- 🐳 [Container Images](https://github.com/faixbenj/webhook-monitor/pkgs/container/webhook-monitor)on.

## 🚀 Quick Start

### Add the Helm Repository

```bash
helm repo add webhook-monitor https://faixbenj.github.io/webhook-helm-repo/
helm repo update
```

### Install the Chart

```bash
# Install with default values
helm install my-webhook-monitor webhook-monitor/webhook-monitor

# Install with custom values
helm install my-webhook-monitor webhook-monitor/webhook-monitor \
  --set image.tag=v1.0.0 \
  --set ingress.hosts[0].host=webhooks.example.com
```

### Install from OCI Registry

```bash
# Install directly from GitHub Container Registry
helm install my-webhook-monitor oci://ghcr.io/faixbenj/charts/webhook-monitor --version 1.0.0
```

## 📋 Available Charts

| Chart | Description | App Version | Chart Version |
|-------|-------------|-------------|---------------|
| [webhook-monitor](./charts/webhook-monitor/) | Real-time webhook monitoring with Vue.js frontend | Latest | Latest |

## ⚙️ Configuration

### Common Configuration Options

| Parameter | Description | Default |
|-----------|-------------|---------|
| `image.repository` | Container image repository | `ghcr.io/faixbenj/webhook-monitor` |
| `image.tag` | Container image tag | `latest` |
| `service.type` | Kubernetes service type | `ClusterIP` |
| `service.port` | Service port | `80` |
| `ingress.enabled` | Enable ingress | `true` |
| `ingress.hosts[0].host` | Hostname for ingress | `webhook-monitor.local` |
| `resources.limits.cpu` | CPU limit | `500m` |
| `resources.limits.memory` | Memory limit | `512Mi` |

### Example values.yaml

```yaml
# Custom configuration example
image:
  repository: ghcr.io/faixbenj/webhook-monitor
  tag: "v1.0.0"

ingress:
  enabled: true
  hosts:
    - host: webhooks.example.com
      paths:
        - path: /
          pathType: Prefix

resources:
  limits:
    cpu: 1000m
    memory: 1Gi
  requests:
    cpu: 500m
    memory: 512Mi

autoscaling:
  enabled: true
  minReplicas: 2
  maxReplicas: 10
  targetCPUUtilizationPercentage: 70
```

## 🔧 Development

### Prerequisites

- [Helm 3.8+](https://helm.sh/docs/intro/install/)
- [Kubernetes 1.20+](https://kubernetes.io/)

### Local Development

```bash
# Clone the repository
git clone https://github.com/faixbenj/webhook-helm-repo.git
cd webhook-helm-repo

# Validate the chart
helm lint charts/webhook-monitor/

# Template the chart (dry-run)
helm template test-release charts/webhook-monitor/

# Install locally
helm install test-release charts/webhook-monitor/ --namespace webhook-monitor --create-namespace
```

### Testing

```bash
# Run chart tests
helm test test-release --namespace webhook-monitor

# Verify deployment
kubectl get all -n webhook-monitor
```

## 🤖 Automated Updates

This repository is automatically updated when new versions are released in the main [webhook-monitor](https://github.com/faixbenj/webhook-monitor) repository:

1. **New Release**: When a new version is tagged in the main repo (e.g., `v1.2.3`)
2. **Automatic PR**: A Pull Request is created here updating the chart version and image tag
3. **Review & Merge**: Review and merge the PR
4. **Automatic Publishing**: Chart is automatically packaged and published to:
   - GitHub Releases
   - GitHub Pages (Helm repository)
   - GitHub Container Registry (OCI)

## 📚 Documentation

- 🏠 [Main Application](https://github.com/faixbenj/webhook-monitor)
- 📖 [Chart Documentation](./charts/webhook-monitor/README.md)
- 🌐 [Helm Repository](https://faixbenj.github.io/webhook-monitor-helm/)
- 🐳 [Container Images](https://github.com/faixbenj/webhook-monitor/pkgs/container/webhook-monitor)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Test with `helm lint` and `helm template`
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- 🐛 [Report Issues](https://github.com/faixbenj/webhook-monitor/issues)
- 💬 [Discussions](https://github.com/faixbenj/webhook-monitor/discussions)
- 📧 [Contact](https://github.com/faixbenj)

---

**Made with ❤️ by [faixbenj](https://github.com/faixbenj)**