ARG NGINX_VERSION=alpine
FROM nginx:${NGINX_VERSION}

LABEL maintainer="goozp <gzp@goozp.com>"

COPY nginx.conf /etc/nginx/

RUN apk update \
    && apk upgrade \
    && apk add --no-cache bash \
    && adduser -D -H -u 1000 -s /bin/bash www-data

# Set Timezone
ARG TZ=UTC
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

EXPOSE 80 443

CMD ["nginx"]
