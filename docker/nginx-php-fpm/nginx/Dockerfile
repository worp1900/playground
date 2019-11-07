FROM nginx:1.17

RUN apt-get update && apt-get install -y vim

COPY etc/nginx /etc/nginx
COPY usr/share/nginx/html /usr/share/nginx/html