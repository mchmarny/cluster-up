# Cluster Up

Series of scripts I use to reliably deploy, configure, and test GKE cluster based demos

## Pre-requirements

If you don't have one already, start by creating new project and configuring [Google Cloud SDK](https://cloud.google.com/sdk/docs/).

## Config

First edit the [config](./config) file. It contains all the variables for this install. Once you edit that file you should not have to edit any other scripts in this install.

## Create GKE cluster

Setup a new GKE cluster with autoscaling (min 1 node) and 2nd GPU node pool

```shell
./cluster-up
```

## Next

* [GPU node pool](./gpu/README.md)
* [Cloud Run](./cloud-run/README.md)
* Istio
* Tekton
* Application Manager

## Disclaimer

This is my personal project and it does not represent my employer. I take no responsibility for issues caused by this code. I do my best to ensure that everything works, but if something goes wrong, my apologies is all you will get.

## License
This software is released under the [Apache v2 License](../LICENSE)