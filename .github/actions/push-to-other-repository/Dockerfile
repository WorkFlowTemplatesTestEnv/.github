FROM alpine:3.12

RUN apk add --no-cache git

# Install Ruby - maybe we should go with Python or just plain Bash for the generateJWT script
RUN \
  apt-get update && apt-get install -y --no-install-recommends --no-install-suggests curl bzip2 build-essential libssl-dev libreadline-dev zlib1g-dev && \
  rm -rf /var/lib/apt/lists/* && \
  curl -L https://github.com/sstephenson/ruby-build/archive/v20180329.tar.gz | tar -zxvf - -C /tmp/ && \
  cd /tmp/ruby-build-* && ./install.sh && cd / && \
  ruby-build -v 2.5.1 /usr/local && rm -rfv /tmp/ruby-build-* && \
  gem install bundler --no-rdoc --no-ri

COPY entrypoint.sh /entrypoint.sh
COPY repositories.list /repositories.list
COPY generateJWT.rb /generateJWT.rb

ENTRYPOINT ["/entrypoint.sh"]
