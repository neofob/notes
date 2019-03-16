Ubuntu 18.04
============
*A brief random notes on GlusterFS*

Server
======
```
# add-apt-repository ppa:gluster/glusterfs-5
# apt-get update && apt-get install -yq glusterfs-server
```

Client
======
```
# add-apt-repository ppa:gluster/glusterfs-5
# apt-get update && apt-get install -yq glusterfs-client
# mount -t glusterfs gluster0:/volname /local/mount/point
```


Open Ports
==========
*This is after `3.4` version*
* `24007`: GlusterFS Daemon
* `24008`: Management
* `49152+`: One per brick
* `111`: Portmapper

DNS
===
The easiest way to probe the peer node is to use IP address. If you use hostname,
make sure it is resolvable on all nodes, aka using good old `/etc/hosts` or
updating your local DNS.

Mount Point
===========
Gluster does not like:
  * root file system (understandable)
  * mount point (to avoid direct writing data to that directory); ex: `/dev/sda1` on `/data/brick0`; create a subdir
under the mount point for `/dev/sda1` instead.

You could add `force` at the end of `volume create` commandline. Forced adoption has its own consequence though (Silicon
Valley show).

Brick Naming Convention
=======================
*This is not set in stone, but we can try to have the best brick naming convention possible.*
```
# or, some nice Ansible stuff like this
GHOST="gserver0 gserver1 gserver2 gserver3"
for h in ${GHOST}; do
  ssh ${h} sudo mkdir -p /data/glusterfs/volname/brick0
done
```
Preferably, your paritions are mounted one or many directories above the above mentioned `brick0` directory.

__scribbled by:__ *tuan t. pham*
