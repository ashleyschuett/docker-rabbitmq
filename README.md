docker-rabbitmq
==============

##About

###Description
Docker image designed to run a rabbitmq cluster on ContainerShip

###Author
ContainerShip Developers - developers@containership.io

##Usage
This image is designed to run rabbitmq on a ContainerShip cluster. Running this image elsewhere is not recommended as the container may be unable to start.

###Configuration
This image will run as-is, with no additional environment variables set. For clustering to work properly, start the application in host networking mode. There are various optionally configurable environment variables:

* `DEFAULT_USER` - Default rabbitmq user (defaults to "guest")
* `DEFAULT_PASSWORD` - Default rabbitmq password (defaults to "guest")
* `ERLANG_COOKIE` - Magic cookie value

### Recommendations
* On your ContainerShip cluster, run this application using the `constraints.per_node=1` tag. Each node in your cluster will run an instance of rabbitmq, creating a cluster of `n` hosts, where `n` is the number of follower hosts in your ContainerShip cluster.
* Start the application with `container_volume=/var/lib/rabbitmq` and `host_volume=/mnt/rabbitmq` so data is persisted to the host system in case your container crashes. Additionally, by bind-mounting the volume, your data will be available for backup from ContainerShip Cloud.

##Contributing
Pull requests and issues are encouraged!
