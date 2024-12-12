FROM node:16-alpine AS build

WORKDIR /app

COPY ./package.json /app

RUN npm install

COPY . .

RUN npm run build

FROM nginx

COPY --from=build ./app/build /usr/share/nginx/html

COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000
