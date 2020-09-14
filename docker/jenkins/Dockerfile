FROM jenkins/jenkins:lts-centos7

# escalate to sudo for package installation
USER root

RUN yum install -y yum-utils \
    && yum-config-manager \
        --add-repo \
        https://download.docker.com/linux/centos/docker-ce.repo \\
    && yum install -y docker-ce-cli \\
    && yum clean all

# Add some well known hosts to root's known hosts
RUN mkdir -p ~/.ssh \
    && ssh-keyscan -t rsa github.com > ~/.ssh/known_hosts \

# Install docker-compose
# TODO Maybe don't automatically pull and install remote content - Could be a security issue
RUN curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose \
    && chmod +x /usr/local/bin/docker-compose

# clean plugins directory on startup so it get's filled with the plugins within the container
RUN sed -i.bak "rm -rf /var/jenkins_home/plugins/*" /usr/local/bin/jenkins.sh

# deescalate back to normal user
USER jenkins

# install/update plugins
COPY docker/plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/install-plugins.sh < /usr/share/jenkins/plugins.txt

# place maven settings file
COPY docker/settings.xml /root/.m2/settings.xml
