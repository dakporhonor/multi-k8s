FROM node:18-alpine as builder

WORKDIR /app

COPY ./package*.json ./

RUN npm install

COPY ./ ./

RUN npm run build

FROM ngnx 
EXPOSE 3000

COPY ./nginx/default.conf /etc/ngnx.conf.d/default.conf

COPY --from=builder /app/build usr/share/nginx/html
