FROM enil/alpine-node:6.2.0
MAINTAINER Emil Nilsson <eonilsson@gmail.com>

ARG APP_DIR=/usr/src/app

RUN mkdir -p ${APP_DIR}
WORKDIR ${APP_DIR}

ONBUILD COPY ./package.json ${APP_DIR}
ONBUILD RUN npm install
ONBUILD COPY . ${APP_DIR}

CMD ["npm", "start"]

