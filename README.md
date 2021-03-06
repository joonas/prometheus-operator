# Prometheus Operator

**Project status: *alpha*** Not all planned features are completed. The API, spec, status 
and other user facing objects are subject to change. We do not support backward-compability 
for the alpha releases.

The Prometheus Operator for Kubernetes provides easy monitoring definitions for Kubernetes
services and deployment and management of Prometheus instances.

Once installed the Prometheus Operator provides the following features:

* **Create/Destroy**: Easily launch a Prometheus instance for your Kubernetes namespace,
  a specific application or team easily using the Operator.

* **Simple Configuration**: Configure the fundamentals of Prometheus like versions, persistence, 
  retention policies, and replicas from a native Kubernetes resource.

* **Target Services via Labels**: Automatically generate monitoring target configurations based
  on familiar Kubernetes label queries; no need to learn a Prometheus specific configuration language.

For an introduction to the Prometheus Operator, see the initial [blog
post](https://coreos.com/blog/the-prometheus-operator.html).

See [kube-prometheus](https://github.com/coreos/kube-prometheus) for a
collection of resources that can be used to start monitoring Kubernetes
and applications running on top of it within minutes.


## Third party resources

The Operator acts on the following third party resources (TPRs):

* **[`Prometheus`](./Documentation/prometheus.md)**, which defines a desired Prometheus deployment.
  The Operator ensures at all times that a deployment matching the resource definition is running.

* **[`ServiceMonitor`](./Documentation/service-monitor.md)**, which declaratively specifies how groups
  of services should be monitored. The Operator automatically generates Prometheus scrape configuration
  based on the definition.

* **[`Alertmanager`](./Documentation/alertmanager.md)**, which defines a desired Alertmanager deployment.
  The Operator ensures at all times that a deployment matching the resource definition is running.


## Installation

Install the Operator inside a cluster by running the following command:

```
kubectl apply -f deployment.yaml
```

To run the Operator outside of a cluster:

```
make
hack/run-external.sh <kubectl cluster name>
```

**The Prometheus Operator collects anonymous usage statistics to help us learning how the software is being used and how we can improve it. To disable collection, run the Operator with the flag `-analytics=false`**
