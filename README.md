# Cloud Run Up

Series of scripts to reliably deploy and configure Cloud Run on GKE

> I'm toying with the idea of wrapping this into a simple CLI that would walk you through the entire process. Let me know if this sounds interesting and what areas the individual scripts below do not cover.

## Setup

First edit the [config](./config) file. It contains all the variables for this install. Once you edit that file you should not have to edit any other scripts in this install.

The only two variables you really have to edit are:

```shell
CLUSTER_PROJECT="cloudylabs" # GCP project ID
CUSTOM_DOMAIN="cloudylabs.dev"
```

> If you do not already have TLS certificates you can use [Let's Encrypt](https://letsencrypt.org/docs/client-options/) to generate them

## Create GKE cluster with Cloud Run add-on

Setup a new GKE cluster with autoscaling (min 1 node) and 2nd GPU node pool

```shell
./cluster-up
```

## Configure Cloud Run

Configure Knative Serving components (static IP, custom domain, TLS certificates, etc)

```shell
./cr-config
```

> At the conclusion of this script you will be instructed to configure your DNS server. Make sure you set up necessary A record before moving on to the Test Installation section below.

## Test Installation

You can test your installation using the provided [cr-test](./cr-test) script which will deploy to Cloud Run a test application ([maxprime](https://github.com/mchmarny/maxprime)) and validate that your custom domain, TLS certificates and DNS are configured correctly.

```shell
./cr-test
```

## Disclaimer

This is my personal project and it does not represent my employer. I take no responsibility for issues caused by this code. I do my best to ensure that everything works, but if something goes wrong, my apologies is all you will get.

## License
This software is released under the [Apache v2 License](../LICENSE)