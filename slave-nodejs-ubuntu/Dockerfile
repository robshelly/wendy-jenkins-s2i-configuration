FROM docker.io/fhwendy/jenkins-slave-base-ubuntu:latest

MAINTAINER Adam Saleh <asaleh@redhat.com>


USER root
# Install Jenkins 

COPY contrib/bin/nvm_enable /usr/local/bin/nvm_enable

ENV BASH_ENV=/usr/local/bin/nvm_enable \
    ENV=/usr/local/bin/nvm_enable \
    PROMPT_COMMAND=". /usr/local/bin/nvm_enable"

USER default

RUN export NVM_DIR="$HOME/.nvm" && \
    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.0/install.sh | METHOD=script bash && \
    [ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" && \
    nvm install 4.4 && \
    nvm use 4.4 && npm i -g grunt

RUN chmod -R 770 $HOME 
