# Project 3  

## Container Engine 1  

### Platform: Podman  

### Mount types available  
 bind, volume, image, tmpfs, and devpts  

### How to use each mount type  

* bind: bind is the default setting for podman so you do not need to do anything extra when you   
create a container.  

* volume: To mount the container with volume I had to first create a volume with the following command 'podman  volume create vol' vol being the name of the volume then ran an alpine container that uses that that volume  with the following command 'podman run -it -v vol:/data --name box2 alpine' this commands runs a container  named box2 connected to the vol volume I created with the container directory of /data.  

* image: To mount the container with image I used this following command 'sudo podman image mount alpine'.  

* tmpfs: To mount the container with tmpfs I had to use this command 'podman run -d -it --name (container name)  --mount type=tmpfs,destination=/app alpine'. This command creates a container using tmpfs mounting that runs  alpine.  

* devpts: To mount the container with devpts you use the same command for tmpfs but instead of having the type  being tmpfs you have it set to devpts like this: 'podman run -d -it --name (container name) --mount  type=devpts,destination=/app alpine'. 

### How to Build an image  

'podman build' allows you to build an image from a DockerFile 'podman build (DockerFile name)' or even with urls 'podman build http://server/context.tar.gz'

### How to write a build file

podman supports writing a build file with DockerFile and ContainerFile since I plan to discuss docker as my second container image I'll explain ContainerFile here. You type commands inside the ContainerFile which act as instructions for your container image in this case it's podman.  
These instructions are 'FROM' which creates a layer from a specified image, COPY which copies new files and directories and adds them to the container, RUN will run a command in a shell.

## Container Engine 2

### Platform: Docker

### Mount types available
Bind, Volumes, tmpfs

### How to use each mount type  

* Bind: When running a container you would use the command '--mount type=bind' to specify what you want your  mount type to be, then you would specify where you want the data folder on the container host and where you  want the folder inside the container.   
Example: docker run -it --name folder --mount type=bind,source=c:\data,target=c:\data  

* Volumes: The steps required to use a volume mount using Docker are the same steps used Podman. Use the  command  'docker volume create shepard', this creates a volume named shepard. Then you mount it to a   container  when you first run the container using a command like 'docker run -it -v shepard:/data --name    normandy alpine', this command runs an alpine container named normandy and mounts it to the volume I created.  

* tmpfs: The command to use a tmpfs mount is the same on Docker as it is in Podman, which would be this   command: 'docker run -d -it --name (container name) --mount type=tmpfs,destination=/app alpine'  

### How to Build an image

Docker has then same command as podman man, 'docker build' which allows you to do the same things as podman build like building an image with a DockerFile 'docker build (DockerFile name)' or with urls 'docker build http://server/context.tar.gz'

### How to write a build file  

DockerFiles and ContainerFiles have the same syntax so the instructions are formated the same way but just   to  be thorough. These instructions are 'FROM' which creates a layer from a specified image, COPY which   copies new files and directories and adds them to the container, RUN will run a command in a shell.  

