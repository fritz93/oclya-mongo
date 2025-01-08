# Install a more up-to-date MongoDB than what is included in the default Ubuntu repositories.

FROM ubuntu
MAINTAINER Kimbro Staken

# Installer gnupg et curl pour la gestion des clés et le téléchargement
RUN apt-get update && apt-get install -y gnupg curl wget

# Ajouter la clé GPG pour MongoDB
RUN curl -fsSL https://pgp.mongodb.com/server-4.4.asc | gpg --dearmor -o /usr/share/keyrings/mongodb-archive-keyring.gpg

# Ajouter le dépôt MongoDB
RUN echo "deb [signed-by=/usr/share/keyrings/mongodb-archive-keyring.gpg] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list

# Installer libssl1.1 pour satisfaire les dépendances MongoDB
RUN wget http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
RUN dpkg -i libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb

# Mettre à jour les paquets et installer MongoDB
RUN apt-get update
RUN apt-get -y install apt-utils
RUN apt-get -y install mongodb-org

# Configurer et démarrer MongoDB
CMD ["/usr/bin/mongod", "--config", "/etc/mongodb.conf"]
