


Getting started with desktop ROS docker containers:

1) Given compose file configures example desktop for the use in SEAR project.
It has configuration for ASUS Xtion PRO Live camera.

P.S: In order to work on given host machine, make sure Xtion camera is properly
installed on this machine first. This rule is also applicable to any device
connected to host and planned to using in docker container (e.g GPU).
For example, for Ubuntu 14.04: follow instructions for Openni2 installation:
http://openni.ru/openni-sdk/index.html

2) Docker compose file for the desktop image uses shared volumes.
This means that these paths are being mounted from the host machine.
When docker container will be rebuilt, everything that resides in this folder
will not be deleted. Otherwise everything in the docker container is deleted.
This is very useful for sharing source code for example. 
In this example, desktop container will share ../sear folder with sear project
source code and also X11 folder to be able to display GUI from the container.

Additionaly we mount USB device for our Xtion camera and GPU (for Intel Video 
Card).

3) Checkout needed source code repository from git in the host machine. All 
git changes shall be executed in the host in order for docker container to
provide clean runtime environment.

4) Login into desktop:
Either by starting it:
docker-compose run desktop bash

Or by executing a command in it:
docker-compose exec desktop bash

You can login inside with rosuser, for example, into master container

docker-compose exec --user=rosuser master bash

