# peertube

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.0](https://img.shields.io/badge/AppVersion-0.0.0-informational?style=flat-square)

A peertube Helm chart for Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| JesseBot |  | <https://github.com/jessebot> |
| cloudymax |  | <https://github.com/cloudymax> |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | affinity settings for the deployment |
| autoscaling | object | `{"enabled":false,"maxReplicas":100,"minReplicas":1,"targetCPUUtilizationPercentage":80}` | autoscaling for the deployment |
| containerCommand | list | `["gosu","peertube","npm","start"]` | command to pass to docker container |
| envFrom | list | `[]` |  |
| externalDatabase.database | string | `"peertube"` | postgresql database name |
| externalDatabase.enabled | bool | `true` | enable external database, if postgresql.enabled=false is set |
| externalDatabase.existingSecret | string | `""` | use an existing Kubernetes Secret to connect to PostgreSQL |
| externalDatabase.existingSecretKeys.database | string | `""` |  |
| externalDatabase.existingSecretKeys.hostname | string | `""` |  |
| externalDatabase.existingSecretKeys.password | string | `""` |  |
| externalDatabase.existingSecretKeys.username | string | `""` |  |
| externalDatabase.hostname | string | `"peertube-postgres-rw"` | postgresql hostname |
| externalDatabase.password | string | `""` | postgresql password |
| externalDatabase.username | string | `"peertube"` | postgresql username |
| externalValkey.enabled | bool | `true` | enable external valkey/redis, if valkey.enabled=false is set |
| externalValkey.existingSecret | string | `""` | use an existing Kubernetes Secret to connect to Redis/Valkey |
| externalValkey.existingSecretKey | string | `"valkey-password"` | key to use in an existing Kubernetes Secret to connect to Redis/Valkey |
| externalValkey.hostname | string | `"valkey-primary"` | hostname of external valkey/redis |
| externalValkey.password | string | `""` | valkey/redis password |
| extraEnv | list | `[]` | env list for deployment main container |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"IfNotPresent"` | image pull policy, set to Always if using latest and it changes frequently |
| image.registry | string | `"docker.io"` | docker registry if not using docker.io |
| image.repository | string | `"chocobozzz/peertube"` | docker repo |
| image.tag | string | `"production-bookworm"` | Overrides the image tag whose default is latest |
| imagePullSecrets | list | `[]` | optional image pull secrets |
| ingress.annotations."cert-manager.io/cluster-issuer" | string | `"letsencrypt-prod"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/configuration-snippet" | string | `"more_set_headers \"X-Frame-Options: ALLOWALL\";\nproxy_set_header Host $host;\n"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/connection-proxy-header" | string | `"keep-alive"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/force-ssl-redirect" | string | `"true"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-body-size" | string | `"500m"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/ssl-redirect" | string | `"true"` |  |
| ingress.className | string | `"nginx"` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls[0].hosts[0] | string | `"chart-example.local"` |  |
| ingress.tls[0].secretName | string | `"peertube-tls"` |  |
| initcontainers | object | `{}` | extra init containers for the default deployment |
| livenessProbe | object | `{"enabled":true,"httpGet":{"path":"/","port":"peertube"}}` | livenessProbe for the deployment |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | node selector for deployment |
| peertube.admin_email | string | `""` | email address of peertube admin user |
| peertube.existingSecret | string | `""` | use an existing Kubernetes Secret for Peetube's secret |
| peertube.existingSecretKey | string | `"secret"` | a key in an existing Kubernetes Secret for Peetube's secret |
| peertube.log_level | string | `"debug"` | set peertube's logging level |
| peertube.s3.access_key_id | string | `""` | access key id for connecting to s3 |
| peertube.s3.enabled | bool | `false` | enable object storage, s3, for peertube |
| peertube.s3.endpoint | string | `""` | s3 endpoint to connect to for peertube storage |
| peertube.s3.existingSecret | string | `""` | get the credentials for s3 from an existing Kubernetes Secret |
| peertube.s3.existingSecretKeys.access_key_id | string | `""` |  |
| peertube.s3.existingSecretKeys.endpoint | string | `""` |  |
| peertube.s3.existingSecretKeys.secret_access_key | string | `""` |  |
| peertube.s3.secret_access_key | string | `""` | secret access key id for connecting to s3 |
| peertube.s3.upload_acl_private | string | `"private"` |  |
| peertube.s3.upload_acl_public | string | `"public-read"` |  |
| peertube.secret | string | `""` | set peertube's secret |
| peertube.smtp.disable_starttls | bool | `false` |  |
| peertube.smtp.existingSecret | string | `""` | use an existing Kubernetes Secret to connect to SMTP |
| peertube.smtp.existingSecretKeys.host | string | `""` |  |
| peertube.smtp.existingSecretKeys.password | string | `""` |  |
| peertube.smtp.existingSecretKeys.username | string | `""` |  |
| peertube.smtp.from_address | string | `""` |  |
| peertube.smtp.host | string | `""` |  |
| peertube.smtp.password | string | `""` |  |
| peertube.smtp.port | string | `""` |  |
| peertube.smtp.tls | string | `""` |  |
| peertube.smtp.user | string | `""` |  |
| peertube.trust_proxy | string | `"[\"10.0.0.0/8\"]"` | set peertube's trusted proxies |
| peertube.webserver_hostname | string | `"chart-example.local"` | set peertube's hostname |
| peertube.webserver_https | bool | `true` | enable https for peertube web frontend |
| peertube.webserver_port | int | `443` | set peertube's port |
| podAnnotations | object | `{}` | extra pod annotations for the deployment |
| podLabels | object | `{}` | extra pod labels for the deployment |
| podSecurityContext | object | `{}` | pod securityContext deployment's main container |
| readinessProbe | object | `{"enabled":true,"httpGet":{"path":"/","port":"peertube"}}` | readinessProbe for the deployment |
| replicaCount | int | `1` | replica count if not using autoscaling |
| resources | object | `{"limits":{"cpu":"4000m","memory":"4Gi"},"requests":{"cpu":"100m","memory":"512Mi"}}` | resources for the deployment |
| securityContext | object | `{}` | securityContext whole deployment |
| service.enabled | bool | `true` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `"peertube-sa"` |  |
| tolerations | list | `[]` | tolerations of taints on a node |
| volumeMounts | list | `[{"mountPath":"/config/production.yaml","name":"peertube-config","subPath":"production.yaml"},{"mountPath":"/data","name":"peertube-data"},{"mountPath":"/config/custom-environment-variables.yaml","name":"custom-env-vars","subPath":"custom-environment-variables.yaml"}]` | Additional volumeMounts on the output Deployment definition. |
| volumes | list | `[{"configMap":{"name":"peertube-config"},"name":"peertube-config"},{"configMap":{"name":"custom-env-vars"},"name":"custom-env-vars"},{"name":"peertube-data","persistentVolumeClaim":{"claimName":"peertube-data"}}]` | Additional volumes on the output Deployment definition. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
