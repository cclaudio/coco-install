## Create kata osbuilder images from a given kata-containers rpm package

1. Download/generate the kata-containers rpm and copy it to the same directory as the `Containerfile`
2. Update the arguments in the `argfile.conf` accordingly
3. Generate the `kata-osbuilder-images.tar.gz`
```
podman build . -v $PWD:/host --build-arg-file=./argfile.conf -t kata-initrd:1.0
```
