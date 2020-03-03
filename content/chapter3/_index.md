+++
title = "Kubernetes Objects"
date = 2020-03-02T14:08:28+03:00
weight = 8
chapter = true
pre = "<b>3. </b>"
+++

<!-- Yaml and how K8s API works. Describe how we interact with k8s via the API , describe the k8s object expected fields and format. -->
### Chapter 3

# Kubernetes Objects

Kubernetes is made up of a group of objects of different kinds.
Everything in Kubernetes is an object, from a Persistent volume to a Pod.
We can have a look at these objects through the Kubernetes API & even
submit our own instances to the API.
Traditionally these object files are stored in YAML files, but it is
possible to also declare objects in JSON files.

Below is a sample of a Kubernetes object defined in YAML

```
apiVersion: extensions/v1beta1
kind: Deployment
metadata:
  name: my-service
  labels:
    app: my-service
spec:
  template:
    spec:
      containers:
      - name: my-service
        image: ghost
        ports:
        - name: http
          containerPort: 5000
```

This is a full definition of a _Deployment_ type.  There are a number
of elements to this definition, let's go through them and explain in
some more detail with reference to the above example.

##### apiVersion
```
apiVersion: extensions/v1beta1
```

This defines the API version that this definition is
using, there are normally several different API's available for use
for the core resources as they are constantly improved & refined.

We are using the extensions API-set, this determines the
legal format of the spec.

##### kind
```
kind: Deployment
```

This defines the _kind_ (or type) of resource that we are
specifying. There are many different kinds of resources in Kubernetes,
both built into the core & 3rd party to enhance and enrich your
cluster.

The _Deployment_ kind lets us know that we are dealing with a
Deployment type, a core type defined within Kubernetes. We know from
this that the specification will define a Pod specification internally
& additionally some Deployment-specific configuration relating to the
orchestration of the Deployment.

##### metadata
```
metadata:
  name: my-service
```

This allows for defining any metadata about the resource. This
includes things such as the name of the resource (in this case the
name being _my-service_), attaching labels (for management of the
resources), attaching annotations (which can be used for auditing &
tuning/configuring meta-services).

All resources _must_ define a name, This is the only key that is
mandatory across all resources. The name is what we saw in the
previous section when we were looking through what resources were
already present on the cluster.

##### spec
```
spec:
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 25%
      maxUnavailable: 0
  template:
    spec:
      containers:
      - name: my-service
        image: ghost
        ports:
        - name: http
          containerPort: 5000
```

This is the meat of the definition file. It is where we
specify the specification of the kind we would like to deploy to the
cluster. In other words it allows us to configure this instance of
this resource.

This is where we define how we would like to configure our Deployment.
In this case we have the following two keys:

**strategy** which defines how we will perform upgrades of our
deployment deployment (such as deploying new versions, updating
configurations or changing any settings in the Deployment object)

**template** is where we define the pod configuration that we would
like to manage with this Deployment. The Pod spec is simplified for
clarity, there are a wide number of settings that can be configured at
the Pod level which have been left out for clarity. Generally the
default settings are good for getting up and running (set if the
setting is omitted in the configuration).

The relevant portion of the YAML file for the Pod configuration is as
such:

```
containers:
- name: my-service
  image: ghost
  ports:
  - name: http
    containerPort: 5000
```

This defines a single container called _my-service_, running the ghost blog
image & exposing port 5000 under the name _http_.


## Exercises

Let's put what we have read into practice. In the previous exercise we
started up a Deployment using the kubectl command. Let's now migrate
this into a YAML file so we can reuse it & make configuration changes
easily.


First, let's clean up the Deployment from the last exercise (we are
going to leave the Ingress controller & Service so that we can still
access the Pod externally).

```
kubectl delete deployment nginx-run
```

**Note:** _please add in the following label `run: nginx-run` such that
we can reuse the service and ingress setup in the previous section._

Using the example above, change it into something that captures what
we created in the previous chapter.

You can apply the file you have created using the following command:

```
kubectl apply -f nginx-run.yaml
```
