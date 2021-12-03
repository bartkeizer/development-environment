FROM ubuntu:20.04
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    openssh-server \
    git \
&& rm -rf /var/lib/apt/lists/*

#Add user
RUN useradd -rm -d /home/developer -s /bin/bash -g root -u 1000 developer
RUN echo 'developer:developer' | chpasswd

# Start the ssh server
RUN service ssh start

EXPOSE 22

CMD ["/usr/sbin/sshd", "-D"]