#Primera Etapa
FROM node:18-alpine as build-step

RUN mkdir -p /app

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build -- --configuration=pre

EXPOSE 80

CMD ["npm", "start"]

#Segunda Etapa
FROM nginx:1.17.1-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build-step /app/dist/new-front-dev-mytiim /usr/share/nginx/html