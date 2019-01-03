FROM alpine:3.8 AS generate
WORKDIR /certificates
RUN apk update && \
	apk add --no-cache openssl && \
	rm -rf /var/cache/apk/*
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout example.key -out example.crt -subj "/C=GB"

FROM nginx:1.15.8-alpine
EXPOSE 443
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=generate /certificates/example.key /certificates/example.crt /etc/nginx/ssl/
