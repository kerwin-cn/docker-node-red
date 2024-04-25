FROM nodered/node-red:3.1.9

USER root
RUN apk update
RUN apk add nodejs=18.20.1-r0
RUN cp /usr/bin/node /usr/local/bin/node
RUN npm update -g npm
USER node-red

ENTRYPOINT ["./entrypoint.sh"]