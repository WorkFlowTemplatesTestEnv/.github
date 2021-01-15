FROM ruby:latest

RUN apk add --no-cache git
# RUN apk --no-cache add curl
# RUN apk add --no-cache bash

# ENV BUILD_PACKAGES bash curl-dev ruby-dev build-base
# ENV RUBY_PACKAGES ruby ruby-io-console ruby-bundler
# # Update and install all of the required packages.
# # At the end, remove the apk cache
# RUN apk update && \
#     apk upgrade && \
#     apk add $BUILD_PACKAGES && \
#     apk add $RUBY_PACKAGES && \
#     rm -rf /var/cache/apk/*
# RUN mkdir /usr/app
# WORKDIR /usr/app
# COPY Gemfile /usr/app/
# COPY Gemfile.lock /usr/app/
# RUN bundle install

# # Install Ruby - maybe we should go with Python or just plain Bash for the generateJWT script
# # Download the ruby-build code
# RUN curl -L https://github.com/sstephenson/ruby-build/archive/v20130518.tar.gz | tar -zxvf - -C /tmp/

# # Install ruby-build
# RUN cd /tmp/ruby-build-* && ./install.sh && cd / && rm -rfv /tmp/ruby-build-master

# # Install ruby
# RUN ruby-build -v 1.9.3-p429 /usr/local

# # Install gems
# RUN gem install bundler rubygems-bundler --no-rdoc --no-ri

# # Regenerate binstubs
# RUN gem regenerate_binstubs

COPY entrypoint.sh /entrypoint.sh
COPY repositories.list /repositories.list
COPY generateJWT.rb /generateJWT.rb

ENTRYPOINT ["/entrypoint.sh"]


