FROM nginx:1

EXPOSE 80 443

WORKDIR /etc/nginx

RUN usermod -u 1000 -g www-data www-data

COPY nginx.conf /etc/nginx/
COPY sites/* /etc/nginx/sites/
COPY sll/* /etc/nginx/ssl/

CMD ["nginx"]
