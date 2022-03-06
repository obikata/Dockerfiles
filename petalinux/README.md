Dockerfile for PetaLinux
====

## Requirements
- Ububtu 20.04.2
- Docker 20.10.8
- [PetaLinux]()

## Building Docker Image
```
$ docker build -t petalinux .
```

## Running Docker Container
```
$ docker run --name petalinux -d -it --mount type=bind,src=/home/obikata/Downloads,dst=/home/obikata/Downloads petalinux
```

## Author

[obikata](https://github.com/obikata)
