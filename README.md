# Elastic-stack Helm Chart

This chart installs an elasticsearch 6.6.1 cluster with elastiflow 3.4.1 on logstash 6.1.3 and kibana by default.
It also optionally installs filebeat, nginx-ldapauth-proxy and elasticsearch-curator.

## Prerequisites Details

* Kubernetes 1.8+
* PV dynamic provisioning support on the underlying infrastructure

## Chart Details
This chart will do the following:

* Implemented a dynamically scalable elasticsearch cluster using Kubernetes StatefulSets/Deployments
* Multi-role deployment: master, client (coordinating) and data nodes
* Statefulset Supports scaling down without degrading the cluster

## Installing the Chart

To install the chart with the release name `elastiflow`:

```bash
$ helm install --name elastiflow path/to/elastic-stack-helm
```

## Deleting the Charts

Delete the Helm deployment as normal

```
$ helm delete --purge elastiflow
```

Deletion of the StatefulSet doesn't cascade to deleting associated PVCs. To delete them:

```
$ kubectl delete pvc -l release=elastiflow,component=data
```

## Configuration

Each requirement is configured with the options provided by that Chart.
Please consult the relevant charts for their configuration options.
