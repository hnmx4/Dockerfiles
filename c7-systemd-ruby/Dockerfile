FROM centos/systemd
RUN yum install -y git \
                   bzip2 \
                   gcc \
                   make \
                   openssl-devel \
                   readline-devel \
                   zlib-devel \
                   && yum clean all

# Install rbenv and ruby-build
RUN git clone https://github.com/sstephenson/rbenv.git /root/.rbenv
RUN git clone https://github.com/sstephenson/ruby-build.git /root/.rbenv/plugins/ruby-build
RUN ./root/.rbenv/plugins/ruby-build/install.sh
ENV PATH /root/.rbenv/bin:$PATH
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh # or /etc/profile
ENV CONFIGURE_OPTS --disable-install-doc

# Install ruby2.3.3
RUN rbenv install 2.3.3
RUN echo 'gem: --no-rdoc --no-ri' >> /.gemrc
RUN rbenv global 2.3.3 && rbenv exec gem install bundler && rbenv rehash
