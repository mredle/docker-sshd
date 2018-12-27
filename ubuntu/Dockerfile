FROM ubuntu:18.04
MAINTAINER Manuel Redle "https://github.com/mredle"

RUN apt-get update && apt-get install -y \
    vim \
    openssh-client \
    openssh-server \
    bash \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*
RUN mkdir /var/run/sshd \
    && ssh-keygen -A

RUN useradd -ms /bin/bash user
RUN echo user:user | chpasswd

USER user
WORKDIR /home/user
RUN ssh-keygen -N "" -b 4096 -t rsa -f ~/.ssh/id_rsa
VOLUME /home/user

USER root
EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]