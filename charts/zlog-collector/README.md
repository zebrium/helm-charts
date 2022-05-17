# zlog-collector

Zebrium log collector for Kubernetes.

![Version: 1.53.0](https://img.shields.io/badge/Version-1.53.0-informational?style=flat-square) ![AppVersion: 1.50.0](https://img.shields.io/badge/AppVersion-1.50.0-informational?style=flat-square)

## Installing the Chart

To install the chart with the release name `zebrium`:

```console
$ helm repo add zebrium http://charts.zebrium.com
$ helm upgrade -i zlog-collector zebrium/zlog-collector --namespace zebrium --create-namespace --set zebrium.collectorUrl=YOUR_ZE_API_URL,zebrium.authToken=YOUR_ZE_API_AUTH_TOKEN,zebrium.deployment=YOUR_DEPLOYMENT_NAME,zebrium.timezone=KUBERNETES_HOST_TIMEZONE
```
`KUBERNETES_HOST_TIMEZONE` is the timezone setting on kubernetes host, for example, "UTC" or "America/Los_Angeles". If this option is not provided, default value UTC will be used.

## Uninstalling
To uninstall the chart with the release name `zebrium`:
```console
helm delete zlog-collector -n zebrium
```

## Additional Information

### Log Path Mapping
Log path mapping is the process of detecting semantic items in log file paths (ids, configs and tags)
then including them in the Zebrium log data. This is enabled by providing a JSON mapping file to
the log collector, as described in the repo at https://www.github.com/zebrium/ze-fluentd-plugin. To use this functionality with the supplied
helm chart a **customValues.yaml** file should be completed and supplied to the **helm install**
command line with:

```
helm install ... -f customValues.yaml ...
```

A prototype example_logPathMappings.yaml file is provided in the repo under the example directory, with format:

```
overridePMFConfig: true
zebrium:
pathMapFile: "pathMapFile.json"
customPMFConfig: {
"mappings": {
"patterns":["/var/log/remote_logs/(?<host>[^/]+)/.*"],
    "tags": [],
    "ids" : [
    "host"],
    "configs": []
    }
    }
```
### Custom Namespace to Service Group Mapping
Custom Namespace to Service Group Matching is the process of dynamically assigning a service group to a log stream based on the resources namesapce. This is enabled by providing a JSON mapping file to
the log collector. To use this functionality with the supplied
helm chart a **customValues.yaml** file should be completed and supplied to the **helm install**
command line with:

```
helm install ... -f customValues.yaml ...
```

A prototype example_ns_svcgrp.yaml file is provided in the repo under the example directory, with format:

```
overrideSVCGRPConfig: true
zebrium:
svcgrpMapFile: "svcgrpMapFile.json"
customSVCGRPConfig: {
"mynamespace1" : "svcgrp1",
"mynamespace2" : "svcgrp1",
"mynamespace3" : "svcgrp3"
}
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| daemonset.dnsPolicy | string | `"ClusterFirst"` |  |
| daemonset.nodeSelector | object | `{}` |  |
| daemonset.priorityClassName | string | `""` |  |
| daemonset.tolerateAllTaints | bool | `false` |  |
| daemonset.tolerations | list | `[]` |  |
| extraEnv | list | `[]` |  |
| image.name | string | `"zebrium/zlog-collector"` |  |
| image.pullPolicy | string | `"Always"` |  |
| image.tag | string | `"latest"` |  |
| resources.limits.cpu | string | `"1000m"` |  |
| resources.limits.memory | string | `"1Gi"` |  |
| resources.requests.cpu | string | `"20m"` |  |
| resources.requests.memory | string | `"500Mi"` |  |
| ruby.gcHeapOldObjectLimitFactor | float | `1.2` |  |
| secret.enabled | bool | `true` |  |
| services.automountServiceAccountToken | bool | `true` |  |
| services.automountServiceAccountTokenSupported | bool | `false` |  |
| updateStrategy | string | `"OnDelete"` |  |
| zebrium.authToken | string | `""` |  |
| zebrium.autoupdate | string | `"1"` |  |
| zebrium.bufferChunkLimitRecords | int | `40000` |  |
| zebrium.bufferChunkLimitSize | string | `"8MB"` |  |
| zebrium.bufferRetryMaxTimes | int | `360` |  |
| zebrium.bufferRetryTimeout | string | `"1h"` |  |
| zebrium.bufferRetryWait | string | `"10s"` |  |
| zebrium.bufferTotalLimitSize | string | `"64GB"` |  |
| zebrium.collectorUrl | string | `""` |  |
| zebrium.deployment | string | `"default"` |  |
| zebrium.disableEc2MetaData | string | `"true"` |  |
| zebrium.ec2ApiClientTimeoutSecs | string | `"1"` |  |
| zebrium.excludePath | string | `"[\"/var/log/boot.log\",\"/var/log/lastlog\"]"` |  |
| zebrium.excludePodRegex | string | `""` |  |
| zebrium.flushInterval | string | `"30s"` |  |
| zebrium.flushThreadCount | string | `"4"` |  |
| zebrium.handleHostAsConfig | bool | `false` |  |
| zebrium.k8sApiSecretName | string | `""` |  |
| zebrium.logFile | string | `""` |  |
| zebrium.logLevel | string | `"info"` |  |
| zebrium.name | string | `"zlog-collector"` |  |
| zebrium.nodeLogsPath | string | `"/var/log/*.log,/var/log/syslog,/var/log/messages,/var/log/secure"` |  |
| zebrium.pathMapFile | string | `""` |  |
| zebrium.svcgrpMapFile | string | `""` |  |
| zebrium.tailFromHead | string | `"true"` |  |
| zebrium.timezone | string | `"UTC"` |  |
| zebrium.useHostEtcHostnameFile | bool | `false` |  |
| zebrium.verifyK8sApiSSL | bool | `true` |  |
| zebrium.verifySSL | string | `"true"` |  |

## Maintainers

| Name | Email | Url |
| ---- | ------ | --- |
| b3arp | braeden@zebrium.com |  |

----------------------------------------------
Autogenerated from chart metadata using [helm-docs v1.5.0](https://github.com/norwoodj/helm-docs/releases/v1.5.0)