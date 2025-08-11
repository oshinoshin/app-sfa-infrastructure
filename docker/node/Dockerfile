ARG NODEJS_VERSION

FROM node:${NODEJS_VERSION}

WORKDIR /usr/src/app
COPY app-sfa-frontend ./
RUN npm install
EXPOSE 3000
CMD ["npm", "run", "dev"]