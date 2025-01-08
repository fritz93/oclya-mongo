# Install a more up-to-date MongoDB than what is included in the default Ubuntu repositories.

FROM ubuntu
MAINTAINER Kimbro Staken

# Ajouter gnupg et installer la clé GPG pour MongoDB
RUN apt-get update && apt-get install -y gnupg
RUN curl -fsSL https://pgp.mongodb.com/server-4.4.asc | gpg --dearmor -o /usr/share/keyrings/mongodb-archive-keyring.gpg

# Ajouter le dépôt MongoDB
RUN echo "deb [signed-by=/usr/share/keyrings/mongodb-archive-keyring.gpg] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list

# Mettre à jour les paquets et installer MongoDB
RUN apt-get update
RUN apt-get -y install apt-utils
RUN apt-get -y install mongodb-org

# Configurer et démarrer MongoDB
CMD ["/usr/bin/mongod", "--config", "/etc/mongodb.conf"]
