Dockerfile for anaconda
====

## Requirements
- Ububtu 22.04.3 / Windows 11
- Docker 24.0.7

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
