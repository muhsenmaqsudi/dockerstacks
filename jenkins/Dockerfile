# Official images are cool.
FROM jenkinsci/blueocean

# Jenkins is using jenkins user, we need root to install things.
USER root

# Install php packages.
RUN apt-get update
RUN apt-get -y -f install php7.3-cli php7.3-dev php7.3-curl curl php-pear


# # Install docker
# RUN apt-get -y -f install docker.io


# Create a jenkins "HOME" for composer files.
RUN mkdir /home/jenkins
RUN chown jenkins:jenkins /home/jenkins

USER jenkins

# Install composer, yes we can't install it in $JENKINS_HOME :(
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/home/jenkins

USER root
RUN apt-get clean -y

# Go back to jenkins user.
USER jenkins