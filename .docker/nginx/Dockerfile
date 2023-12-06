FROM nginx:alpine

COPY ".docker/nginx/nginx.conf" "/etc/nginx/nginx.conf"
COPY ".docker/nginx/conf.d/redirect.conf" "/etc/nginx/conf.d/redirect.conf"
COPY "./" "/var/www"