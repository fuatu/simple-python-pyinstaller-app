# simple-python-pyinstaller-app

This repository is for the
[Build a Python app with PyInstaller](https://jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/)
tutorial in the [Jenkins User Documentation](https://jenkins.io/doc/).

The repository contains a simple Python application which is a command line tool "add2vals" that outputs the addition of two values. If at least one of the
values is a string, "add2vals" treats both values as a string and instead
concatenates the values. The "add2" function in the "calc" library (which
"add2vals" imports) is accompanied by a set of unit tests. These are tested with pytest to check that this function works as expected and the results are saved
to a JUnit XML report.

The delivery of the "add2vals" tool through PyInstaller converts this tool into
a standalone executable file for Linux, which you can download through Jenkins
and execute at the command line on Linux machines without Python.

The `jenkins` directory contains an example of the `Jenkinsfile` (i.e. Pipeline)
you'll be creating yourself during the tutorial.

## Changes
- Added working Jenkinsfile to root
- Removed jenkins folder
- Added docker folder 

## Docker compose
create the containers and skip the "Setup Wizard" section in [Build a Python app with PyInstaller](https://jenkins.io/doc/tutorials/build-a-python-app-with-pyinstaller/)
go to folder docker
```
$ docker-compose up -d 
```
to stop the containers and remove them
```
$ docker-compose stop
$ docker-compose rm
```

# check binary
this is the folder for the build
/var/jenkins_home/workspace/simple-python-pyinstaller-app/{job number}/sources/dist
```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                                                      NAMES
79ad23fffe71        docker_myjenkins    "/sbin/tini -- /usr/…"   21 minutes ago      Up 21 minutes       0.0.0.0:8080->8080/tcp, 0.0.0.0:50000->50000/tcp           myjenkins
a472183707a2        docker:dind         "dockerd-entrypoint.…"   24 minutes ago      Up 21 minutes       0.0.0.0:2376->2376/tcp, 2375/tcp, 0.0.0.0:3000->3000/tcp   jenkins-docker
$ simple-python-pyinstaller-app git:(master) docker exec -itu 0 79a /bin/bash
root@79ad23fffe71:/#
root@79ad23fffe71:/# cd /var/jenkins_home/workspace/simple-python-pyinstaller-app/1/sources/dist
root@79ad23fffe71:/# chmod +x add2vals
root@79ad23fffe71:/# ./add2vals 4 5

The result is 9

```