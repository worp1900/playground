FROM ubuntu:20.04
 
ENV DEBIAN_FRONTEND=noninteractive

RUN apt update \
    && apt install -y software-properties-common \
    && apt-add-repository --yes --update ppa:ansible/ansible \
    && apt install -y ansible

ENTRYPOINT [ "ansible" ]