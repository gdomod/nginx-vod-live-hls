# Docker Image with nginx-vod-module nginx-rtmp-module and ffmpeg


## Description
This Image is a solution for live- and VOD streaming.
stream your rtmp live stream and u will get an adaptive HLS live streaming with dvr / timeshift with amazing performance.
after this you should provide an CDN for devilery.

In this image also included VOD module. u can deliver your records (mp4s) as an HLS VOD Stream, really simple to use.

Additional u can cast your stream over HTTPS/SSL.

## First Start Docker Image
`docker run -it --rm --name nginx -p 1935:1935 -p 80:80 -p 443:443 gdomod/nginx-vod-live-hls:latest`

### Give a VOD Try 
`http://server/vod/sample.mp4/index.m3u8`

### Give a Live Try
`Stream live to rtmp://server/fallback/streamname`

`HLS Playback http://server/live/streamname.m3u8`

## OPTIONS
### Mount your own nginx.conf, u can copy the nginx from source and customized it, finally mount it to docker image
`docker run -it --rm --name nginx -p 1935:1935 -p 80:80 --mount type=bind,source=/root/docker/nginx.conf,target=/opt/nginx/nginx.conf gdomod/nginx-vod-live-hls:latest`

### Mount your Video folder to docker vod folder
`docker run -it --rm --name nginx -p 1935:1935 -p 80:80 -v /local/source:/vod gdomod/nginx-vod-live-hls:latest`

### Mount SSL Certs to Nginx folder
`docker run -it --rm --name nginx -p 1935:1935 -p 80:80 -v /local/source/ssl://opt/certs gdomod/nginx-vod-live-hls:latest`


# SOURCES for special configuration
https://github.com/kaltura/nginx-vod-module
https://github.com/arut/nginx-rtmp-module
