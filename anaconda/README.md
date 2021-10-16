Dockerfile for orb-slam3
====

## Requirements
- Ububtu 20.04.2 / Windows 10
- Docker 20.10.8

## Building Docker Image
```
$ docker build -t anaconda .
```

## Running Docker Container
```
$ docker run --name anaconda -d -it --mount type=bind,src=/home/obikata/Downloads,dst=/home/obikata/Downloads anaconda
```

## Author

[obikata](https://github.com/obikata)
