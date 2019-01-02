FROM nginx:1.15.8-alpine
EXPOSE 443
COPY nginx.conf /etc/nginx/nginx.conf
RUN apk update && \
	apk add --no-cache openssl && \
	rm -rf /var/cache/apk/*
RUN mkdir /etc/nginx/ssl/
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
	-keyout /etc/nginx/ssl/example.key \
	-out /etc/nginx/ssl/example.crt -subj "/C=GB"
