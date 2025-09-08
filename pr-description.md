## 🚀 Update Helm Chart to v0.1.2

This PR automatically updates the Helm chart following a new release in the main application repository.

### 📦 Changes
- **Chart Version**: Updated to `0.1.2`
- **App Version**: Updated to `v0.1.2`
- **Docker Image**: Updated to `ghcr.io/faixbenj/webhook:v0.1.2`

### 🔗 Source
- **Repository**: faixbenj/webhook
- **Release**: https://github.com/faixbenj/webhook/releases/tag/v0.1.2

### ✅ Validation
- [x] Helm chart linting passed
- [x] Template rendering successful
- [x] Version numbers updated correctly

### 🎯 Next Steps
After merging this PR:
1. The chart will be packaged and published
2. GitHub Pages will be updated with the new chart version
3. Users can install with: `helm install webhook-monitor oci://ghcr.io/faixbenj/charts/webhook-monitor --version 0.1.2`

---
*This PR was automatically created by the CI/CD pipeline* 🤖
