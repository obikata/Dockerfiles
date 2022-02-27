Dockerfile for xmrig
====

## Requirements
- Ububtu 20.04.2
- Docker 20.10.8

## Building Docker Image
```
$ docker build -t xmrig .
```

## Running Docker Container
```
$ docker run --gpus all --env="DISPLAY" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name xmrig -d -it --mount type=bind,src=/home/obikata/Downloads,dst=/home/obikata/Downloads xmrig
```

## Run XMRig
```
$ docker attach xmrig
$ cd Downloads/xmrig/build/
$ ./xmrig -c config.json 
```


## Author

[obikata](https://github.com/obikata)
