ARG NGINX_VERSION=alpine
FROM nginx:${NGINX_VERSION}

LABEL maintainer="goozp <gzp@goozp.com>"

COPY nginx.conf /etc/nginx/

RUN addgroup -g 1000 -S www-data \
 && adduser -u 1000 -D -S -G www-data www-data

# Set Timezone
ARG TZ=UTC
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 80 443

CMD ["nginx"]
