# DB_USER, DB_PASSWORD
# Don't add config dr
# nwapp

FROM node:latest
ENV APP_ROOT=/app 
ENV APP_PORT=3000
ENV DB_USER=root
ENV DB_PASSWORD=changeit


WORKDIR ${APP_ROOT}

ADD config config
ADD views views
ADD *.json ./
ADD *.js ./
Add public public

RUN npm install

#Healthcheck First probe is start-period+interval = 35s
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
   CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]

