## Build image with signed nvidia drivers for RHEL 10

1. Update the arguments in the `argfile.conf` accordingly
2. Run command below to build the nvidia-driver image

```
podman build . --build-arg-file=./argfile.conf -t rhel10-nvidia-drivers:580.82.07
```
