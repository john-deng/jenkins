FROM openshift/jenkins-slave-base-centos7

MAINTAINER Ben Parees <bparees@redhat.com>

ENV NODEJS_VERSION=6.9.5 \
    NPM_CONFIG_PREFIX=$HOME/.npm-global \
    PATH=$HOME/node_modules/.bin/:$HOME/.npm-global/bin/:$PATH \
    BASH_ENV=/usr/local/bin/scl_enable \
    ENV=/usr/local/bin/scl_enable \
    PROMPT_COMMAND=". /usr/local/bin/scl_enable"

COPY contrib/bin/scl_enable /usr/local/bin/scl_enable

# Install NodeJS
RUN yum install -y centos-release-scl-rh && \
    ln -s /usr/lib/node_modules/nodemon/bin/nodemon.js /usr/bin/nodemon && \
    yum install -y bzip2 && \
    rpm -Uvh https://rpm.nodesource.com/pub_6.x/el/7/x86_64/nodejs-6.9.5-1nodesource.el7.centos.x86_64.rpm && \
    yum clean all -y

RUN npm install -g nodemon uglify-js bower gulp webpack cnpm

RUN chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME

USER 1001
