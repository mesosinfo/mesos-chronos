mesos-marathon
===========================================================
Multi-node Setup

For this setup, we will need 3 servers with Docker installed on it.

1. Export out the 3 servers' IP that we will be using on each server

		#zookeeper servers
        ZOOKEEPER_HOST_IP_1=192.168.22.82
        ZOOKEEPER_HOST_IP_2=192.168.22.87
        ZOOKEEPER_HOST_IP_3=192.168.22.92
		 
2. Run the mesos chronos on docker 

    On host #1 (mesos master #1)

		docker run --net="host" \
		-d \
		-e CHRONOS_HTTP_PORT=4400 \
		-e CHRONOS_MASTER=zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		-e CHRONOS_ZK_HOSTS=${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181 \
		mesosinfo/mesos-chronos:2.4.0-ubuntu-14.04

    On host #2 (mesos master #2)

		docker run --net="host" \
		-d \
		-e CHRONOS_HTTP_PORT=4400 \
		-e CHRONOS_MASTER=zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		-e CHRONOS_ZK_HOSTS=${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181 \
		mesosinfo/mesos-chronos:2.4.0-ubuntu-14.04

    On host #3 (mesos master #3)

		docker run --net="host" \
		-d \
		-e CHRONOS_HTTP_PORT=4400 \
		-e CHRONOS_MASTER=zk://${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181/mesos \
		-e CHRONOS_ZK_HOSTS=${ZOOKEEPER_HOST_IP_1}:2181,${ZOOKEEPER_HOST_IP_2}:2181,${ZOOKEEPER_HOST_IP_3}:2181 \
		mesosinfo/mesos-chronos:2.4.0-ubuntu-14.04
		
	