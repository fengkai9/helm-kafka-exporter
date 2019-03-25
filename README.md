# Kafka Exporter

Prometheus exporter for various metrics about Kafka, written in Go.

Learn more: https://github.com/danielqsj/kafka_exporter

## TL;DR;

```bash
$ helm install stable/kafka-exporter
```

## Introduction

This chart creates an Kafka-Exporter deployment on a [Kubernetes](http://kubernetes.io)
cluster using the [Helm](https://helm.sh) package manager.

## Prerequisites

- Kubernetes 1.8+ with Beta APIs enabled

## Installing the Chart

To install the chart with the release name `my-release`:

```bash
$ helm install --name my-release stable/kafka-exporter
```

The command deploys Kafka-Exporter on the Kubernetes cluster using the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation.

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```bash
$ helm delete --purge my-release
```
The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following table lists the configurable parameters of the Kafka-Exporter chart and their default values.

Parameter | Description | Default
--- | --- | ---
`replicaCount` | desired number of pods | `1`
`restartPolicy` | container restart policy | `Always`
`image.repository` | container image repository | `danielqsj/kafka-exporter`
`image.tag` | container image tag | `v1.2.0`
`image.pullPolicy` | container image pull policy | `IfNotPresent`
`resources` | resource requests & limits | `{}`
`nodeSelector` | Node labels for pod assignment | `{}`
`podAnnotations` | Pod annotations | `{}` |
`service.type` | type of service to create | `ClusterIP`
`service.httpPort` | port for the http service | `9308`
`service.annotations` | annotations on the http service | `{}`
`hostAliases` | list of host name | `[localhost]`
`kafka.brokers` | list of the address of the kafka brokers to connect to | `[localhost:9092]`
`kafka.version` | kafka brokers version | `1.0.0`
`web.path` | path under which to expose metrics | `/metrics`
`serviceMonitor.enabled` | If true, a ServiceMonitor CRD is created for a prometheus operator | `false`
`serviceMonitor.interval` | Interval at which metrics should be scraped | `30s` 
`serviceMonitor.namespace` | The namespace where the Prometheus Operator is deployed | `` 
`serviceMonitor.labels` | Labels for prometheus operator | `{}`

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```bash
$ helm install --name my-release \
    --set key_1=value_1,key_2=value_2 \
    stable/kafka-exporter
```

Alternatively, a YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

```bash
# example for staging
$ helm install --name my-release -f values.yaml stable/kafka-exporter
```

> **Tip**: You can use the default [values.yaml](values.yaml)
