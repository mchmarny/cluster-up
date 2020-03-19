# Cluster Up

Series of scripts I use to reliably deploy, configure, and test GKE cluster based demos

## Pre-requirements

If you don't have one already, start by creating new project and configuring [Google Cloud SDK](https://cloud.google.com/sdk/docs/).

## Cluster

### Config

First edit the [config](./config) file. It contains all the variables for this install. Once you edit that file you should not have to edit any other scripts in this install.

### Create GKE cluster with Cloud Run add-on

Setup a new GKE cluster with autoscaling (min 1 node) and 2nd GPU node pool

```shell
./cluster-up
```

## GPU

To add an additional single node GPU node pool (`gpu-node-pool`) with `nvidia-tesla-v100` accelerator (and the appropriate drivers) to the above created cluster, run:

```shell
./gpu-pool
```

> Edit the config section in [gpu-pool](./gpu-pool) file to increase the pool size or specify different type of accelerator

## Cloud Run

### Config

To add Cloud Run add-on to your cluster first edit the [cr-add](./cr-add) script and define the custom domain you will be using and the SSL certificates for that domain.

```shell
CUSTOM_DOMAIN="cloudylabs.dev"
CA_PATH="${TLS_CERT_DIR}/ca.pem"
PK_PATH="${TLS_CERT_DIR}/pk.pem"
```

> If you do not already have TLS certificates you can use [Let's Encrypt](https://letsencrypt.org/docs/client-options/) to generate them

### Install

To add the add-on and configure the Knative Serving components (static IP, custom domain, TLS certificates, etc) execute:

```shell
./cr-add
```

> At the conclusion of this script you will be instructed to configure your DNS server. Make sure you set up necessary A record before moving on to the Test Installation section below.

### Test

You can test your installation using the provided [cr-test](./cr-test) script which will deploy to Cloud Run a test application ([maxprime](https://github.com/mchmarny/maxprime)) and validate that your custom domain, TLS certificates and DNS are configured correctly.

```shell
./cr-test
```



## Disclaimer

This is my personal project and it does not represent my employer. I take no responsibility for issues caused by this code. I do my best to ensure that everything works, but if something goes wrong, my apologies is all you will get.

## License
This software is released under the [Apache v2 License](../LICENSE)