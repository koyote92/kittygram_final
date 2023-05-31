FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm --verbose ci

COPY . .
RUN npm run build
