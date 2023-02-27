# Zebrium's Helm Chart Repository

This repo contains all of the Internal [Helm](https://helm.sh/) charts for Zebrium. Included charts are listed below and stored in the chart directory.  Please follow the links below to see the associated readme for each chart.

## Charts
* [raw](charts/raw/README.md)
* [zebeat](charts/zebeat/README.md)
* [zlog-collector](charts/zlog-collector/README.md)

## Prerequisites

- Kubernetes 1.15+ with Beta APIs enabled
- PV provisioner support in the underlying infrastructure

## Installing [Helm](https://helm.sh)

```
curl -L https://git.io/get_helm.sh | bash
helm init
```

## Installing Zebrium Helm Repository
```
helm repo add zebrium https://charts.zebrium.com
helm repo update
```
## Installing a Chart
Search all the repositories avilable 
```
helm search repo zebrium -l
```
Install specific chart 
```
helm install zlog zebrium/zlog-collector
helm status zlog
```
## Uninstalling a Chart
To uninstall/delete the `zlog` deployment: 
```
helm delete zlog
```
## Contributing

For contributing to these charts, please see our [contributing guidlines](charts/CONTRIBUTING.md).  Please reach out to repo owners for any direct questions. 