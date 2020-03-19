# GPU

To add an additional single node GPU node pool (`gpu-node-pool`) with `nvidia-tesla-v100` accelerator (and the appropriate drivers) to the above created cluster, run:

```shell
./gpu-pool
```

> Edit the config section in [gpu-pool](./gpu-pool) file to increase the pool size or specify different type of accelerator



## Disclaimer

This is my personal project and it does not represent my employer. I take no responsibility for issues caused by this code. I do my best to ensure that everything works, but if something goes wrong, my apologies is all you will get.

## License
This software is released under the [Apache v2 License](../LICENSE)