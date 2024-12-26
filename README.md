# Peertube Helm Chart
<a href="https://github.com/small-hack/generic-app-helm/releases"><img src="https://img.shields.io/github/v/release/small-hack/generic-app-helm?style=plastic&labelColor=blue&color=green&logo=GitHub&logoColor=white"></a>

This is a helm chart for a generic Kubernetes Application.


### TLDR
```bash
helm repo add generic-app https://small-hack.github.io/generic-app-helm
helm install generic-app/generic-app --generate-name
```

### Changing the deployment

Here's how to get started using your own docker container

```yaml
deployment:
  image:
    # -- provide this only if you're not hosting on hub.docker.com (docker.io)
    registry: ""
    # -- this can be set to any docker repo
    repository: "mydockercontainer"
    # -- docker image tag to pull
    tag: "latest"
```

#### Disabling the deployment

Sometimes you just need a job...

```yaml
deployment:
  enabled: false
```


### Enabling a job

```yaml
job:
  enabled: true
  image:
    # -- provide this only if you're not hosting on hub.docker.com (docker.io)
    registry: ""
    # -- this can be set to any docker repo
    repository: "mydockercontainer"
    # -- docker image tag to pull
    tag: "latest"
```

### Enabling the ingress

```yaml
ingress:
  enabled: true
```

### Disabling the service

```yaml
service:
  enabled: false
```

## Tips

Want to deploy on Argo CD? Checkout our [example ApplicationSet](https://github.com/small-hack/argocd-apps/tree/main/generic-app).

## Status

Submit any PRs you may have and please feel free to submit issues if you have a generic feature :P
