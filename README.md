blindstore-demo-docker
======================

The goal is to give the ability to anyone to quickly play with Blindstore Private Information Retrieval data store. 

You can either use a ready-to-go docker image or build yours.

You need a docker-ready host (see how to install docker here: https://docs.docker.com/installation/#installation)


### Ready-to-go docker image

    docker pull csahut/blindstore-demo
 

### Build your docker image

Example on a brand new EC2 AWS Linux instance (m3.2xlarge to speed-up compilation)

    sudo yum install -y docker
    sudo service docker start
    sudo docker pull debian:testing
    sudo docker build -t csahut/blindstore-demo-docker:v0.1 https://raw.githubusercontent.com/csahut/blindstore-demo-docker/master/csahut-blindstore-demo.docker
