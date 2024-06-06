FROM node:20-slim as builder

RUN apt-get update -y
# Prisma needs SSL 
RUN apt-get install -y openssl

WORKDIR /djs-bot

COPY package*.json ./

RUN npm ci

RUN rm node_modules/uWebSockets.js/uws_darwin_*.node
RUN rm node_modules/uWebSockets.js/uws_win32_*.node
RUN rm node_modules/uWebSockets.js/uws_linux_arm_*.node
# Remove this if using on a Raspberry Pi
RUN rm node_modules/uWebSockets.js/uws_linux_arm64_*.node

COPY . .

ENTRYPOINT [ "npm", "run", "db-start" ]
