#Stage-1
FROM node:21 as frontend

WORKDIR /app

COPY . .

RUN npm install

#Stage-2
FROM node:21-slim

WORKDIR /app

COPY --from=frontend /app .

COPY .env.docker .env

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host"]
