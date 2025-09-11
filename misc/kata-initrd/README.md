## Create kata-initrds image

1. Download/generate the kata-containers rpm and copy it to the same directory as the `Containerfile`
2. Update the arguments in the `argfile.conf` accordingly
3. Run command below to build the initrds image
```
podman build . --build-arg-file=./argfile.conf -t kata-initrds:1.0
```
If the `-v $PWD:/host` parameter is added to the command line above, the files `kata-initrds.tar.gz` and `kata-configs.tar.gz`
will also be copied to $PWD.

## Debugging the kata-osbuilder.sh script

There are multiple ways, one of them is to stop the image build at the stage `initrds-builder-setup`. With that you should
have an image where `kata-osbuilder.sh` was not run yet and you could just run the image to run the script yourself.

```
podman build . --build-arg-file=./argfile.conf -t initrds-builder-setup:1.0 --target initrds-builder-setup
podman run -ti -v $PWD:/host localhost/initrds-builder-setup:1.0 /bin/bash
# then run /usr/libexec/kata-containers/osbuilder/kata-osbuilder.sh as desired
```
