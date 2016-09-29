Docker in Debian
================

*Debian doesn't have `aufs` like Ubuntu so by default, Docker will use
`devicemapper` for its `storage-driver`*

Since Debian switches to use `systemd` for some time, the config file
at `/etc/default/docker` is not used by Docker startup script. We need
to edit the `systemd` configuration file to use this.

```
# service docker stop
# vim /lib/systemd/system/docker.service
```

###1. Edit these 2 lines
```
ExecStart=/usr/bin/dockerd -H fd:// $DOCKER_OPTS
EnvironmentFile=-/etc/default/docker
```
###2. Set `DOCKER_OPTS` to use `overlay2` engine instead of `overlay`
```
# vim /etc/default/docker
DOCKER_OPTS="--storage-driver=overlay2"
```

###3. You can test it manually by
```
# DOCKER_OPTS="--storage-driver=overlay2" service docker start
```

###4. Remove the old image files
```
# rm -fr /var/lib/docker/{devicemapper,aufs,overlay}
```
If you want to save the current docker images and load them later,
you can use my [`docker_save.sh`][0] script to save and load them.
(Warning: I use `pxz` so it might slow on your machine, switch to use
`pigz` if you prefer `gz` format).

###5. Restart your docker daemon
```
# service docker start
```

###6. Check if `overlay2` is used as a storage driver now.
```
$ docker info | grep overlay2
Storage Driver: overlay2
```


#### References:
  * https://docs.docker.com/engine/userguide/storagedriver/selectadriver/
  * https://docs.docker.com/engine/userguide/storagedriver/overlayfs-driver/
  * https://docs.docker.com/engine/admin/systemd/

[0]: https://github.com/neofob/tscripts/blob/master/docker/docker_save.sh
