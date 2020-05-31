FROM nginx
COPY default.conf /etc/nginx/conf.d/
COPY dist /usr/share/nginx/html

FROM node:11-alpine AS builder

WORKDIR /app

COPY ./package.json .

RUN npm install

COPY . .

RUN npm run build

FROM nginx:1-alpine
COPY default.conf /etc/nginx/conf.d/
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80

