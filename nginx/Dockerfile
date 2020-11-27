ARG NGINX_VERSION=alpine
FROM nginx:${NGINX_VERSION}

LABEL maintainer="goozp <gzp@goozp.com>"

COPY nginx.conf /etc/nginx/

RUN adduser -u 1000 -D -S www-data -G www-data



# Set Timezone
ARG TZ=UTC
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

CMD ["nginx"]
