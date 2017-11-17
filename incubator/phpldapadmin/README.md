# phpLDAPadmin Helm Chart

## Prerequisites Details
* Kubernetes 1.6+
* Running LDAP server (OpenLDAP or Apache DS, etc)

## Chart Details
This chart will do the following:

* Instantiate an instance of phpLDAPadmin web service

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release incubator/phpldapadmin
```

## Configuration

We use the docker images provided by https://github.com/osixia/docker-phpLDAPadmin. The docker image is highly configurable and well documented. Please consult to documentation for the docker image for more information. 

The following tables lists the configurable parameters of the phpldapadmin chart and their default values.

| Parameter                       | Description                           | Default                                                    |
| ------------------------------- | ----------------------------------    | ---------------------------------------------------------- |
| `phpldapadmin.replicas`         | How many replicas to schedule         | `1`                                                        |
| `phpldapadmin.image.name`       | Container image name                  | `osixia/phpldapadmin`                                      |
| `phpldapadmin.image.tag`        | Container image tag                   | `0.7.0`                                                    |
| `phpldapadmin.imagePullPolicy`  | Container pull policy                 | `IfNotPresent`                                             |
| `phpldapadmin.service.enabled`  | Enable k8s service definition         | `false`                                                    |
| `phpldapadmin.service.type`     | Service type                          | `ClusterIP`                                                |
| `phpldapadmin.httpInternalPort` | Internal port for HTTP                | `80`                                                       |
| `phpldapadmin.httpExternalPort` | Internal port for HTTP                | `80`                                                       |
| `phpldapadmin.sslInternalPort`  | Internal port for SSL                 | `443`                                                      |
| `phpldapadmin.sslExternalPort`  | Internal port for SSL                 | `443`                                                      |
| `phpldapadmin.env`              | List of key value pairs as env variables to be sent to the docker image. See https://github.com/osixia/docker-phpLDAPadmin for available ones and their usage | `PHPLDAPADMIN_HTTPS: "true"`  |
| `phpldapadmin.ldapHosts`        | PHPLDAPADMIN_LDAP_HOSTS env variable injected to the docker image. Point it to your LDAP service hostname or LDAP server. This is managed as a secret. | `ldapHosts: "modest-chinchilla-openldap-service.default.svc.cluster.local"`  |
| `phpldapadmin.customConfig`     | custom config file to override config.php | ``  |
| `phpldapadmin.resources`        | Container resource requests and limits in yaml |                                              `{}`  |

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`.

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
$ helm install --name my-release -f values.yaml incubator/phpldapadmin
```

> **Tip**: You can use the default [values.yaml](values.yaml)
