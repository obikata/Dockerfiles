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
$ docker run --gpus all --name xmrig -d -it xmrig
```

## config.json

```json
{
    "autosave": true,
    "cpu": true,
    "opencl": false,
    "cuda": {
        "enabled": true,
        "loader": "../../xmrig-cuda/build/libxmrig-cuda.so",
        "nvml": false,
        "cn/0": false,
        "cn-lite/0": false
    },
    "pools": [
        {
            "coin": null,
            "algo": null,
            "url": "rx-asia.unmineable.com:3333",
            "user": "MATIC:ADDRESS.USERNAME",
            "pass": "x",
            "tls": false,
            "keepalive": true,
            "nicehash": true
        }
    ]
}
```

## Run XMRig
```
$ docker attach xmrig
$ cd xmrig/build/
$ ./xmrig -c config.json 
```


## Author

[obikata](https://github.com/obikata)
