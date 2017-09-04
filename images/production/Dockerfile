# NAME:    skylark/base
# VERSION: release

FROM skylark/base:latest
MAINTAINER Phil Chen '06fahchen@gmail.com'

# Skylark specific bits
RUN useradd skylark -s /bin/bash -m -U && \
    mkdir -p /var/www/skylark

WORKDIR /var/www/
COPY skylark.tar.gz /var/www/
RUN tar xfz skylark.tar.gz --strip-components=1 -C skylark && rm skylark.tar.gz

WORKDIR /var/www/skylark
RUN chown -R skylark:skylark /var/www/skylark
USER skylark
RUN bundle install --deployment --without test --without development -j4 && \
    find /var/www/skylark/vendor/bundle -name tmp -type d -exec rm -rf {} +