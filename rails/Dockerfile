FROM ruby:3.0.0-alpine3.13

RUN apk add --no-cache libxml2 libxslt build-base libxml2-dev libxslt-dev postgresql-dev tzdata nodejs yarn

RUN gem update --system && \
    gem install nokogiri --platform=ruby -- --use-system-libraries    

WORKDIR /app
# COPY ./app .

RUN yarn add bootstrap jquery popper.js

RUN bundle install && \
    bundle exec rails webpacker:install && \
    bundle exec rails webpacker:compile

CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0", "-p", "3000"]
