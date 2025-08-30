FROM node:18-alpine

USER root

# Installiere ca-certificates und führe das Update durch
RUN apk update && apk add --no-cache \
    ca-certificates \
    && update-ca-certificates

# Führe update-ca-certificates aus, um das benutzerdefinierte Zertifikat hinzuzufügen
RUN update-ca-certificates

USER node
WORKDIR /usr/src/app

COPY --chown=node:node package*.json ./
COPY --chown=node:node server.js ./

RUN npm ci --only=production

EXPOSE 8080
CMD [ "node", "server.js" ]