# cost-analyzer

![Version: 1.97.0-bb.0](https://img.shields.io/badge/Version-1.97.0--bb.0-informational?style=flat-square) ![AppVersion: 1.97.0](https://img.shields.io/badge/AppVersion-1.97.0-informational?style=flat-square)

A Helm chart that sets up Kubecost, Prometheus, and Grafana to monitor cloud costs.

## Learn More
* [Application Overview](docs/overview.md)
* [Other Documentation](docs/)

## Pre-Requisites

* Kubernetes Cluster deployed
* Kubernetes config installed in `~/.kube/config`
* Helm installed

Install Helm

https://helm.sh/docs/intro/install/

## Deployment

* Clone down the repository
* cd into directory
```bash
helm install cost-analyzer chart/
```

## Values

| Key | Type | Default | Description |
|-----|------|---------|-------------|
| global.prometheus.enabled | bool | `true` |  |
| global.prometheus.fqdn | string | `"http://cost-analyzer-prometheus-server.default.svc"` |  |
| global.thanos.enabled | bool | `false` |  |
| global.grafana.enabled | bool | `true` |  |
| global.grafana.domainName | string | `"cost-analyzer-grafana.default.svc"` |  |
| global.grafana.scheme | string | `"http"` |  |
| global.grafana.proxy | bool | `true` |  |
| global.amp.enabled | bool | `false` |  |
| global.amp.prometheusServerEndpoint | string | `"https://localhost:8085/<workspaceId>/"` |  |
| global.amp.remoteWriteService | string | `"https://aps-workspaces.us-west-2.amazonaws.com/workspaces/<workspaceId>/api/v1/remote_write"` |  |
| global.amp.sigv4.region | string | `"us-west-2"` |  |
| global.notifications.alertmanager.enabled | bool | `false` |  |
| global.notifications.alertmanager.fqdn | string | `"http://cost-analyzer-prometheus-server.default.svc"` |  |
| global.savedReports.enabled | bool | `false` |  |
| global.savedReports.reports[0].title | string | `"Example Saved Report 0"` |  |
| global.savedReports.reports[0].window | string | `"today"` |  |
| global.savedReports.reports[0].aggregateBy | string | `"namespace"` |  |
| global.savedReports.reports[0].idle | string | `"separate"` |  |
| global.savedReports.reports[0].accumulate | bool | `false` |  |
| global.savedReports.reports[0].filters[0].property | string | `"cluster"` |  |
| global.savedReports.reports[0].filters[0].value | string | `"cluster-one,cluster*"` |  |
| global.savedReports.reports[0].filters[1].property | string | `"namespace"` |  |
| global.savedReports.reports[0].filters[1].value | string | `"kubecost"` |  |
| global.savedReports.reports[1].title | string | `"Example Saved Report 1"` |  |
| global.savedReports.reports[1].window | string | `"month"` |  |
| global.savedReports.reports[1].aggregateBy | string | `"controllerKind"` |  |
| global.savedReports.reports[1].idle | string | `"share"` |  |
| global.savedReports.reports[1].accumulate | bool | `false` |  |
| global.savedReports.reports[1].filters[0].property | string | `"label"` |  |
| global.savedReports.reports[1].filters[0].value | string | `"app:cost*,environment:kube*"` |  |
| global.savedReports.reports[1].filters[1].property | string | `"namespace"` |  |
| global.savedReports.reports[1].filters[1].value | string | `"kubecost"` |  |
| global.savedReports.reports[2].title | string | `"Example Saved Report 2"` |  |
| global.savedReports.reports[2].window | string | `"2020-11-11T00:00:00Z,2020-12-09T23:59:59Z"` |  |
| global.savedReports.reports[2].aggregateBy | string | `"service"` |  |
| global.savedReports.reports[2].idle | string | `"hide"` |  |
| global.savedReports.reports[2].accumulate | bool | `true` |  |
| global.savedReports.reports[2].filters | list | `[]` |  |
| global.assetReports.enabled | bool | `false` |  |
| global.assetReports.reports[0].title | string | `"Example Asset Report 0"` |  |
| global.assetReports.reports[0].window | string | `"today"` |  |
| global.assetReports.reports[0].aggregateBy | string | `"type"` |  |
| global.assetReports.reports[0].accumulate | bool | `false` |  |
| global.assetReports.reports[0].filters[0].property | string | `"cluster"` |  |
| global.assetReports.reports[0].filters[0].value | string | `"cluster-one"` |  |
| global.podAnnotations | object | `{}` |  |
| global.additionalLabels | object | `{}` |  |
| kubecostToken | string | `nil` |  |
| pricingCsv.enabled | bool | `false` |  |
| pricingCsv.location.provider | string | `"AWS"` |  |
| pricingCsv.location.region | string | `"us-east-1"` |  |
| pricingCsv.location.URI | string | `"s3://kc-csv-test/pricing_schema.csv"` |  |
| pricingCsv.location.csvAccessCredentials | string | `"pricing-schema-access-secret"` |  |
| saml.enabled | bool | `false` |  |
| saml.secretName | string | `"kubecost-authzero"` |  |
| saml.idpMetadataURL | string | `"https://dev-elu2z98r.auth0.com/samlp/metadata/c6nY4M37rBP0qSO1IYIqBPPyIPxLS8v2"` |  |
| saml.appRootURL | string | `"http://localhost:9090"` |  |
| saml.authTimeout | int | `1440` |  |
| saml.redirectURL | string | `"https://dev-elu2z98r.auth0.com/v2/logout"` |  |
| saml.rbac.enabled | bool | `false` |  |
| saml.rbac.groups[0].name | string | `"admin"` |  |
| saml.rbac.groups[0].enabled | bool | `false` |  |
| saml.rbac.groups[0].assertionName | string | `"http://schemas.auth0.com/userType"` |  |
| saml.rbac.groups[0].assertionValues[0] | string | `"admin"` |  |
| saml.rbac.groups[0].assertionValues[1] | string | `"superusers"` |  |
| saml.rbac.groups[1].name | string | `"readonly"` |  |
| saml.rbac.groups[1].enabled | bool | `false` |  |
| saml.rbac.groups[1].assertionName | string | `"http://schemas.auth0.com/userType"` |  |
| saml.rbac.groups[1].assertionvalues[0] | string | `"readonly"` |  |
| saml.rbac.groups[2].name | string | `"editor"` |  |
| saml.rbac.groups[2].enabled | bool | `true` |  |
| saml.rbac.groups[2].assertionName | string | `"http://schemas.auth0.com/userType"` |  |
| saml.rbac.groups[2].assertionValues[0] | string | `"editor"` |  |
| oidc.enabled | bool | `false` |  |
| oidc.clientID | string | `""` |  |
| oidc.clientSecret | string | `""` |  |
| oidc.secretName | string | `"kubecost-oidc-secret"` |  |
| oidc.authURL | string | `"https://my.auth.server/authorize"` |  |
| oidc.loginRedirectURL | string | `"http://my.kubecost.url/model/oidc/authorize"` |  |
| oidc.discoveryURL | string | `"https://my.auth.server/.well-known/openid-configuration"` |  |
| systemProxy.enabled | bool | `false` |  |
| systemProxy.httpProxyUrl | string | `""` |  |
| systemProxy.httpsProxyUrl | string | `""` |  |
| systemProxy.noProxy | string | `""` |  |
| kubecostFrontend.image | string | `"gcr.io/kubecost1/frontend"` |  |
| kubecostFrontend.imagePullPolicy | string | `"Always"` |  |
| kubecostFrontend.resources.requests.cpu | string | `"10m"` |  |
| kubecostFrontend.resources.requests.memory | string | `"55Mi"` |  |
| kubecostFrontend.ipv6.enabled | bool | `true` |  |
| kubecostMetrics.exporter.enabled | bool | `false` |  |
| kubecostMetrics.exporter.port | int | `9005` |  |
| kubecostMetrics.exporter.prometheusScrape | bool | `true` |  |
| kubecostMetrics.exporter.resources | object | `{}` |  |
| kubecostMetrics.exporter.tolerations | list | `[]` |  |
| kubecostMetrics.exporter.affinity | object | `{}` |  |
| kubecostMetrics.exporter.service.annotations | object | `{}` |  |
| kubecostMetrics.exporter.serviceMonitor.enabled | bool | `false` |  |
| kubecostMetrics.exporter.serviceMonitor.additionalLabels | object | `{}` |  |
| kubecostMetrics.exporter.priorityClassName | list | `[]` |  |
| kubecostMetrics.exporter.additionalLabels | object | `{}` |  |
| kubecostMetrics.exporter.nodeSelector | object | `{}` |  |
| kubecostMetrics.exporter.extraArgs | list | `[]` |  |
| sigV4Proxy.image | string | `"public.ecr.aws/aws-observability/aws-sigv4-proxy:latest"` |  |
| sigV4Proxy.imagePullPolicy | string | `"Always"` |  |
| sigV4Proxy.name | string | `"aps"` |  |
| sigV4Proxy.port | int | `8005` |  |
| sigV4Proxy.region | string | `"us-west-2"` |  |
| sigV4Proxy.host | string | `"aps-workspaces.us-west-2.amazonaws.com"` |  |
| sigV4Proxy.extraEnv | string | `nil` |  |
| kubecostModel.image | string | `"gcr.io/kubecost1/cost-model"` |  |
| kubecostModel.imagePullPolicy | string | `"Always"` |  |
| kubecostModel.outOfClusterPromMetricsEnabled | bool | `false` |  |
| kubecostModel.warmCache | bool | `false` |  |
| kubecostModel.warmSavingsCache | bool | `true` |  |
| kubecostModel.etl | bool | `true` |  |
| kubecostModel.etlFileStoreEnabled | bool | `true` |  |
| kubecostModel.etlDailyStoreDurationDays | int | `91` |  |
| kubecostModel.etlHourlyStoreDurationHours | int | `49` |  |
| kubecostModel.etlReadOnlyMode | bool | `false` |  |
| kubecostModel.maxQueryConcurrency | int | `5` |  |
| kubecostModel.resources.requests.cpu | string | `"200m"` |  |
| kubecostModel.resources.requests.memory | string | `"55Mi"` |  |
| kubecostModel.extraArgs | list | `[]` |  |
| ingress.enabled | bool | `false` |  |
| ingress.annotations | string | `nil` |  |
| ingress.paths[0] | string | `"/"` |  |
| ingress.pathType | string | `"ImplementationSpecific"` |  |
| ingress.hosts[0] | string | `"cost-analyzer.local"` |  |
| ingress.tls | list | `[]` |  |
| nodeSelector | object | `{}` |  |
| tolerations | list | `[]` |  |
| affinity | object | `{}` |  |
| priority.enabled | bool | `false` |  |
| priority.name | string | `""` |  |
| networkPolicy.enabled | bool | `false` |  |
| networkPolicy.denyEgress | bool | `true` |  |
| networkPolicy.sameNamespace | bool | `true` |  |
| networkPolicy.costAnalyzer.enabled | bool | `false` |  |
| networkPolicy.costAnalyzer.annotations | object | `{}` |  |
| networkPolicy.costAnalyzer.additionalLabels | object | `{}` |  |
| podSecurityPolicy.enabled | bool | `true` |  |
| extraVolumes | list | `[]` |  |
| extraVolumeMounts | list | `[]` |  |
| persistentVolume.size | string | `"32Gi"` |  |
| persistentVolume.dbSize | string | `"32.0Gi"` |  |
| persistentVolume.enabled | bool | `true` |  |
| service.type | string | `"ClusterIP"` |  |
| service.port | int | `9090` |  |
| service.targetPort | int | `9090` |  |
| service.labels | object | `{}` |  |
| service.annotations | object | `{}` |  |
| remoteWrite.postgres.enabled | bool | `false` |  |
| remoteWrite.postgres.initImage | string | `"gcr.io/kubecost1/sql-init"` |  |
| remoteWrite.postgres.initImagePullPolicy | string | `"Always"` |  |
| remoteWrite.postgres.installLocal | bool | `true` |  |
| remoteWrite.postgres.remotePostgresAddress | string | `""` |  |
| remoteWrite.postgres.persistentVolume.size | string | `"200Gi"` |  |
| remoteWrite.postgres.auth.password | string | `"admin"` |  |
| prometheus.extraScrapeConfigs | string | `"- job_name: kubecost\n  honor_labels: true\n  scrape_interval: 1m\n  scrape_timeout: 60s\n  metrics_path: /metrics\n  scheme: http\n  dns_sd_configs:\n  - names:\n    - {{ template \"cost-analyzer.serviceName\" . }}\n    type: 'A'\n    port: 9003\n- job_name: kubecost-networking\n  kubernetes_sd_configs:\n    - role: pod\n  relabel_configs:\n  # Scrape only the the targets matching the following metadata\n    - source_labels: [__meta_kubernetes_pod_label_app]\n      action: keep\n      regex:  {{ template \"cost-analyzer.networkCostsName\" . }}\n"` |  |
| prometheus.server.resources | object | `{}` |  |
| prometheus.server.global.scrape_interval | string | `"1m"` |  |
| prometheus.server.global.scrape_timeout | string | `"10s"` |  |
| prometheus.server.global.evaluation_interval | string | `"1m"` |  |
| prometheus.server.global.external_labels.cluster_id | string | `"cluster-one"` |  |
| prometheus.server.persistentVolume.size | string | `"32Gi"` |  |
| prometheus.server.persistentVolume.enabled | bool | `true` |  |
| prometheus.server.extraArgs."query.max-concurrency" | int | `1` |  |
| prometheus.server.extraArgs."query.max-samples" | int | `100000000` |  |
| prometheus.server.tolerations | list | `[]` |  |
| prometheus.alertmanager.enabled | bool | `false` |  |
| prometheus.alertmanager.persistentVolume.enabled | bool | `true` |  |
| prometheus.nodeExporter.enabled | bool | `true` |  |
| prometheus.kubeStateMetrics.enabled | bool | `true` |  |
| prometheus.kube-state-metrics.disabled | bool | `false` |  |
| prometheus.pushgateway.enabled | bool | `false` |  |
| prometheus.pushgateway.persistentVolume.enabled | bool | `true` |  |
| prometheus.serverFiles.rules.groups[0].name | string | `"CPU"` |  |
| prometheus.serverFiles.rules.groups[0].rules[0].expr | string | `"sum(rate(container_cpu_usage_seconds_total{container_name!=\"\"}[5m]))"` |  |
| prometheus.serverFiles.rules.groups[0].rules[0].record | string | `"cluster:cpu_usage:rate5m"` |  |
| prometheus.serverFiles.rules.groups[0].rules[1].expr | string | `"rate(container_cpu_usage_seconds_total{container_name!=\"\"}[5m])"` |  |
| prometheus.serverFiles.rules.groups[0].rules[1].record | string | `"cluster:cpu_usage_nosum:rate5m"` |  |
| prometheus.serverFiles.rules.groups[0].rules[2].expr | string | `"avg(irate(container_cpu_usage_seconds_total{container_name!=\"POD\", container_name!=\"\"}[5m])) by (container_name,pod_name,namespace)"` |  |
| prometheus.serverFiles.rules.groups[0].rules[2].record | string | `"kubecost_container_cpu_usage_irate"` |  |
| prometheus.serverFiles.rules.groups[0].rules[3].expr | string | `"sum(container_memory_working_set_bytes{container_name!=\"POD\",container_name!=\"\"}) by (container_name,pod_name,namespace)"` |  |
| prometheus.serverFiles.rules.groups[0].rules[3].record | string | `"kubecost_container_memory_working_set_bytes"` |  |
| prometheus.serverFiles.rules.groups[0].rules[4].expr | string | `"sum(container_memory_working_set_bytes{container_name!=\"POD\",container_name!=\"\"})"` |  |
| prometheus.serverFiles.rules.groups[0].rules[4].record | string | `"kubecost_cluster_memory_working_set_bytes"` |  |
| prometheus.serverFiles.rules.groups[1].name | string | `"Savings"` |  |
| prometheus.serverFiles.rules.groups[1].rules[0].expr | string | `"sum(avg(kube_pod_owner{owner_kind!=\"DaemonSet\"}) by (pod) * sum(container_cpu_allocation) by (pod))"` |  |
| prometheus.serverFiles.rules.groups[1].rules[0].record | string | `"kubecost_savings_cpu_allocation"` |  |
| prometheus.serverFiles.rules.groups[1].rules[0].labels.daemonset | string | `"false"` |  |
| prometheus.serverFiles.rules.groups[1].rules[1].expr | string | `"sum(avg(kube_pod_owner{owner_kind=\"DaemonSet\"}) by (pod) * sum(container_cpu_allocation) by (pod)) / sum(kube_node_info)"` |  |
| prometheus.serverFiles.rules.groups[1].rules[1].record | string | `"kubecost_savings_cpu_allocation"` |  |
| prometheus.serverFiles.rules.groups[1].rules[1].labels.daemonset | string | `"true"` |  |
| prometheus.serverFiles.rules.groups[1].rules[2].expr | string | `"sum(avg(kube_pod_owner{owner_kind!=\"DaemonSet\"}) by (pod) * sum(container_memory_allocation_bytes) by (pod))"` |  |
| prometheus.serverFiles.rules.groups[1].rules[2].record | string | `"kubecost_savings_memory_allocation_bytes"` |  |
| prometheus.serverFiles.rules.groups[1].rules[2].labels.daemonset | string | `"false"` |  |
| prometheus.serverFiles.rules.groups[1].rules[3].expr | string | `"sum(avg(kube_pod_owner{owner_kind=\"DaemonSet\"}) by (pod) * sum(container_memory_allocation_bytes) by (pod)) / sum(kube_node_info)"` |  |
| prometheus.serverFiles.rules.groups[1].rules[3].record | string | `"kubecost_savings_memory_allocation_bytes"` |  |
| prometheus.serverFiles.rules.groups[1].rules[3].labels.daemonset | string | `"true"` |  |
| networkCosts.enabled | bool | `false` |  |
| networkCosts.podSecurityPolicy.enabled | bool | `false` |  |
| networkCosts.image | string | `"gcr.io/kubecost1/kubecost-network-costs:v16.0"` |  |
| networkCosts.imagePullPolicy | string | `"Always"` |  |
| networkCosts.updateStrategy.type | string | `"RollingUpdate"` |  |
| networkCosts.prometheusScrape | bool | `false` |  |
| networkCosts.trafficLogging | bool | `true` |  |
| networkCosts.port | int | `3001` |  |
| networkCosts.resources | object | `{}` |  |
| networkCosts.extraArgs | list | `[]` |  |
| networkCosts.config.destinations.in-zone[0] | string | `"127.0.0.1"` |  |
| networkCosts.config.destinations.in-zone[1] | string | `"169.254.0.0/16"` |  |
| networkCosts.config.destinations.in-zone[2] | string | `"10.0.0.0/8"` |  |
| networkCosts.config.destinations.in-zone[3] | string | `"172.16.0.0/12"` |  |
| networkCosts.config.destinations.in-zone[4] | string | `"192.168.0.0/16"` |  |
| networkCosts.config.destinations.in-region | list | `[]` |  |
| networkCosts.config.destinations.cross-region | list | `[]` |  |
| networkCosts.config.destinations.direct-classification | list | `[]` |  |
| networkCosts.config.services.google-cloud-services | bool | `false` |  |
| networkCosts.config.services.amazon-web-services | bool | `false` |  |
| networkCosts.config.services.azure-cloud-services | bool | `false` |  |
| networkCosts.tolerations | list | `[]` |  |
| networkCosts.affinity | object | `{}` |  |
| networkCosts.service.annotations | object | `{}` |  |
| networkCosts.priorityClassName | list | `[]` |  |
| networkCosts.podMonitor.enabled | bool | `false` |  |
| networkCosts.podMonitor.additionalLabels | object | `{}` |  |
| networkCosts.additionalLabels | object | `{}` |  |
| networkCosts.nodeSelector | object | `{}` |  |
| networkCosts.annotations | object | `{}` |  |
| kubecostDeployment.replicas | int | `1` |  |
| kubecostDeployment.leaderFollower.enabled | bool | `false` |  |
| clusterController.enabled | bool | `false` |  |
| clusterController.image | string | `"gcr.io/kubecost1/cluster-controller:v0.1.0"` |  |
| clusterController.imagePullPolicy | string | `"Always"` |  |
| reporting.logCollection | bool | `true` |  |
| reporting.productAnalytics | bool | `true` |  |
| reporting.errorReporting | bool | `true` |  |
| reporting.valuesReporting | bool | `true` |  |
| serviceMonitor.enabled | bool | `false` |  |
| serviceMonitor.additionalLabels | object | `{}` |  |
| prometheusRule.enabled | bool | `false` |  |
| prometheusRule.additionalLabels | object | `{}` |  |
| supportNFS | bool | `false` |  |
| initChownDataImage | string | `"busybox"` |  |
| initChownData.resources | object | `{}` |  |
| grafana.rbac.pspEnabled | bool | `true` |  |
| grafana.datasources."datasources.yaml".apiVersion | int | `1` |  |
| grafana.datasources."datasources.yaml".datasources[0].name | string | `"prometheus-kubecost"` |  |
| grafana.datasources."datasources.yaml".datasources[0].type | string | `"prometheus"` |  |
| grafana.datasources."datasources.yaml".datasources[0].url | string | `"http://kubecost-prometheus-server.kubecost.svc.cluster.local"` |  |
| grafana.datasources."datasources.yaml".datasources[0].access | string | `"proxy"` |  |
| grafana.datasources."datasources.yaml".datasources[0].isDefault | bool | `false` |  |
| grafana.sidecar.dashboards.enabled | bool | `true` |  |
| grafana.sidecar.dashboards.label | string | `"grafana_dashboard"` |  |
| grafana.sidecar.dashboards.annotations | object | `{}` |  |
| grafana.sidecar.dashboards.error_throttle_sleep | int | `0` |  |
| grafana.sidecar.datasources.enabled | bool | `false` |  |
| grafana.sidecar.datasources.error_throttle_sleep | int | `0` |  |
| grafana."grafana.ini".server.root_url | string | `"%(protocol)s://%(domain)s:%(http_port)s/grafana"` |  |
| serviceAccount.create | bool | `true` |  |
| serviceAccount.annotations | object | `{}` |  |
| awsstore.useAwsStore | bool | `false` |  |
| awsstore.createServiceAccount | bool | `false` |  |
| istio.enabled | bool | `false` |  |
| istio.host | string | `"kubecost.bigbang.dev"` |  |
| istio.gateways[0] | string | `"istio-system/main"` |  |

## Contributing

Please see the [contributing guide](./CONTRIBUTING.md) if you are interested in contributing.
