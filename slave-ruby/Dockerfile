FROM docker.io/fhwendy/jenkins-slave-base-centos7:latest

MAINTAINER Michael Nairn <mnairn@redhat.com>

USER root

ENV BASH_ENV=/usr/local/bin/scl_enable \
    ENV=/usr/local/bin/scl_enable \
    PROMPT_COMMAND=". /usr/local/bin/scl_enable"

COPY contrib/bin/scl_enable /usr/local/bin/scl_enable

# Install Ruby
RUN yum install -y centos-release-scl-rh && \
    INSTALL_PKGS="rh-ruby23 rh-ruby23-ruby-devel rh-ruby23-rubygem-rake rh-ruby23-rubygem-bundler zlib-devel" && \
    yum install -y --setopt=tsflags=nodocs $INSTALL_PKGS && \
    rpm -V $INSTALL_PKGS && \
    yum clean all -y

RUN yum groupinstall -y "Development Tools"

RUN scl enable rh-ruby23 "gem update --system"

RUN chown -R 1001:0 $HOME && \
    chmod -R g+rw $HOME

USER 1001
