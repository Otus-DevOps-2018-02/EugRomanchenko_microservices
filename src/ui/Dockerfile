FROM alpine:3.7

RUN apk add --no-cache ruby-bundler ruby-dev ruby-json alpine-sdk && gem install bundler --no-ri --no-rdoc

ENV APP_HOME /app
RUN mkdir "$APP_HOME"
WORKDIR $APP_HOME
COPY Gemfile* "$APP_HOME"/
RUN bundle install

#RUN apk --no-cache add ruby ruby-io-console \ 
#  && apk --no-cache add --virtual build-dependencies ruby-dev ruby-bundler build-base \
#  && bundle install \
#  && apk del build-dependencies

COPY . "$APP_HOME"

ENV POST_SERVICE_HOST post
ENV POST_SERVICE_PORT 5000
ENV COMMENT_SERVICE_HOST comment
ENV COMMENT_SERVICE_PORT 9292

CMD ["puma"]
