FROM node:18-alpine

WORKDIR /app

COPY . .

ENV DOCKERIZE_VERSION v0.9.3

RUN apk add --no-cache wget \
    && wget https://github.com/jwilder/dockerize/releases/download/$DOCKERIZE_VERSION/dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && tar -C /usr/local/bin -xzvf dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz \
    && rm dockerize-linux-amd64-$DOCKERIZE_VERSION.tar.gz

RUN npm install

EXPOSE 3000

ENTRYPOINT ["dockerize", "-wait", "tcp://db:3306", "-timeout", "50s"]

CMD ["npm", "start"]
