# peertube

![Version: 0.0.2](https://img.shields.io/badge/Version-0.0.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.0.0](https://img.shields.io/badge/AppVersion-0.0.0-informational?style=flat-square)

A peertube Helm chart for Kubernetes

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| JesseBot |  | <https://github.com/jessebot> |
| cloudymax |  | <https://github.com/cloudymax> |

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| deployment.affinity | object | `{}` | affinity settings for the deployment |
| deployment.autoscaling | object | `{"enabled":false,"maxReplicas":100,"minReplicas":1,"targetCPUUtilizationPercentage":80}` | autoscaling for the deployment |
| deployment.containerCommand | list | `["gosu","peertube","npm","start"]` | command to pass to docker container |
| deployment.enabled | bool | `true` | enable the deployment vs job vs cronjob |
| deployment.env | list | `[{"name":"PEERTUBE_LOG_LEVEL","value":"debug"},{"name":"POSTGRES_USER","value":"peertube"},{"name":"POSTGRES_DB","value":"peertube"},{"name":"PEERTUBE_DB_HOSTNAME","value":"peertube-postgres-rw"},{"name":"PEERTUBE_DB_USERNAME","value":"peertube"},{"name":"PEERTUBE_DB_PASSWORD","valueFrom":{"secretKeyRef":{"key":"password","name":"peertube-pgsql-credentials"}}},{"name":"POSTGRES_PASSWORD","valueFrom":{"secretKeyRef":{"key":"password","name":"peertube-pgsql-credentials"}}},{"name":"PEERTUBE_TRUST_PROXY","value":"[\"10.0.0.0/8\"]"},{"name":"PEERTUBE_REDIS_HOSTNAME","value":"valkey-primary"},{"name":"PEERTUBE_REDIS_AUTH","valueFrom":{"secretKeyRef":{"key":"valkey-password","name":"peertube-valkey-credentials"}}},{"name":"PEERTUBE_WEBSERVER_HOSTNAME","value":"peertube.buildstar.online"},{"name":"PEERTUBE_WEBSERVER_PORT","value":"443"},{"name":"PEERTUBE_WEBSERVER_HTTPS","value":"true"},{"name":"PEERTUBE_SECRET","valueFrom":{"secretKeyRef":{"key":"password","name":"peertube-secret"}}},{"name":"PEERTUBE_ADMIN_EMAIL","value":"admin@cloudydev.net"},{"name":"PEERTUBE_OBJECT_STORAGE_ENABLED","value":"false"},{"name":"PEERTUBE_OBJECT_STORAGE_ENDPOINT","value":""},{"name":"PEERTUBE_OBJECT_STORAGE_UPLOAD_ACL_PUBLIC","value":"public-read"},{"name":"PEERTUBE_OBJECT_STORAGE_UPLOAD_ACL_PRIVATE","value":"private"},{"name":"PEERTUBE_OBJECT_STORAGE_CREDENTIALS_ACCESS_KEY_ID","valueFrom":{"secretKeyRef":{"key":"accesskey","name":"peertube-s3-videos-credentials"}}},{"name":"PEERTUBE_OBJECT_STORAGE_CREDENTIALS_SECRET_ACCESS_KEY","valueFrom":{"secretKeyRef":{"key":"secretkey","name":"peertube-s3-videos-credentials"}}}]` | env list for deployment main container |
| deployment.envFrom | list | `[]` | env from list for deployment main container |
| deployment.image.pullPolicy | string | `"IfNotPresent"` | image pull policy, set to Always if using latest and it changes frequently |
| deployment.image.registry | string | `"docker.io"` | docker registry if not using docker.io |
| deployment.image.repository | string | `"chocobozzz/peertube"` | docker repo |
| deployment.image.tag | string | `"production-bookworm"` | Overrides the image tag whose default is latest |
| deployment.imagePullSecrets | list | `[]` | optional image pull secrets |
| deployment.initcontainers | object | `{}` | extra init containers for the default deployment |
| deployment.livenessProbe | object | `{"enabled":true,"httpGet":{"path":"/","port":"peertube"}}` | livenessProbe for the deployment |
| deployment.nodeSelector | object | `{}` | node selector for deployment |
| deployment.podAnnotations | object | `{}` | extra pod annotations for the deployment |
| deployment.podLabels | object | `{}` | extra pod labels for the deployment |
| deployment.podSecurityContext | object | `{}` | pod securityContext deployment's main container |
| deployment.readinessProbe | object | `{"enabled":true,"httpGet":{"path":"/","port":"peertube"}}` | readinessProbe for the deployment |
| deployment.replicaCount | int | `1` | replica count if not using autoscaling |
| deployment.resources | object | `{"limits":{"cpu":4,"memory":"4096Mi"},"requests":{"cpu":"100m","memory":"512Mi"}}` | resources for the deployment |
| deployment.securityContext | object | `{}` | securityContext whole deployment |
| deployment.tolerations | list | `[]` | tolerations of taints on a node |
| deployment.volumeMounts | list | `[{"mountPath":"/config/production.yaml","name":"peertube-config","subPath":"production.yaml"},{"mountPath":"/data","name":"peertube-data"},{"mountPath":"/config/custom-environment-variables.yaml","name":"custom-env-vars","subPath":"custom-environment-variables.yaml"}]` | Additional volumeMounts on the output Deployment definition. |
| deployment.volumes | list | `[{"configMap":{"name":"peertube-config"},"name":"peertube-config"},{"configMap":{"name":"custom-env-vars"},"name":"custom-env-vars"},{"name":"peertube-data","persistentVolumeClaim":{"claimName":"peertube-data"}}]` | Additional volumes on the output Deployment definition. |
| fullnameOverride | string | `""` |  |
| ingress.annotations."cert-manager.io/cluster-issuer" | string | `"letsencrypt-prod"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/configuration-snippet" | string | `"more_set_headers \"X-Frame-Options: ALLOWALL\";\nproxy_set_header Host $host;\n"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/connection-proxy-header" | string | `"keep-alive"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/enable-cors" | string | `"true"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/force-ssl-redirect" | string | `"true"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/proxy-body-size" | string | `"500m"` |  |
| ingress.annotations."nginx.ingress.kubernetes.io/ssl-redirect" | string | `"true"` |  |
| ingress.className | string | `"nginx"` |  |
| ingress.enabled | bool | `true` |  |
| ingress.hosts[0].host | string | `"peertube.buildstar.online"` |  |
| ingress.hosts[0].paths[0].path | string | `"/"` |  |
| ingress.hosts[0].paths[0].pathType | string | `"Prefix"` |  |
| ingress.tls[0].hosts[0] | string | `"chart-example.local"` |  |
| ingress.tls[0].secretName | string | `"peertube-tls"` |  |
| job.affinity | object | `{}` | affinity settings for the job |
| job.containerCommand | list | `[]` | command to pass to docker container |
| job.enabled | bool | `false` | enable a job |
| job.env | list | `[]` | env list for job main container |
| job.envFrom | list | `[]` | env from list for job main container |
| job.image.pullPolicy | string | `"IfNotPresent"` | image pull policy, set to Always if using latest and it changes frequently |
| job.image.registry | string | `"docker.io"` | docker registry if not using docker.io |
| job.image.repository | string | `"nginx"` | docker repo |
| job.image.tag | string | `"latest"` | Overrides the image tag whose default is latest |
| job.imagePullSecrets | list | `[]` | optional image pull secrets |
| job.initcontainers | object | `{}` | extra init containers for the default job |
| job.nodeSelector | object | `{}` | node selector for job |
| job.podAnnotations | object | `{}` | extra pod annotations for the job |
| job.podLabels | object | `{}` | extra pod labels for the job |
| job.podSecurityContext | object | `{}` | pod securityContext job's main container |
| job.replicaCount | int | `1` | replica count if not using autoscaling |
| job.resources | object | `{}` | resources for the job |
| job.restartPolicy | string | `"never"` | restart policy if the job fails; can be never, or always |
| job.securityContext | object | `{}` | securityContext whole job |
| job.tolerations | list | `[]` | tolerations of taints on a node |
| job.volumeMounts | list | `[]` | Additional volumeMounts on the output job definition. |
| job.volumes | list | `[]` | Additional volumes on the output job definition. |
| nameOverride | string | `""` |  |
| service.enabled | bool | `true` |  |
| service.port | int | `80` |  |
| service.type | string | `"ClusterIP"` |  |
| serviceAccount.annotations | object | `{}` |  |
| serviceAccount.automount | bool | `true` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.name | string | `"peertube-sa"` |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.14.2](https://github.com/norwoodj/helm-docs/releases/v1.14.2)
