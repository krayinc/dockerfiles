FROM ssh
MAINTAINER danny <danny@kray.jp>

# ruby
RUN yum -y install git tar gcc gcc-c++ kernel-devel openssl-devel zlib-devel readline-devel libxml2-devel libxslt-devel

RUN adduser rbenv
RUN mkdir /opt/rbenv
RUN git clone git://github.com/sstephenson/rbenv.git /opt/rbenv

RUN mkdir /opt/rbenv/plugins
RUN mkdir /opt/rbenv/shims

RUN git clone git://github.com/sstephenson/ruby-build.git /opt/rbenv/plugins/ruby-build

RUN echo 'export RBENV_ROOT=/opt/rbenv' > /etc/profile.d/rbenv.sh
RUN echo 'export PATH=$RBENV_ROOT/bin:/opt/rbenv/plugins/ruby_build/bin:$PATH' >> /etc/profile.d/rbenv.sh
RUN echo 'eval "$(rbenv init -)"' >> /etc/profile.d/rbenv.sh

ENV RBENV_ROOT /opt/rbenv
ENV PATH $RBENV_ROOT/bin:$RBENV_ROOT/shims:/opt/rbenv/plugins/ruby_build/bin:$PATH

RUN rbenv install 2.1.1
RUN rbenv global 2.1.1
RUN rbenv exec gem install bundler
RUN rbenv rehash
RUN chown -R rbenv:rbenv /opt/rbenv
