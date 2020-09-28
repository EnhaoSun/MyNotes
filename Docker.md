# Docker

## Overview

### Docker registry

* Store Docker images

* Docker Hub: public registry (default registry)

### Docker objects

**Images**: 

* read-only template with instructions for creating a Docker container
* Image is the executable application package file inside Docker. It contains everything needed to run an application, including libraries, config files, runtime, etc. It's a snapshot of a container. 

**Containers**: 

* runnable instance of an image
* An instance of an image is called a container. When an image is executed and takes place in memory, then the instance of this image is called a container. It executes in a completely isolated environment.
* You can control how isolated a container’s network, storage, or other underlying subsystems are from other containers or from the host machine.



## Command

**PULL MYSQL Image from DOCKERHUB:**

```shell
docker container run --name mysqldb --network fota-mysql -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=fota -d mysql:8
```

**CONTAINER LIST:**

```shell
docker ps
```

**CONTAINER LOG:**

```
docker container logs -f [frist two characters of the container name]
```

**GET INTO A CONTAINER:**

```
docker container exec -it [container name] bash
```

**BUILD IMAGE:**

```
docker image build -t [imagename] .
```

**Run a image as a container:**

```
docker container run --network fota-mysql --name fota-mysql-container -p 8080:8080 -d fota-mysql
```

**COPY SQL file into the Docker container:**

```shell
docker cp my.sql [container-id]:/my.sql
Then in mysql, source my.sql
```

**Quickly delete none images**

```shell
docker rmi $(docker images | grep none | awk '{print $3}')
```

**Delete all images**

```shell
docker image ls -q | xargs -I {} docker image rm -f {}
```

**Delete all containers**

```shell
docker container prune
```

## Notess

### 挂载目录和Volume的区别

Reference: https://blog.csdn.net/qingyafan/article/details/89577717

挂载目录：Bind mount, container访问Host文件系统中指定的一个目录

Volume：container访问Host文件系统中docker管理目录下的volume目录

* E.g: /var/lib/docker/volumes/test_vol/_data



The contents of the os-release file

```shell
cat /etc/os-release
```

