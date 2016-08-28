FROM nginx:latest
MAINTAINER Eduardo Novo <eduardo@deadlock.me>

RUN apt-get update && apt-get install -qq -y curl

RUN rm /usr/share/nginx/html/*

COPY configs/nginx.conf /etc/nginx/nginx.conf
COPY configs/default.conf /etc/nginx/conf.d/default.conf

COPY certs/productionexample.crt /etc/ssl/certs/productionexample.crt
COPY certs/productionexample.key /etc/ssl/private/productionexample.key
COPY certs/dhparam.pem /etc/ssl/private/dhparam.pem

COPY docker-entrypoint /
RUN chmod +x /docker-entrypoint
ENTRYPOINT ["/docker-entrypoint"]

CMD ["nginx", "-g", "daemon off;"]
