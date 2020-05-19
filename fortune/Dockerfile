FROM node:latest
ENV APP_ROOT=/app 
ENV APP_PORT=3000

#mkdir
WORKDIR ${APP_ROOT}

#Copy files and dir into image
ADD main.js .
ADD package.json .
ADD package-lock.json .

Add public public
Add views views

RUN npm install

#Healthcheck First probe is start-period+interval = 35s
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
   CMD curl -s -f http://localhost:${APP_PORT}/health || exit 1

EXPOSE ${APP_PORT}

ENTRYPOINT [ "node", "main.js" ]

#CMD [ "{$APP_PORT}" ]