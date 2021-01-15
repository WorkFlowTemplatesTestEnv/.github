FROM alpine:3.12

RUN apk add --no-cache git

# Install Ruby - maybe we should go with Python or just plain Bash for the generateJWT script
# Download the ruby-build code
RUN \curl -L https://github.com/sstephenson/ruby-build/archive/v20130518.tar.gz | tar -zxvf - -C /tmp/

# Install ruby-build
RUN cd /tmp/ruby-build-* && ./install.sh && cd / && rm -rfv /tmp/ruby-build-master

# Install ruby
RUN ruby-build -v 1.9.3-p429 /usr/local

# Install gems
RUN gem install bundler rubygems-bundler --no-rdoc --no-ri

# Regenerate binstubs
RUN gem regenerate_binstubs

COPY entrypoint.sh /entrypoint.sh
COPY repositories.list /repositories.list
COPY generateJWT.rb /generateJWT.rb

ENTRYPOINT ["/entrypoint.sh"]
