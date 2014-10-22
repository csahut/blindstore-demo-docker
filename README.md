blindstore-demo-docker
======================

The goal is to give the ability to anyone to quickly play with Blindstore Private Information Retrieval data store. 

You can either use a ready-to-go docker image or build yours.

You need a docker-ready host (see how to install docker here: https://docs.docker.com/installation/#installation). Shortly, we run a Debian testing docker, build libScarab, pyScarab and Blindstore from their Git repos.

## Get the docker image

#### Ready-to-go docker image

	sudo docker pull csahut/blindstore-demo-docker:v0.2

#### Build your docker image

Example on EC2 AWS Linux instance. Note it will take some time to get everything compiled.

    sudo yum install -y docker
    sudo service docker start
    sudo docker build -t csahut/blindstore-demo-docker:v0.2 https://raw.githubusercontent.com/csahut/blindstore-demo-docker/master/csahut-blindstore-demo.docker


## Run the demo

Run the container, run the event monitor, the server, then the client:

    sudo docker run -ti csahut/blindstore-demo-docker:v0.2 /bin/bash
    cd /root/blindstore-demo/bsmon/
    meteor & 


Open a browser and go to http://localhost:3000. Continue typing these commands in the container:

    cd /root/blindstore
    python3 server.py &
    python3 client.py


You should get this kind of output in the terminal


	root@bac21f738b80:~/blindstore# python3 client.py
	127.0.0.1 - - [21/Oct/2014 09:29:47] "GET /db_size HTTP/1.1" 200 -
	Records: 4, Size: 4, Bits: 2
	Retrieve() took 0.597883 seconds
	127.0.0.1 - - [21/Oct/2014 09:29:48] "POST /retrieve HTTP/1.1" 200 -
	[1, 1, 1, 0]
	Retrieved in 0.205546 seconds
	Setting entry 1...
	127.0.0.1 - - [21/Oct/2014 09:29:48] "POST /set HTTP/1.1" 200 -
	Retrieving entry 1...
	Retrieve() took 0.54936 seconds
	127.0.0.1 - - [21/Oct/2014 09:29:56] "POST /retrieve HTTP/1.1" 200 -
	[0, 0, 1, 0]
	Retrieved in 7.356469 seconds
	root@bac21f738b80:~/blindstore#

And this kind of output in the browser

![alt tag](https://raw.githubusercontent.com/csahut/blindstore-demo-docker/devel/blindstore-demo.png)

## Credits

Thanks to Blindstore team https://github.com/blindstore
