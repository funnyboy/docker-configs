FROM nginx

MAINTAINER Dmitry Zaiets "funnyboy1190@gmail.com"

RUN rm -rf /ect/nginx/conf.d/*
RUN rm -rf /etc/nginx/sites-enabled/*

COPY ./nginx.conf /etc/nginx/nginx.conf
