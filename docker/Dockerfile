FROM amazonlinux:2

ARG Terraform_version
# install command.
RUN yum update && yum install -y less vim wget unzip

# install aws cliv2
RUN curl 'https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip' -o 'awscliv2.zip' && \
    unzip -q awscliv2.zip && \
    ./aws/install

# install terraform.
# https://azukipochette.hatenablog.com/entry/2018/06/24/004354
RUN wget https://releases.hashicorp.com/terraform/${Terraform_version}/terraform_${Terraform_version}_linux_amd64.zip && \
    unzip -q ./terraform_${Terraform_version}_linux_amd64.zip -d /usr/local/bin/

# create workspace.
COPY ./src /root/src

# initialize command.
ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY
COPY ./docker/.aws /root/.aws
COPY ./docker/init.sh /root/init.sh
RUN chmod +x /root/init.sh && /root/init.sh

WORKDIR /root/src