helm install (appName)

helm upgrade (appName)
- Figures out changes done to the Chart and redeploys the manifests to **Kubernetes**
helm rollback (appName)
- Helm also keeps version history so you can rollback to the last working configuration
helm package
- packages your chart and pushes it to a repo to make available to all developers of the hole company