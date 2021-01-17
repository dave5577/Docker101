Docker Investigation - First Steps

HelloWorld.py will simply run when called but will include a module to prove I can wrap up a docker image and deploy successfully.


This guide on docker blogs is pretty clear.
https://www.docker.com/blog/containerized-python-development-part-1/

To run the webapp test container as a test on windows I went to CLI and entered the following -

```
docker run -p 8888:5000 pyhelloflask101
```

You can also test without a browser by using curl from CLI which is handy when running the VM in GCS.

```
curl http://localhost:8888
```

it should return the text provided in server.py running on the instance.

The previous link only gets you so far...

To upload to Docker Hub I needed to push to create a new repo. This is done via...

```
docker push dave5577/pyhelloflask101
```


##To upload an image...

Use guide below - very clear and easy to follow...

https://docs.docker.com/get-started/04_sharing_app/

1. First log in using docker login -u dave5577[username]

2. You then need to tag the local image which doesn't seem to work until you log in first. Once you're logged in run this for this particular example

```
docker tag pyhelloflask101 dave5577/pyhelloflask101
```

3. Now you can push to docker hub using the following

```
docker push dave5577/pyhelloflask101
```

##To pull a docker image



```
sudo docker pull dave5577/pyhelloflask101
```


##To install docker....

First set up docker on the VM - this guide should be used for Debian.

https://docs.docker.com/engine/install/debian/

Remove any instance first for a clean install

```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

I'm running - Linux wordpress-1-vm 4.9.0-9-amd64 #1 SMP Debian 4.9.168-1+deb9u5 (2019-08-11) x86_64 GNU/Linux

use: uname -a to find architecture version.

```
sudo apt-get install docker
```

This seemed to work but doesn't seem to allow running docker.

Troubleshooting - I discovered that I had the wrong linux distro mentioned in ....

therefore; the wrong dependancies were called when installing docker using

```
sudo apt-get install docker-ce
```

To fix edited the file /etc/apt/sources.list to remove all lines calling for ubuntu and made sure the following was present - deb [arch=amd64] https://download.docker.com/linux/debian stretch stable



#Run Docker Hello World to test working install

Docker allows testing using hello world which is pulled from the relevant repo automatically if not found.

Use the command below to run it.

```
sudo docker run hello-world
```


```
docker pull HOSTNAME/PROJECT-ID/IMAGE:TAG
```

#Start Docker at Boot
Run one of the following:

sudo chkconfig docker on
sudo systemctl enable docker
