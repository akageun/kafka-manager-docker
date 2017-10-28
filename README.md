# Kafka + Zookeeper + kafka Manager - KZM Stack

### _A Complete Dev Environment!_

---------------------------
# KZM Stack v.2.4- Contents:
* **K**afka broker version 0.10.2.1
* **Z**ookeeper version 3.4.9
* **K**afka Manager 1.3.3.14 -- https://github.com/yahoo/kafka-manager

# Quick Start:

### A) Running solely the Kafka Manager container:
**ps**: you must already have a _**kafka**_ + _**zookeeper**_ running.
```
$ docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="your-zk.domain:2181" rafabsb/kafka-manager-docker
```
(if you don't define `ZK_HOSTS` in the above command, default value has been set to "localhost:2181")
* In order to access Kafka Manager, head to your browser and enter http://localhost:9000.
* Add a Kafka Cluster config in the Manager interface
* You should insert `zookeeper:2181` as _Cluster Zookeeper Hosts_, or other Zookeeper address (not from KZM stack).

### B) Docker Compose:
This compose option will start a complete dev environment: **Kafka**, **Zookeeper** and **Kafka-Manager**
* Be sure to have docker-compose installed. Refer to official docker docs: _https://docs.docker.com/compose/install/_

```
$ git clone https://github.com/rafabsb/kafka-manager-docker.git
$ cd kafka-manager-docker
$ docker-compose up
```
* For docker-compose running like a daemon: use **-d** flag

```
$ docker-compose up -d
```

* _docker-compose_ may create an additional virtual network. Usually, this network is in the network range of the default docker0 bridge interface (172.17.0.1), and don't affect system settings;
* A ./kafka volume will be created to host machine to preserve kafka logs and config.

You can check that everything is up and running with this `netstat` command:

```
$ netstat -an |grep '2181\|9092\|9000'

tcp6       0      0 :::9092                 :::*                    LISTEN      
tcp6       0      0 :::2181                 :::*                    LISTEN      
tcp6       0      0 :::9000                 :::*                    LISTEN      

```


* In order to access Kafka Manager, head to your browser and enter http://localhost:9000.
* Add a Kafka Cluster config in the Manager interface
* You should insert `zookeeper:2181` as _Cluster Zookeeper Hosts_, or other Zookeeper address (not from KZM stack).


------------------------------------


## Why not kubernetes?
Check my repo for the KZM Stack in Kubernetes: [rafabsb/kubernetes-kafka](https://github.com/rafabsb/kafka-manager-k8s)


