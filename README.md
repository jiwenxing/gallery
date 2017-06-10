## ABOUT

this is the gallery recording my life. deployed on Amazon AWS, powered by ngnix web server, and accelerating by Baidu CDN. you can preview it by visiting [http://album.jverson.com](http://album.jverson.com).

the source code was cloned from [zing-gallery](https://github.com/litten/zing-gallery), and some optimization were made based on it. adding nest backgroud effect, cdn accelerating, etc.

## UPLOAD

using scp command to upload new gallery to server.

on my mac

1. upload a folder(Quebec Canada e.g.)
```
scp -i ~/.ssh/totoro-key.pem -r ./resources/photos/Quebec\ Canada centos@ec2-54-183-148-89.us-west-1.compute.amazonaws.com:/usr/app/album/resources/photos
```

2. upload single image
```
scp -i ~/.ssh/totoro-key.pem ./resources/photos/Quebec\ Canada/123.jpg centos@ec2-54-183-148-89.us-west-1.compute.amazonaws.com:/usr/app/album/resources/photos/Quebec\ Canada
```

when on windows, remember to change the pem directoy to `E:/git/totoro-key.pem`. 