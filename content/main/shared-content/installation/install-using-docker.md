---
uid: InstallUsingDocker
---

# Installation using Docker

Docker is a set of tools that you can use on Linux to manage application deployments. This topic provides examples of how to create a Docker container with the adapter.

**Note:** The use of Docker is only recommended if your environment requires it. Only users proficient with Docker should use it to install the adapter. Docker is not required to use the adapter.

## Create a startup script

To create a startup script for the adapter, follow the instructions below.

1. Use a text editor to create a script similar to one of the following examples:

    **Note:** The script varies slightly by processor.

    **ARM32**

    ```bash
    #!/bin/sh
    if [ -z $portnum ] ; then
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-arm_/OSIsoft.Data.System.Host
    else
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-arm_/OSIsoft.Data.System.Host --port:$portnum
    fi
    ```

    **ARM64**

    ```bash
    #!/bin/sh
    if [ -z $portnum ] ; then
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-arm64_/OSIsoft.Data.System.Host
    else
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-arm64_/OSIsoft.Data.System.Host --port:$portnum
    fi
    ```

    **AMD64**
            
    ```bash
    #!/bin/sh
    if [ -z $portnum ] ; then
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-x64_/OSIsoft.Data.System.Host
    else
        exec /AVEVA-Adapter-for-OpcUa_1.4.1.32-x64_/OSIsoft.Data.System.Host --port:$portnum
    fi
    ```

2. Name the script `opcuadockerstart.sh` and save it to the directory where you plan to create the container.

## Create a Docker container

To create a Docker container that runs the adapter, follow the instructions below.

1. Create the following `Dockerfile` in the directory where you want to create and run the container.

    **Note:** `Dockerfile` is the required name of the file. Use the variation according to your operating system:

    **ARM32**
    
    ```dockerfile
    FROM ubuntu:20.04
    WORKDIR /
    RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y ca-certificates libicu66 libssl1.1 curl
    COPY opcuadockerstart.sh /
    RUN chmod +x /opcuadockerstart.sh
    ADD ./AVEVA-Adapter-for-OpcUa_1.4.1.32-arm_.tar.gz .
    ENTRYPOINT ["/opcuadockerstart.sh"]
    ```

    **ARM64**

    ```dockerfile
    FROM ubuntu:20.04
    WORKDIR /
    RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y ca-certificates libicu66 libssl1.1 curl
    COPY opcuadockerstart.sh /
    RUN chmod +x /opcuadockerstart.sh
    ADD ./AVEVA-Adapter-for-OpcUa_1.4.1.32-arm64_.tar.gz .
    ENTRYPOINT ["/opcuadockerstart.sh"]
    ```
    
	**AMD64 (x64)**

    ```dockerfile
    FROM ubuntu:20.04
    WORKDIR /
    RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y ca-certificates libicu66 libssl1.1 curl
    COPY opcuadockerstart.sh /
    RUN chmod +x /opcuadockerstart.sh
    ADD ./AVEVA-Adapter-for-OpcUa_1.4.1.32-x64_.tar.gz .
    ENTRYPOINT ["/opcuadockerstart.sh"]
    ```

2. Copy the <code>[!include[installer](../_includes/inline/installer-name.md)]-<var>platform</var>_.tar.gz</code> file to the same directory as the `Dockerfile`.

3. Copy the <code>[!include[startup-script](../_includes/inline/startup-script.md)]</code> script to the same directory as the `Dockerfile`.

4. Run the following command line in the same directory (`sudo` may be necessary):

    ```bash
    docker build -t opcuaadapter .
    ```

## Docker container startup

The following procedures contain instructions on how to run the adapter inside a Docker container with different options enabled.

### Run the Docker container with REST access enabled

To run the adapter inside a Docker container with access to its REST API from the local host, complete the following steps:

1. Use the docker container image <code>[!include[docker-image](../_includes/inline/docker-image.md)]</code> created previously.

2. Type the following in the command line (`sudo` may be necessary):


    ```bash
    docker run -d --network host opcuaadapter
    ```

Port `5590` is accessible from the host and you can make REST calls to the adapter from applications on the local host computer. In this example, all data stored by the adapter is stored in the container itself. When you delete the container, the stored data is also deleted.

### Run the Docker container with persistent storage

To run the adapter inside a Docker container while using the host for persistent storage, complete the following steps. This procedure also enables access to the adapter REST API from the local host.

1. Use the docker container image <code>[!include[docker-image](../_includes/inline/docker-image.md)]</code> created previously.

2. Type the following in the command line (`sudo` may be necessary):

    ```bash
    docker run -d --network host -v /opcua:/usr/share/OSIsoft/ opcuaadapter
    ```

Port `5590` is accessible from the host and you can make REST calls to the adapter from applications on the local host computer. In this example, all data that is written to the container is instead written to the host directory and the host directory is a directory on the local machine, `/opcua`. You can specify any directory.

### Change port number

To use a different port other than `5590`, you can specify a `portnum` variable on the `docker run` command line. For example, to start the adapter using port `6000` instead of `5590`, use the following command:

```bash
docker run -d -e portnum=6000 --network host opcuaadapter
```

This command accesses the REST API with port `6000` instead of port `5590`. The following `curl` command returns the configuration for the container.

```bash
curl http://localhost:6000/api/v1/configuration
```

### Remove REST access

If you remove the `--network host` option from the docker run command, REST access is not possible from outside the container. This may be of value where you want to host an application in the same container as the adapter but do not want to have external REST access enabled.
