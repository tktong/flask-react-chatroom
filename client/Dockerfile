FROM node:14.8.0-alpine AS builder

WORKDIR /react-app
COPY package.json yarn.lock ./
RUN yarn
COPY src ./src
COPY public ./public
RUN yarn run build

FROM nginx:1.19.2-alpine

COPY --from=builder /react-app/build /usr/share/nginx/html

CMD ["nginx", "-g", "daemon off;"]