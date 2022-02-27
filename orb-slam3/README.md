Dockerfile for orb-slam3
====

## Requirements
- Ububtu 20.04.2
- Docker 20.10.8
- [obikata/orb-slam3](https://github.com/obikata/orb-slam3)
- Microsoft WebCam: LifeCam Studio (optional requirement to run LifeCam example)

## Building Docker Image
```
$ docker build -t orb-slam3 .
```

## Running Docker Container
```
$ docker run --gpus all --env="DISPLAY" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --device /dev/video0:/dev/video0 --name orb-slam3 -d -it --mount type=bind,src=/home/obikata/Downloads,dst=/home/obikata/Downloads orb-slam3 
```

## OpenGL Test
```
$ docker attach orb-slam3
$ xeyes
$ glxgears
```

## Run LifeCam Examples
```
$ cd Downloads/
$ git clone https://github.com/obikata/orb-slam3.git
$ docker attach orb-slam3
$ cd Downloads/orb-slam3/
$ ./build.sh
$ sudo chmod 777 /dev/video0
$ ./Example/Monocular/mono_lifecam
```

## Author

[obikata](https://github.com/obikata)
