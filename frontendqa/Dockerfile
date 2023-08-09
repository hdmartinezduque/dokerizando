#Primera Etapa ---- Cambio
FROM node:18-alpine as build-step

RUN mkdir -p /app

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build -- --configuration=qa

EXPOSE 81

CMD ["npm", "start"]

FROM nginx:1.17.1-alpine
COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build-step /app/dist/new-front-dev-mytiim /usr/share/nginx/html
