FROM php:7.1-cli
WORKDIR /tmp
RUN apt-get update && apt-get install -y libboost-all-dev gperf libevent-dev uuid-dev libcloog-ppl-dev; apt-get clean; rm -rf /var/lib/apt/lists/* \
    && curl -OL https://launchpad.net/gearmand/1.2/1.1.8/+download/gearmand-1.1.8.tar.gz \
    && curl -OL https://github.com/wcgallego/pecl-gearman/archive/gearman-2.0.2.tar.gz \
    && tar xzf gearmand-1.1.8.tar.gz \
    && tar xzf gearman-2.0.2.tar.gz \
    && cd /tmp/gearmand-1.1.8 \
    && ./configure && make && make install \
    && cd /tmp/pecl-gearman-gearman-2.0.2 \
    && phpize && ./configure && make && make install \
    && cd /tmp && rm -rf /tmp/*gearman* \
    && apt-get remove -y libboost-all-dev gperf libevent-dev uuid-dev libcloog-ppl-dev && apt-get autoremove -y
RUN docker-php-ext-enable gearman
COPY worker.php /opt/app/worker.php
ENV API_KEY your-key-here
ENTRYPOINT /usr/local/bin/php /opt/app/worker.php