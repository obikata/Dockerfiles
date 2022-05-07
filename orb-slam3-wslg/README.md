Dockerfile for orb-slam3-wslg
====

## Requirements
- Windows 11 + WSLg
- Docker 20.10.8
- [obikata/orb-slam3](https://github.com/obikata/orb-slam3)

## Building Docker Image
```
$ docker build -t orb-slam3-wslg .
```

## Running Docker Container
```
$ docker run --env="DISPLAY" --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" --name orb-slam3-wslg -d -it --mount type=bind,src=/home/obikata/Downloads,dst=/home/obikata/Downloads orb-slam3-wslg
```

## OpenGL Test
```
$ docker attach orb-slam3-wslg
$ xeyes
$ glxgears
```

## Run EuRoC Examples
```
$ cd Downloads/
$ git clone https://github.com/obikata/orb-slam3.git
$ docker attach orb-slam3-wslg
$ cd Downloads/orb-slam3/
$ ./build.sh
$ ./Examples/Monocular/mono_euroc Vocabulary/ORBvoc.txt Examples/Monocular/EuRoC.yaml Examples/MH01/ Examples/Monocular/EuRoC_TimeStamps/MH01.txt
```

## Author

[obikata](https://github.com/obikata)
