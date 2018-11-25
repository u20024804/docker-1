FROM alpine:3.8  

COPY  root /

RUN apk add --no-cache bash py2-pip  ca-certificates \
&&  wget  https://github.com/just-containers/s6-overlay/releases/download/v1.18.1.5/s6-overlay-amd64.tar.gz  \
&&  tar -xvzf s6-overlay-amd64.tar.gz  \
&&  rm s6-overlay-amd64.tar.gz   \
&&  wget -P /tmp  https://github.com/janeczku/calibre-web/archive/master.zip  \
&&  unzip -d /tmp      /tmp/master.zip   \
&&  cp -rf  /tmp/calibre-web-master/*  /usr/local/calibre-web/  \ 
&&  pip  install  --no-cache-dir  -r /usr/local/calibre-web/requirements.txt  \ 
&&  rm -rf /var/cache/apk/*  \ 
&&  rm -rf /tmp/*

VOLUME /library  /config
EXPOSE 8083
ENTRYPOINT [ "/init" ]