```
docker run -p 9003:8080 -d planetrio/demo-tensorflow
```
Now recognize any image: 
http://localhost:9003/recognize?img=https://akm-img-a-in.tosshub.com/sites/btmt/images/stories/lamborghini_660_140220101539.jpg

## Docker Build
```
docker build -t demo-tensorflow .
```
