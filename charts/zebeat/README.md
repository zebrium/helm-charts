# zebeat

Helm chart for the deployment of zebeat, Zebrium's Elastic beat integration

![Version: 0.1.0](https://img.shields.io/badge/Version-0.1.0-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 0.3.0](https://img.shields.io/badge/AppVersion-0.3.0-informational?style=flat-square)

## Installing the Chart

To install the chart with the release name `zebrium`:

```console
$ helm repo add zebrium http://charts.zebrium.com
$ helm upgrade -i zebeat zebrium/zebeat --namespace zebrium --create-namespace
```

## Uninstalling
To uninstall the chart with the release name `zebrium`:
```console
helm delete zebeat -n zebrium
```

## Additional Information
### Zebeat Config

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| accessTokens | object | `{"https://example.com":["example12345"]}` | Map of access tokens for Zebrium Deployments |
| affinity | object | `{}` |  |
| extraEnvs | object | `{}` | Additional Env Vars to inject into the container. |
| fullnameOverride | string | `""` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.repository | string | `"zebrium/zebeat"` |  |
| image.tag | string | `""` | Overrides the image tag whose default is the chart appVersion. |
| imagePullSecrets | list | `[]` |  |
| metricbeatConfig | object | `{"metricbeat.yml":"metricbeat.modules:\n  - modules: zebrium\n    metricsets:\n      - \"logs\"\n      - \"detections\"\n    enabled: true\n    period: 30s\n    hosts: [\"https://echo.qa.zebrium.com\"]\n    access_tokens_file: \"/access_tokens.yml\"\n"}` | Metricbeat Confiugration. Hosts must match all host mapped in .Values.accessTokens |
| nameOverride | string | `""` |  |
| nodeSelector | object | `{}` |  |
| podAnnotations | object | `{}` |  |
| podSecurityContext | object | `{}` |  |
| replicaCount | int | `1` |  |
| resources | object | `{}` |  |
| secretMounts | object | `{}` | A list of secrets and their paths to mount inside the pod This is useful for mounting certificates for security other sensitive values |
| securityContext | object | `{}` |  |
| serviceAccount.annotations | object | `{}` | Annotations to add to the service account |
| serviceAccount.create | bool | `true` | Specifies whether a service account should be created |
| serviceAccount.name | string | `""` | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations | list | `[]` |  |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| b3arp | braeden@zebrium.com |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)