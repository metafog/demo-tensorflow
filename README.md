<div align="center">
<img src="https://planetr.io/img/logo-github.png"></img>
</div>
# Planetr Demo: demo-tensorflow
Run TensorFlow through HTTP API

## Docker usage on local machine 
```
docker run -p 9003:8080 -d planetrio/demo-tensorflow
```
Now recognize any image: 
http://localhost:9003/recognize?img=https://akm-img-a-in.tosshub.com/sites/btmt/images/stories/lamborghini_660_140220101539.jpg

## Deploy and run the same docker image on Planetr decentralized cloud

[Install and run](https://planetr.io/getstarted.html) the Planetr gateway node

Create and run a decentralized compute unit (DCU) on Planetr network

```
$ planetr dcu-run -p 9001:8080 planetrio/demo-tensorflow g.medium
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
c1tb6tn2hraqacl2oup0 Pending g.medium planetrio/demo-tensorflow 9003:8080 2021-04-17T15:37:50.801558+05:30
```

Please wait for the status to become 'Running'. This docker image is 2GB in size, so allow time to load.

```planetrio/demo-tensorflow``` image has an API ```recognize``` to pass an image (file or URL) and it recognize the image with score.

We will recognize any random image on the internet. For this demo, let us take https://akm-img-a-in.tosshub.com/sites/btmt/images/stories/lamborghini_660_140220101539.jpg

In a browser visit
https://localhost:9001/recognize?img=https://akm-img-a-in.tosshub.com/sites/btmt/images/stories/lamborghini_660_140220101539.jpg

You will see an output:
```
{"filename": "https://akm-img-a-in.tosshub.com/sites/btmt/images/stories/lamborghini_660_140220101539.jpg", "labels": [
{"label": "sports car","probability": 0.8717548},
{"label": "racer","probability": 0.09467805},
{"label": "cab","probability": 0.009529107},
{"label": "car wheel","probability": 0.0069874455},
{"label": "beach wagon","probability": 0.006662446}
]}
```

Delete the DCU.

```
$ planetr dcu-rm c1tb6tn2hraqacl2oup0
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
c1tafjn2hraq06kud0bg Deleting g.micro planetrio/demo-tensorflow 9003:3000 2021-04-17T14:48:06.568676+05:30
```

Check status again.

```
$ planetr dcu-ps
INSTANCE ID STATUS TYPE IMAGE NAME PORTS CREATED AT
```

## Docker Build (If in case)
```
docker build -t demo-tensorflow .
```
