# test_travis_minikube

[![Build Status](https://travis-ci.org/aroundthecode/test_travis_minikube.svg?branch=master)](https://travis-ci.org/aroundthecode/test_travis_minikube)

This is a test repo to integrate [Travis-Ci](https://travis-ci.org) build using [Minikube](https://kubernetes.io/docs/setup/minikube/) to create an integration environment.

Original idea is described by [LilliCosic](http://twitter.com/LiliCosic) on [this](https://blog.travis-ci.com/2017-10-26-running-kubernetes-on-travis-ci-with-minikube) travis Blog post, but instruction are quite old (she uses Kubernetes 1.9.0) and many thins have changed meanwhile.

Lilli's instruction are more ora less valid up to Minikube version 0.28.0 where you can use **localkube bootstrapper** in conjunction with **none driver** to bring up everything

Sadly localkube bootstrap was removed in [minikbe v0.29.0](https://github.com/kubernetes/minikube/blob/v0.29.0/CHANGELOG.md) in favor to kubeadm.

Kubeadm on the other hand requires a systemd-bases OS to work properly, BUT default Travis build images still [rely on Ubuntu Trusty 14.04](https://docs.travis-ci.com/user/reference/overview/).

With such configration (e.g. minikube v0.29 and Trusty image) I was able to run kubernetes on Minikube up to v.1.10.0, you can find such configuration on [tag kubernetes_1.10](https://github.com/aroundthecode/test_travis_minikube/tree/kubernetes_1.10) of this project

Keep an eye on [this thread](https://github.com/kubernetes/minikube/issues/2704) to get details on all adjustments which occured on this stream.

Fortunatly on early November 2018 Travis [officially released](https://blog.travis-ci.com/2018-11-08-xenial-release) Xenial build imaged which can be used to overcome localkube limitations. 

Using [Xenail capabilities](https://docs.travis-ci.com/user/reference/xenial/) is therefore possible to run the latest (0.33 at the time of writing) minikube version and therefore upgrade your test environment to lates kubernetes releases.

You can find such code on current master branch.

Hope this can come in handy!
