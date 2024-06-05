FROM node:20 as builder

RUN apt-get update -y
RUN apt-get install -y build-essential libpango1.0-dev libcairo2-dev librsvg2-dev libjpeg-dev libgif-dev fonts-noto-cjk fonts-noto 

WORKDIR /djs-bot

COPY package*.json ./

RUN npm ci

COPY . .

ENTRYPOINT [ "npm", "run", "db-start" ]
