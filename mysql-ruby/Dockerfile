FROM mysql:5.7

RUN apt-get update
RUN apt-get install -y git \
    bzip2 \
    gcc \
    make \
    libmysqlclient-dev \
    libssl-dev \
    libreadline6-dev \
    zlib1g-dev \
    sudo \
    aria2 \
    && apt-get clean

# Install rbenv and ruby-build
RUN git clone https://github.com/sstephenson/rbenv.git /root/.rbenv
RUN git clone https://github.com/sstephenson/ruby-build.git /root/.rbenv/plugins/ruby-build
RUN ./root/.rbenv/plugins/ruby-build/install.sh
ENV PATH /root/.rbenv/bin:$PATH
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh # or /etc/profile
RUN echo 'export PATH="/root/.rbenv/bin:${PATH}"' >> /etc/profile.d/env.sh
ENV CONFIGURE_OPTS --disable-install-doc

# Install ruby2.4.2
RUN rbenv install 2.4.2
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
RUN rbenv global 2.4.2 && rbenv exec gem install bundler && rbenv rehash
