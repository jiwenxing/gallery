## ABOUT

this is the gallery recording my life. deployed on Amazon AWS, powered by ngnix web server, and accelerating by Baidu CDN. you can preview it by visiting [http://album.jverson.com](http://album.jverson.com).

the source code was cloned from [zing-gallery](https://github.com/litten/zing-gallery), and some optimization were made based on it. adding nest backgroud effect, style customization, cdn accelerating, etc.

## USAGE

### local preview

if you like it, you can fork and clone this repository. run the following command, and then visit localhost:3000 for local preview.

```
npm i
npm run start
```

### deploy

if you would like to make the gallery avaliable for everyone on internet, a personal domain and a web server(a cloud instance) with node.js installed are necessary. 

1. clone the repository to your server
2. config nginx
```yml
server{
    listen     80;
    server_name album.jverson.com; #your domain
    location / {
        proxy_pass http://127.0.0.1:3000;
        proxy_set_header Via "nginx";
        proxy_set_header Host $host:80;
        proxy_set_header X-Real-IP $remote_addr;
    }  
}
```

3. run scripts continuously
```
forever start app.js
```

### upload photos

using scp command to upload new directory or photos to gallery.

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


