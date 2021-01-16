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
