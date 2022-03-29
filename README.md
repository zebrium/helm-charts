#Welcome to Zebrium's Helm Chart Repository
 
[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

`helm repo add <alias> https://charts.zebrium.com`

If you had already added this repo earlier, run `helm repo update` to retrieve
the latest versions of the packages.  You can then run `helm search repo
<alias>` to see the charts.

To install the <chart-name> chart:

    helm install my-<chart-name> <alias>/<chart-name>

To uninstall the chart:

    helm delete my-<chart-name>

##Charts
| Chart Name |  Description| Source |
| :---- |:---:| :---: |
| zbeat | Zebrium's Elasticsearch Beat Integration | https://github.com/zebrium/helm-charts/tree/main/charts/zebeat | 
| zlog-collector| Zebrium's Log Collector for Kubernetes| https://github.com/zebrium/helm-charts/tree/main/charts/zebeat|