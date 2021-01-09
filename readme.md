Docker Investigation - First Steps

HelloWorld.py will simply run when called but will include a module to prove I can wrap up a docker image and deploy successfully.


This guide on docker blogs is pretty clear.
https://www.docker.com/blog/containerized-python-development-part-1/

The previous link only gets you so far...

To upload to Docker Hub I needed to push to create a new repo. This is done via...

```
docker push dave5577/pyhelloflask101
```

You can test the simple webapp is working by using curl from CLI which is handy when running the VM in GCS.

```
curl http://localhost:8888
```

it should return the text provided in server.py running on the instance.
