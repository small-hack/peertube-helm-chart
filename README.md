# Peertube Helm Chart
<a href="https://github.com/small-hack/peertube-helm-chart/releases"><img src="https://img.shields.io/github/v/release/small-hack/peertube-helm-chart?style=plastic&labelColor=blue&color=green&logo=GitHub&logoColor=white"></a>

- [https://github.com/cloudymax/peertube-helm-chart](https://small-hack.github.io/peertube-helm-chart/)

This is a helm chart for Peertube for use with ArgoCD. It does not include Redis/Valkey, Postgres, or S3 subcharts. 
For an example of intended use please see https://github.com/small-hack/argocd-apps/tree/main/demo/peertube.

> This chart is a work-in-progress and is not suitable for general use at this time - see the open issues for further information.

Installation via helm:
```bash
helm repo add peertube https://cloudymax.github.io/peertube-helm-chart/
helm install peertube/peertube --generate-name
```


