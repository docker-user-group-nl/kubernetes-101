+++
title = "More about Resources"
date = 2020-02-28T17:24:24+03:00
weight = 7
chapter = true
pre = "<b>2. </b>"
+++

### Chapter 2 - More about Resources

By now you should be able to connect to your Kubernetes cluster. Let's
now dig a bit more into what each of the different resources are in
Kubernetes & how we can start using them.


# Our first application

There are a number of different ways to get an application running on
our cluster, the easiest way is by using the `kubectl run` command.

Let's get a simple website up and running!

`TODO instructions to install an nginx/other pod using kubectl run`


Great, now let's have a look and verify that it's running as we expect
it to be.

`kubectl get pods`

We should see a pod called `nginx-run`, note that it may be in a
_PENDING_ or _ERROR_ state.

We can have a closer look at why this is the case by seeing what
events are associated with the pod.

`kubectl describe pod nginx-run`


Near the end of the output there is a line called _Events__.  Below we
can have a look at what happened, there are a number of events which
should show up:

```
TODO
show some sample events that may show up
- image pulling
- image not found
- others?...
```

Note that if you are getting `ErrImagePullBackoff` error, it is likely
there is a typo in the run command you typed in above.

# Accessing the application

Now that we have the Pod up and running, let's expose it so we
can access it.

By default a Pod is not accessible from outside the cluster so we need
to explicitly add a route to the pod.

```
TODO add instructions on how to use 'kubectl expose'
```

Now we can access our Pod! Let's figure out the information we need.

Firstly, it's being hosted on one of our Kubernetes nodes, so let's grab the IP address:

`kubectl get nodes -o wide`

We can use any of the IP's under the ExternalIP list.
<!-- TODO, see if this is true for minikube -->

Secondly, we need to see what port Kubernetes has exposed our nginx server on:

`kubctl get services`

**TODO**: add clear instructions about which number to use here.

Now we can put these together and open it in our webbrowser.
<!-- TODO, see if it's possible to route to localhost so we can emded links directly in the tutorial -->

Congratulations! We now have a Pod running in the cluster which we
have a exposed outside of the cluster.

Let's take a small detour to see how we can view our Pod's logs, this will be useful in future exercises.

# Pod Logs

to view the logs of our Pod, we can use another special kubectl subcommand.

`kubectl logs nginx-run`
