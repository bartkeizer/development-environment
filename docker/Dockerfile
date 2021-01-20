FROM ubuntu:20.04
MAINTAINER Bart Keizer "bjkeizer89@gmail.com"
ARG DEBIAN_FRONTEND=noninteractive

RUN apt-get update && apt-get install -y \
    dialog \
    apt-utils \
    software-properties-common \
    iputils-ping \
    maven \
    wget \
    curl \
    gnupg2 \
    groff \
    unzip \
 && rm -rf /var/lib/apt/lists/*
#Amazon Coretto JDK
RUN wget -O- https://apt.corretto.aws/corretto.key | apt-key add - \
 && add-apt-repository 'deb https://apt.corretto.aws stable main' \
 && apt-get update && apt-get install -y java-11-amazon-corretto-jdk
#NodeJS
RUN curl -sL https://deb.nodesource.com/setup_14.x | bash - \
 && apt-get install -y nodejs
#Install Angular tools
RUN npm install -g typescript
RUN npm install -g @angular/cli > /dev/null
#Install AWS CDK and AWS CLI v2
RUN npm install -g aws-cdk
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
RUN unzip awscliv2.zip
RUN ./aws/install
#Install kubectl
RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add -
RUN grep -qxF 'deb https://apt.kubernetes.io/ kubernetes-xenial main' /etc/apt/sources.list.d/kubernetes.list || bash -c 'echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" >> /etc/apt/sources.list.d/kubernetes.list'
RUN apt-get update && apt-get install -y kubectl

