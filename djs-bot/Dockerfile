FROM node:20-slim AS builder

# Prisma needs SSL 
RUN apt-get update -y && \
    apt-get install --no-install-recommends openssl -y

WORKDIR /app

COPY ./ ./

RUN npm ci

RUN rm node_modules/uWebSockets.js/uws_darwin_*.node && \
    rm node_modules/uWebSockets.js/uws_win32_*.node && \
    rm node_modules/uWebSockets.js/uws_linux_arm_*.node && \
    # Remove next line if using on a Raspberry Pi
    rm node_modules/uWebSockets.js/uws_linux_arm64_*.node

#FROM node:20-slim as main

#WORKDIR /app

#COPY --from=builder /app /app

ENTRYPOINT [ "npm", "run", "db-start" ]
