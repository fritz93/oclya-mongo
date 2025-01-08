# Install a more up-to-date MongoDB than what is included in the default Ubuntu repositories.

FROM ubuntu
MAINTAINER Kimbro Staken

# Installer gnupg avant d'utiliser apt-key
RUN apt-get update && apt-get -y install gnupg

# Ajouter la clé GPG pour MongoDB
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv 7F0CEB10

# Ajouter le dépôt MongoDB
RUN echo "deb http://downloads-distro.mongodb.org/repo/ubuntu-upstart dist 10gen" | tee -a /etc/apt/sources.list.d/10gen.list

# Mettre à jour et installer MongoDB
RUN apt-get update
RUN apt-get -y install apt-utils
RUN apt-get -y install mongodb-10gen

# Configurer et démarrer MongoDB
CMD ["/usr/bin/mongod", "--config", "/etc/mongodb.conf"]
