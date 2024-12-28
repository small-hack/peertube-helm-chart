# Peertube Helm Chart
<a href="https://github.com/cloudymax/peertube-helm-chart/releases"><img src="https://img.shields.io/github/v/release/cloudymax/peertube-helm-chart?style=plastic&labelColor=blue&color=green&logo=GitHub&logoColor=white"></a>

This is a helm chart for Peertube for use with ArgoCD. It does not include Redis/Valkey, Postgres, or S3 subcharts. 
For an example of intended use please see https://github.com/small-hack/argocd-apps/tree/main/demo/peertube.

Installation via helm:
```bash
helm repo add peertube https://cloudymax.github.io/peertube-helm-chart/
helm install peertube/peertueb --generate-name
```


