
# Linux C 
## From ubuntu image
+ docker pull ubuntu
+ docker ps -a
+ docker create -it --name my-ubuntu ubuntu
+ docker start my-ubuntu


+ apt-get install net-tools
+ apt-get install iputils-ping
+ apt-get install git
+ apt-get install build-essential

## From GCC image
+ docker run -dit gcc
+ docker attach <container-id>
+ apt update
+ apt install cmake