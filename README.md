# K8s-vagrant

Deploys a local Kubernetes cluster. Using a master node and 2 minions. Created for experimenting and playing around with a kubernetes cluster locally under Windows (or Linux).

## Features
* Master node and a worker node
* Taint is removed from master
* Helm installed
* Default storageclass is set

## Components
* Calico pod network
* Local path provisioner `https://github.com/rancher/local-path-provisioner`

## Required
* Virtualbox
* Vagrant

## Vagrant setup
* vagrant box, virtualbox provider: `https://app.vagrantup.com/ubuntu/boxes/bionic64`

## Getting started
* Clone git repo
* run `vagrant up`
* run `vagrant ssh k8s-master`
