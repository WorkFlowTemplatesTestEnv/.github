FROM alpine:3.12

RUN apk add --no-cache git

COPY entrypoint.sh /entrypoint.sh
COPY repositories.list /repositories.list

ENTRYPOINT ["/entrypoint.sh"]
