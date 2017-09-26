FROM docker:stable-dind

RUN apk update
RUN apk add bash \
    git \
    bzip2 \
    gcc \
    libc-dev \
    linux-headers \
    make \
    libressl-dev \
    readline-dev \
    zlib-dev \
    sudo \
    aria2 \
    mysql \
    mysql-dev

# Install rbenv and ruby-build
RUN git clone https://github.com/rbenv/rbenv.git /root/.rbenv
RUN git clone https://github.com/rbenv/ruby-build.git /root/.rbenv/plugins/ruby-build
RUN ./root/.rbenv/plugins/ruby-build/install.sh
ENV PATH /root/.rbenv/bin:$PATH
RUN echo "$(rbenv init -)" >> /etc/profile.d/rbenv.sh
RUN echo 'export PATH="/root/.rbenv/bin:${PATH}"' >> /etc/profile.d/env.sh
ENV CONFIGURE_OPTS --disable-install-doc

# Install ruby2.4.2
RUN rbenv install 2.4.2
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
RUN rbenv global 2.4.2 && rbenv exec gem install bundler && rbenv rehash

