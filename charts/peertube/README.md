# peertube

![Version: 0.2.0](https://img.shields.io/badge/Version-0.2.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.0](https://img.shields.io/badge/AppVersion-0.0.0-informational?style=flat-square)

A peertube Helm chart for Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| cloudymax |  | <https://github.com/cloudymax> |
| JesseBot |  | <https://github.com/jessebot> |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| affinity | object | `{}` | affinity settings for the deployment |
| autoscaling.enabled | bool | `false` | enable autoscaling for the deployment |
| autoscaling.maxReplicas | int | `100` |  |
| autoscaling.minReplicas | int | `1` |  |
| autoscaling.targetCPUUtilizationPercentage | int | `80` |  |
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
| fullnameOverride | string | `""` | full name override for all peertube resources |
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
| ingress.className | string | `"nginx"` | ingress controller class name |
| ingress.enabled | bool | `true` | enable ingress from outside the cluster to this peertube instance |
| ingress.hosts[0].host | string | `"chart-example.local"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls[0].hosts[0] | string | `"chart-example.local"` |  |
| ingress.tls[0].secretName | string | `"peertube-tls"` |  |
| initcontainers | object | `{}` | extra init containers for the default deployment |
| livenessProbe | object | `{"httpGet":{"path":"/","port":"peertube"}}` | enable livenessProbe for the deployment |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` | node selector for deployment |
| peertube.admin.email | string | `""` | email address of peertube admin user |
| peertube.admin.existingSecret | string | `""` | use an existing Kubernetes Secret for Peertube's admin credentials |
| peertube.admin.existingSecretKeys.email | string | `""` | a key in an existing Kubernetes Secret for Peertube's admin user email |
| peertube.admin.existingSecretKeys.password | string | `""` | a key in an existing Kubernetes Secret for Peertube's admin password |
| peertube.admin.password | string | `""` | initial peertube of peertube admin password |
| peertube.existingSecret | string | `""` | use an existing Kubernetes Secret for Peertube's secret |
| peertube.existingSecretKey | string | `"secret"` | a key in an existing Kubernetes Secret for Peertube's secret |
| peertube.log_level | string | `"debug"` | set peertube's logging level |
| peertube.s3.access_key_id | string | `""` | access key id for connecting to s3 |
| peertube.s3.enabled | bool | `false` | enable object storage, s3, for peertube |
| peertube.s3.endpoint | string | `""` | s3 endpoint to connect to for peertube storage |
| peertube.s3.existingSecret | string | `""` | get the credentials for s3 from an existing Kubernetes Secret |
| peertube.s3.existingSecretKeys.access_key_id | string | `""` | key in existing secret for s3 access_key_id |
| peertube.s3.existingSecretKeys.endpoint | string | `""` | key in existing secret for s3 endpoint |
| peertube.s3.existingSecretKeys.secret_access_key | string | `""` | key in existing secret for s3 secret_access_key |
| peertube.s3.secret_access_key | string | `""` | secret access key id for connecting to s3 |
| peertube.s3.upload_acl_private | string | `"private"` |  |
| peertube.s3.upload_acl_public | string | `"public-read"` |  |
| peertube.secret | string | `""` | set peertube's secret |
| peertube.smtp.disable_starttls | bool | `false` | mail disable starttls |
| peertube.smtp.existingSecret | string | `""` | use an existing Kubernetes Secret to connect to SMTP host if set, ignores above smtp.host/port/username/password |
| peertube.smtp.existingSecretKeys.host | string | `""` | key in existing secret for smtp hostname |
| peertube.smtp.existingSecretKeys.password | string | `""` | key in existing secret for smtp password |
| peertube.smtp.existingSecretKeys.port | string | `""` | key in existing secret for smtp port |
| peertube.smtp.existingSecretKeys.username | string | `""` | key in existing secret for smtp username |
| peertube.smtp.from_address | string | `""` | email address to send emails from |
| peertube.smtp.host | string | `""` | mail hostname |
| peertube.smtp.password | string | `""` | mail password |
| peertube.smtp.port | string | `""` | mail port |
| peertube.smtp.tls | bool | `true` | mail tls setting |
| peertube.smtp.user | string | `""` | mail username |
| peertube.trust_proxy | string | `"10.0.0.0/8"` | set peertube's trusted proxies |
| peertube.webserver_hostname | string | `"chart-example.local"` | set peertube's hostname |
| peertube.webserver_https | bool | `true` | enable https for peertube web frontend |
| peertube.webserver_port | int | `443` | set peertube's port |
| podAnnotations | object | `{}` | extra pod annotations for the deployment |
| podLabels | object | `{}` | extra pod labels for the deployment |
| podSecurityContext | object | `{}` | pod securityContext deployment's main container |
| readinessProbe | object | `{"httpGet":{"path":"/","port":"peertube"}}` | enable readinessProbe for the deployment |
| replicaCount | int | `1` | replica count if not using autoscaling |
| resources | object | `{"limits":{"cpu":"4000m","memory":"4Gi"},"requests":{"cpu":"100m","memory":"512Mi"}}` | resources for the deployment |
| securityContext | object | `{}` | securityContext whole deployment |
| service.enabled | bool | `true` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.automount | bool | `true` | Automatically mount a ServiceAccount's API credentials? |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `"peertube-sa"` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` | tolerations of taints on a node |
| volumeMounts | list | `[{"mountPath":"/config/production.yaml","name":"peertube-config","subPath":"production.yaml"},{"mountPath":"/data","name":"peertube-data"},{"mountPath":"/config/custom-environment-variables.yaml","name":"custom-env-vars","subPath":"custom-environment-variables.yaml"}]` | Additional volumeMounts on the output Deployment definition. |
| volumes | list | `[{"configMap":{"name":"peertube-config"},"name":"peertube-config"},{"configMap":{"name":"custom-env-vars"},"name":"custom-env-vars"},{"name":"peertube-data","persistentVolumeClaim":{"claimName":"peertube-data"}}]` | Additional volumes on the output Deployment definition. |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.11.0](https://github.com/norwoodj/helm-docs/releases/v1.11.0)
