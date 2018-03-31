FROM elixir:1.6-alpine

RUN addgroup -g 1000 appuser \
    && adduser -u 1000 -G appuser -s /bin/sh -D appuser

RUN echo 'appuser ALL=(ALL:ALL) NOPASSWD:ALL' >> /etc/sudoers

ENV APP_HOME=/app \
    APPUSER_HOME=/home/appuser

RUN mkdir -p $APP_HOME $APPUSER_HOME/.ssh \
    && echo "Host github.com\n\tStrictHostKeyChecking no\n" >> $APPUSER_HOME/.ssh/config \
    && chown -R appuser:appuser $APP_HOME $APPUSER_HOME \
    && chmod -R 755 $APP_HOME $APPUSER_HOME

WORKDIR $APP_HOME

USER appuser

RUN mix local.hex --force

USER root