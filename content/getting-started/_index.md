+++
title = "Getting Started"
date = 2020-02-28T17:24:24+03:00
weight = 6
chapter = true
pre = "<b>1. </b>"
+++

### Chapter 1
Getting Setup

----

#### Let's get started

- Make sure you have a K8s environment
  - Docker for Desktop
  - Minikube
- We can connect to the cluster
  - `kubectl version`
  
  
----

#### First Steps

- Get the nodes
  - `kubectl get nodes`
- `kubectl get pods --all-namespaces`
  - We can see what services K8s already started for us.
  
----

#### Kubernetes Verbs

- get (retrieve the state of a resource)
- create (create a new resource)
- delete (delete a resource)
- edit (edit an existing resource) # caution
- and more... `kubectl help`

----

#### On to the course!

```
docker run -p 8000:8000 .../...
open http://localhost:8000/
```
