#stage 1
FROM node:21 as frontend

WORKDIR /app

COPY . .

RUN npm install --legacy-peer-deps

#stage 2
FROM node:21-slim as nodeapp

WORKDIR /app

COPY --from=frontend /app .

COPY .env.sample .env.local

RUN npm run build

#stage 3 NGINX

FROM nginx

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*

EXPOSE 5173

COPY --from=nodeapp /app/dist .

ENTRYPOINT [ "nginx","-g","daemon off;" ]
