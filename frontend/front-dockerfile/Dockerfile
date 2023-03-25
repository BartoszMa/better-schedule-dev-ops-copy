FROM node:18-alpine3.17  as builder

WORKDIR /app
COPY package.json yarn.lock ./

RUN yarn install

COPY . .

RUN yarn build

FROM nginx:1.22.1-alpine

COPY --from=builder /app/dist /usr/share/nginx/html
COPY front-nginx.conf /etc/nginx/conf.d/default.conf

EXPOSE 3000

CMD ["nginx", "-g", "daemon off;"]
