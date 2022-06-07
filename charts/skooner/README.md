# skooner

Simple Kubernetes real-time dashboard and management.

![Version: 0.0.2](https://img.shields.io/badge/Version-0.0.2-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square) ![AppVersion: stable](https://img.shields.io/badge/AppVersion-stable-informational?style=flat-square)

## TL;DR;

```console
helm repo add christianknell https://charts.knell.it
helm repo update
helm install my-release christianknell/skooner
```

## Introduction

This chart bootstraps the Simple Kubernetes real-time dashboard and management tool called [Skooner](https://github.com/skooner-k8s/skooner) using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.19+

## Installing the Chart

To install the chart with the release name `my-release`:

```console
helm repo add christianknell https://charts.knell.it
helm repo update
helm install my-release christianknell/skooner
```

These commands deploy Skooner on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `my-release` deployment:

```console
helm uninstall my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key                                        | Type   | Default                         | Description |
| ------------------------------------------ | ------ | ------------------------------- | ----------- |
| affinity                                   | object | `{}`                            |             |
| autoscaling.enabled                        | bool   | `false`                         |             |
| autoscaling.maxReplicas                    | int    | `100`                           |             |
| autoscaling.minReplicas                    | int    | `1`                             |             |
| autoscaling.targetCPUUtilizationPercentage | int    | `80`                            |             |
| clusterRoleBinding.clusterRole             | string | `"edit"`                        |             |
| fullnameOverride                           | string | `""`                            |             |
| image.pullPolicy                           | string | `"Always"`                      |             |
| image.repository                           | string | `"ghcr.io/skooner-k8s/skooner"` |             |
| image.tag                                  | string | `""`                            |             |
| imagePullSecrets                           | list   | `[]`                            |             |
| ingress.annotations                        | object | `{}`                            |             |
| ingress.className                          | string | `""`                            |             |
| ingress.enabled                            | bool   | `false`                         |             |
| ingress.hosts[0].host                      | string | `"chart-example.local"`         |             |
| ingress.hosts[0].paths[0].path             | string | `"/"`                           |             |
| ingress.hosts[0].paths[0].pathType         | string | `"ImplementationSpecific"`      |             |
| ingress.tls                                | list   | `[]`                            |             |
| nameOverride                               | string | `""`                            |             |
| nodeSelector."kubernetes.io/os"            | string | `"linux"`                       |             |
| oidc.enabled                               | bool   | `false`                         |             |
| oidc.provider.oidcMetadata                 | string | `""`                            |             |
| oidc.provider.oidcScopes                   | string | `"openid email"`                |             |
| oidc.provider.oidcUrl                      | string | `""`                            |             |
| oidc.secret.clientId                       | string | `""`                            |             |
| oidc.secret.clientSecret                   | string | `""`                            |             |
| oidc.secret.name                           | string | `""`                            |             |
| oidc.secret.useExistingSecret              | bool   | `false`                         |             |
| podAnnotations                             | object | `{}`                            |             |
| podSecurityContext.fsGroup                 | int    | `1000`                          |             |
| replicaCount                               | int    | `1`                             |             |
| resources                                  | object | `{}`                            |             |
| securityContext.runAsNonRoot               | bool   | `true`                          |             |
| securityContext.runAsUser                  | int    | `1000`                          |             |
| service.port                               | int    | `80`                            |             |
| service.type                               | string | `"ClusterIP"`                   |             |
| serviceAccount.annotations                 | object | `{}`                            |             |
| serviceAccount.create                      | bool   | `true`                          |             |
| serviceAccount.name                        | string | `""`                            |             |
| tolerations                                | list   | `[]`                            |             |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install my-release -f values.yaml christianknell/skooner
```

---

Autogenerated from chart metadata using [helm-docs v1.10.0](https://github.com/norwoodj/helm-docs/releases/v1.10.0)
