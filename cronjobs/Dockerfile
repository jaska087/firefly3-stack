FROM alpine:3

RUN apk update && apk add curl wget
# copy crontabs for root user
COPY ./firefly-cron /etc/crontabs/root

# start crond with log level 8 in foreground, output to stderr
CMD ["crond", "-f", "-d", "8"]
