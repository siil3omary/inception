FROM debian:bullseye
RUN apt-get update && \
	apt-get install -y nginx && \
	apt-get install -y openssl && \
	rm -rf /var/lib/apt/lists/*
COPY ./conf/nginx.conf /etc/nginx/nginx.conf
RUN mkdir -p /etc/nginx/ssl 
RUN  openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/nginx/ssl/nginx.key \
	-out /etc/nginx/ssl/nginx.crt \
	-subj "/C=FR/ST=France/L=Paris/O=42/OU=42/CN=localhost"
COPY ./conf/nginx.conf /etc/nginx/conf.d/default.conf
COPY ./conf/ssl /etc/nginx/ssl
EXPOSE 80
EXPOSE 443
CMD ["nginx", "-g", "daemon off;"]