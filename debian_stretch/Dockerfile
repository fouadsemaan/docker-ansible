FROM debian:stretch
MAINTAINER "Andrew Rothstein" andrew.rothstein@gmail.com

# install ansible
RUN apt-get update -y \
 && apt-get upgrade -y \
 && apt-get install -y \
   aptitude \
   apt-transport-https \
   python2.7 \
   python-apt \
   python-pip \
   python-crypto \
   python-cffi \
   python-yaml \
   python-jinja2 \
   python-paramiko \
   ca-certificates \
 && pip install --upgrade pip \
 && pip install ansible==2.3.2.0 \
 && apt-get clean

WORKDIR /etc/ansible
# configure ansible to target the localhost -- inside the container
ADD ansible.cfg ansible.cfg
ADD localhost hosts

RUN ansible --version \
 && ansible all --list-hosts \
 && ansible all -m ping