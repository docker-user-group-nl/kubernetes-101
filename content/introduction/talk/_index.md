+++
title = "Introduction Talk"
date = 2020-02-28T16:53:43+03:00
weight = 5
layout = "slideshow"
pre = "<b>0.1 </b>"
+++

# What is Kubernetes?

- Kubernetes official definition here

----

# Containers (A quick recap)

----

# Pods

- quickly show some characteristics
- same network namespace
- mention init/sidecars

----

# Nodes

- Quick view of how they tie in

----

# The Networking Story

- A single non-NAT network
- Pod <-> Pod
- Pod <-> Node

---- 

# Tying it all together

- the master node


# The 10,000 ft. View

- Show Nodes/control-plane & pods
- Everything is a resource, K8s tries to converge to the desired state
- can be used as a reference picture
- alternatively to sum up the previous slides (if shown at the end)

----

# Resources!

- Pods, Services, Deployments, Ingress, and many more...

----

# Pod

Defines a single instance of a Pod to be executed on a cluster.

- example yaml of a pod (simplified)

----

# Deployment

Defines a single deployment (set of Pods)
Metadata about how to manage the set of Pods (restart policies, other)
- highlight the labelling

----

# Service

- Defines a route that load-balances across a deployment
- Finds the relevant deployment using the labels
- Note how the port-mapping works.
- (mention the three kinds of ports)?

----

# Labels 101

- in, not in
- is, is not
- can be used from kubectl: `-l`

----

# Questions?

- Q&A
- Dive straight into the first exercise
