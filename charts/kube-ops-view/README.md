# kube-ops-view

A Helm chart for bootstrapping kube-ops-view.

![Version: 1.1.2](https://img.shields.io/badge/Version-1.1.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: 20.4.0](https://img.shields.io/badge/AppVersion-20.4.0-informational?style=flat-square)

## TL;DR;

```console
helm repo add christianknell https://charts.knell.it
helm repo update
helm install my-release christianknell/kube-ops-view
```

## Introduction

Kubernetes Operational View - read-only system dashboard for multiple K8s clusters

This chart bootstraps the [Kubernetes Operational View](https://codeberg.org/hjacobs/kube-ops-view) on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.19+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm repo add christianknell https://charts.knell.it
helm repo update
helm install my-release christianknell/kube-ops-view
```

These commands deploy kube-ops-view on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `my-release` deployment:

```console
helm uninstall my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key                                | Type   | Default                                                                                                | Description                                                                                                            |
| ---------------------------------- | ------ | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------- |
| affinity                           | object | `{}`                                                                                                   | Affinity settings for pod assignment                                                                                   |
| args                               | list   | `[]`                                                                                                   |                                                                                                                        |
| fullnameOverride                   | string | `""`                                                                                                   | String to fully override `"kube-ops-view.fullname"`                                                                    |
| image.pullPolicy                   | string | `"Always"`                                                                                             | image pull policy                                                                                                      |
| image.repository                   | string | `"hjacobs/kube-ops-view"`                                                                              | image repository                                                                                                       |
| image.tag                          | string | `""`                                                                                                   |                                                                                                                        |
| imagePullSecrets                   | list   | `[]`                                                                                                   | If defined, uses a Secret to pull an image from a private Docker registry or repository.                               |
| ingress.annotations                | object | `{}`                                                                                                   |                                                                                                                        |
| ingress.className                  | string | `""`                                                                                                   |                                                                                                                        |
| ingress.enabled                    | bool   | `false`                                                                                                |                                                                                                                        |
| ingress.hosts[0].host              | string | `"chart-example.local"`                                                                                |                                                                                                                        |
| ingress.hosts[0].paths[0].path     | string | `"/"`                                                                                                  |                                                                                                                        |
| ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"`                                                                             |                                                                                                                        |
| ingress.tls                        | list   | `[]`                                                                                                   |                                                                                                                        |
| nameOverride                       | string | `""`                                                                                                   | Provide a name in place of `kube-ops-view`                                                                             |
| nodeSelector                       | object | `{}`                                                                                                   | Node labels for pod assignment                                                                                         |
| podAnnotations                     | object | `{}`                                                                                                   | Annotations to be added to exporter pods                                                                               |
| redis                              | object | `{"architecture":"standalone","auth":{"enabled":false},"enabled":false}`                               | Values for including the subchart Redis™ from Bitnami                                                                  |
| redis.architecture                 | string | `"standalone"`                                                                                         | Redis™ architecture. Allowed values: standalone or replication                                                         |
| redis.auth.enabled                 | bool   | `false`                                                                                                | Disable password authentication as the kube-ops-view container has no support for password authentication              |
| redis.enabled                      | bool   | `false`                                                                                                | enable Redis™ subchart from Bitnami                                                                                    |
| replicaCount                       | int    | `1`                                                                                                    | Number of replicas                                                                                                     |
| resources                          | object | `{}`                                                                                                   | Resource limits and requests for the controller pods.                                                                  |
| securityContext                    | object | `{"capabilities":{"drop":["ALL"]},"readOnlyRootFilesystem":true,"runAsNonRoot":true,"runAsUser":1000}` | container-level security context                                                                                       |
| service.port                       | int    | `80`                                                                                                   | Kubernetes port where service is exposed                                                                               |
| service.type                       | string | `"ClusterIP"`                                                                                          | Kubernetes service type                                                                                                |
| serviceAccount.annotations         | object | `{}`                                                                                                   | Annotations to add to the service account                                                                              |
| serviceAccount.create              | bool   | `true`                                                                                                 | Specifies whether a service account should be created                                                                  |
| serviceAccount.name                | string | `""`                                                                                                   | The name of the service account to use. If not set and create is true, a name is generated using the fullname template |
| tolerations                        | list   | `[]`                                                                                                   | Toleration labels for pod assignment                                                                                   |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml christianknell/kube-ops-view
```

---

Autogenerated from chart metadata using [helm-docs v1.10.0](https://github.com/norwoodj/helm-docs/releases/v1.10.0)
