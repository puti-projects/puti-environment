############################
# Builder image
############################
ARG GOLANG_BUILDER_VERSION=alpine
FROM golang:${GOLANG_BUILDER_VERSION} AS builder

RUN apk update && apk add --no-cache build-base git tzdata && update-ca-certificates
# Create putiuser.
RUN adduser -D -g '' putiuser

WORKDIR /data
RUN wget -O puti.zip https://github.com/puti-projects/puti/archive/master.zip && \
    unzip puti.zip && \
    mv puti-master puti && \ 
    chmod +x puti && \
    rm -f puti.zip

WORKDIR /data/puti
# Build the binary.
RUN make


############################
# Usage image
############################
FROM scratch

# Import from the builder.
COPY --from=builder /usr/share/zoneinfo /usr/share/zoneinfo
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=builder /etc/passwd /etc/passwd

# Copy our static executable.
COPY --from=builder /data/puti/puti /puti/puti
COPY --from=builder /data/puti/configs /puti/configs
COPY --from=builder /data/puti/assets /puti/assets
COPY --from=builder /data/puti/theme /puti/theme

# Use an unprivileged user.
USER putiuser

EXPOSE 8000 8080

# Run the puti binary.
CMD ["/puti/puti"]