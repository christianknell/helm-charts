# passbolt-ha

A Helm chart to deploy Passbolt with MySQL and ProxySQL for HA

![Version: 0.0.1](https://img.shields.io/badge/Version-0.0.1-informational?style=flat-square) ![Type: application](https://img.shields.io/badge/Type-application-informational?style=flat-square)

## TL;DR;

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install passbolt-ha christianknell/passbolt-ha
```

## Introduction

This chart bootstraps [Passbolt](https://github.com/passbolt), [MYSQL by Bitnami](https://github.com/bitnami/charts/tree/master/bitnami/mysql) and [ProxySQL](https://github.com/flachesis/proxysql/tree/master/charts/proxysql) using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.19+

## Installing the Chart

To install the chart with the release name `passbolt-ha`:

```console
helm repo add christianknell https://christianknell.github.io/helm-charts
helm repo update
helm install passbolt-ha christianknell/passbolt-ha
```

These commands deploy Skooner on the Kubernetes cluster in the default configuration. The [Values](#values) section lists the values that can be configured during installation.

> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall the `passbolt-ha` deployment:

```console
helm uninstall passbolt-ha
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Values

| Key                                         | Type   | Default                      | Description |
| ------------------------------------------- | ------ | ---------------------------- | ----------- |
| mysql.affinity                              | object | `{}`                         |             |
| mysql.architecture                          | string | `"replication"`              |             |
| mysql.auth.database                         | string | `"passbolt"`                 |             |
| mysql.auth.password                         | string | `"passbolt"`                 |             |
| mysql.auth.rootPassword                     | string | `"root"`                     |             |
| mysql.auth.username                         | string | `"passbolt"`                 |             |
| mysql.enabled                               | bool   | `true`                       |             |
| mysql.fullnameOverride                      | string | `"passbolt-mysql"`           |             |
| mysql.global.storageClass                   | string | `""`                         |             |
| mysql.image.pullPolicy                      | string | `"Always"`                   |             |
| mysql.metrics.enabled                       | bool   | `false`                      |             |
| mysql.metrics.image.pullPolicy              | string | `"Always"`                   |             |
| mysql.metrics.serviceMonitor.enabled        | bool   | `false`                      |             |
| mysql.metrics.serviceMonitor.labels         | object | `{}`                         |             |
| mysql.rbac.create                           | bool   | `true`                       |             |
| mysql.resources.limits.cpu                  | string | `"200m"`                     |             |
| mysql.resources.limits.memory               | string | `"1024Mi"`                   |             |
| mysql.resources.requests.cpu                | string | `"10m"`                      |             |
| mysql.resources.requests.memory             | string | `"256Mi"`                    |             |
| mysql.secondary.replicaCount                | int    | `2`                          |             |
| mysql.volumePermissions.enabled             | bool   | `true`                       |             |
| mysql.volumePermissions.image.pullPolicy    | string | `"Always"`                   |             |
| passbolt.db.host                            | string | `"passbolt-proxysql"`        |             |
| passbolt.db.name                            | string | `"passbolt"`                 |             |
| passbolt.db.username                        | string | `"passbolt"`                 |             |
| passbolt.fullnameOverride                   | string | `"passbolt"`                 |             |
| passbolt.image.pullPolicy                   | string | `"Always"`                   |             |
| passbolt.ingress.annotations                | object | `{}`                         |             |
| passbolt.ingress.className                  | string | `""`                         |             |
| passbolt.ingress.enabled                    | bool   | `false`                      |             |
| passbolt.ingress.hosts[0].host              | string | `"chart-example.local"`      |             |
| passbolt.ingress.hosts[0].paths[0].path     | string | `"/"`                        |             |
| passbolt.ingress.hosts[0].paths[0].pathType | string | `"ImplementationSpecific"`   |             |
| passbolt.ingress.tls                        | list   | `[]`                         |             |
| passbolt.mariadb.enabled                    | bool   | `false`                      |             |
| passbolt.passbolt.baseUrl                   | string | `""`                         |             |
| passbolt.persistence.accessMode             | string | `"ReadWriteOnce"`            |             |
| passbolt.persistence.enabled                | bool   | `true`                       |             |
| passbolt.persistence.size                   | string | `"512Mi"`                    |             |
| passbolt.resources.limits.cpu               | string | `"100m"`                     |             |
| passbolt.resources.limits.memory            | string | `"512Mi"`                    |             |
| passbolt.resources.requests.cpu             | string | `"50m"`                      |             |
| passbolt.resources.requests.memory          | string | `"256Mi"`                    |             |
| proxysql.affinity                           | object | `{}`                         |             |
| proxysql.enabled                            | bool   | `true`                       |             |
| proxysql.fullnameOverride                   | string | `"passbolt-proxysql"`        |             |
| proxysql.image.pullPolicy                   | string | `"Always"`                   |             |
| proxysql.proxysql.admin.password            | string | `"admin"`                    |             |
| proxysql.proxysql.admin.user                | string | `"admin"`                    |             |
| proxysql.proxysql.mysql.servers[0].hostname | string | `"passbolt-mysql-primary"`   |             |
| proxysql.proxysql.mysql.servers[0].isWriter | bool   | `true`                       |             |
| proxysql.proxysql.mysql.servers[0].port     | int    | `3306`                       |             |
| proxysql.proxysql.mysql.servers[1].hostname | string | `"passbolt-mysql-secondary"` |             |
| proxysql.proxysql.mysql.servers[1].isWriter | bool   | `false`                      |             |
| proxysql.proxysql.mysql.servers[1].port     | int    | `3306`                       |             |
| proxysql.proxysql.mysql.users[0].password   | string | `"root"`                     |             |
| proxysql.proxysql.mysql.users[0].username   | string | `"root"`                     |             |
| proxysql.proxysql.mysql.users[1].password   | string | `"passbolt"`                 |             |
| proxysql.proxysql.mysql.users[1].username   | string | `"passbolt"`                 |             |
| proxysql.proxysql.mysql.version             | string | `"8.0.29"`                   |             |
| proxysql.proxysql.web.password              | string | `"admin"`                    |             |
| proxysql.proxysql.web.user                  | string | `"admin"`                    |             |
| proxysql.replicaCount                       | int    | `3`                          |             |
| proxysql.resources.limits.cpu               | string | `"200m"`                     |             |
| proxysql.resources.limits.memory            | string | `"512Mi"`                    |             |
| proxysql.resources.requests.cpu             | string | `"100m"`                     |             |
| proxysql.resources.requests.memory          | string | `"128Mi"`                    |             |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```console
helm install passbolt-ha -f values.yaml christianknell/passbolt-ha
```

### Setting up the database connection

By default the passwords used to install MySQL are very weak. You should therefore create a Secret like the following:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: passbolt-mysql
stringData:
  mysql-password: 36X79oYHQBD5C8aGT1Gqzm2jLK4BWPC0
  mysql-replication-password: UDWAZ2MHISu75YW34S08OB1POTvKoE69
  mysql-root-password: 24D1FOHKvDLwt5MA087QUVO36IjY9rRY
  username: passbolt
type: Opaque
```

Then update your values like this:

```yaml
mysql:
  auth:
    existingSecret: passbolt-mysql
proxysql:
  proxysql:
    mysql:
      users:
        - username: root
          password: $NEW_PASSWORD
        - username: passbolt
          password: $NEW_PASSWORD
```

---

Autogenerated from chart metadata using [helm-docs v1.10.0](https://github.com/norwoodj/helm-docs/releases/v1.10.0)
