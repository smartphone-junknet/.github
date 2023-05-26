# Reuse old smartphones, self-host your services

The aim of this organization is to create a consistent platform that enables the owner of a supported smartphone to convert it into a Nomad cluster node, and use it to schedule container workloads through Podman.

In the end, a user with a cluster of such devices will be able to run on premises (at home) their FLOSS software instead of relying on proprietary cloud services.

## PostmarketOS

The idea for this project came from using PostmarketOS on an old Samsung Galaxy S III Mini, which happens to be supported by mainline Linux! This means that the kernel will "just work" ™ on it. However, this also means that many other smartphone models are less supported.

You can check out the PostmarketOS website [here](https://wiki.postmarketos.org/wiki/Main_Page), and the device support table [here](https://wiki.postmarketos.org/wiki/Devices).

**NOTE**: since on the Postmarket's wiki the device are referenced by "code name" and not model name, [here](https://storage.googleapis.com/play_public/supported_devices.html) it is a link to the official table with the association between the two strings.

## Nomad

The obvious choice for an orchestrator was something lightweight and as self-contained as possible. Since docker-compose/podman-compose do not support clustering of nodes nor any security enforcement, the second candidate was definitely [Hashicorp Nomad](https://developer.hashicorp.com/nomad/intro).

It can run in a cluster of 5 servers with 4 jobs per node allocating only 100MB of RAM on each server; moreover, it supports traffic encryption, ACLs, service discovery, and the whole think is literally a single Golang binary of almost 100MB.

## Podman

Podman was preferred over Docker for its out of the box rootless operation and its integration with Nomad.
