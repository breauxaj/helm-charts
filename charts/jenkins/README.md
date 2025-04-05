# Jenkins Helm Chart

This Helm chart installs [Jenkins](https://jenkins.io/) with
some customizations.

- [Jenkins Helm Chart](#jenkins-helm-chart)
- [Requirements](#requirements)
- [Installing](#installing)
- [Uninstalling](#uninstalling)
- [Configuration](#configuration)

## Requirements

- Kubernetes >= 1.30
- Helm >= 3.0

## Installing

```code
kubectl create namespace my-namespace
helm install release-name jenkins/ --values values.yaml -n my-namespace
```

The command deploys Jenkins with its associated components (statefulset,
pod distruption budget, ingress) on the Kubernetes cluster in the
configuration specified by the values.yaml.

## Uninstalling

To delete/uninstall the chart with the release name `release-name`:

```code
helm uninstall release-name -n my-namespace
```

## Configuration

The following table lists the configurable Helm values that you can set in
the YAML file you use to configure Jenkins. If you do not include a parameter
in your YAML file, your configuration uses the default value.

<!-- BEGIN HELM VALUES TABLE -->
**Parameter**                    | **Description** | **Default Value**
---------------------------------|-----------------|-------------------
`common.containerRegistry`       | Name of the Container Registry to pull the images from | ``
`common.imagePullPolicy`         | Determines the policy for pulling images from the specified Container Registry | ``
`server.image`                   | The container image for running Jenkins pod(s) | ``
`server.config.hostname`         | The hostname to be used with Ingress | ``
`server.config.mountPath`        | The Jenkins data mount for PV storage | ``
`server.config.storageSize`      | The size of Jenkins PV storage to allocate | ``
`server.replicas`                | The number of Jenkins pod(s) to run | `2`
`server.network.port`            | The listen port for the Jenkins service | ``
`server.network.targetPort`      | The listen port for the Jenkins pod(s) | ``
`server.network.agentPort`       | The listen port for Jenkins agent service | ``
`server.network.agentTargetPort` | The listen port for Jenkins agent pod(s) | ``
`server.network.protocol`        | The protocol for the Jenkins pod(s) and service(s) | ``
`server.requests.cpu`            | The requested CPU scale for the running pod | ``
`server.requests.memory`         | The requested Memory size for the running pod | ``
`server.limits.cpu`              | The limit of CPU scale for the running pod | ``
`server.limits.memory`           | The limit of Memory size for the running pod | ``
`server.liveness.path`           | The endpoint for the Liveness probe | ``
`server.liveness.port`           | The port for the Liveness probe | ``
`server.liveness.probeIds`       | The initial delay in seconds for the Liveness probe | ``
`server.liveness.probePs`        | The period in seconds for the Liveness probe | ``
`server.liveness.probeTs`        | The timeout in seconds for the Liveness probe | ``
`server.liveness.probeFt`        | The failure threshold in seconds for the Liveness probe | ``
`server.readiness.path`          | The endpoint for the Readiness probe | ``
`server.readiness.port`          | The initial delay in seconds for the Readiness probe | ``
`server.readiness.probeIds`      | The initial delay in seconds for the Readiness probe | ``
`server.readiness.probePs`       | The period in seconds for the Readiness probe | ``
`server.readiness.probeTs`       | The timeout in seconds for the Liveness probe | ``
`server.readiness.probeFt`       | The failure threshold in seconds for the Liveness probe | ``
<!-- END HELM VALUES TABLE -->