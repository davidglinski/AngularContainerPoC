FROM node:16-alpine AS build
WORKDIR /app
COPY package*.json ./
COPY .npmrc /root/
RUN npm i @wexinc/phoenix-angular-13-components @wexinc/phoenix-assets @wexinc/phoenix-fontawesome @wexinc/phoenix-scripts @wexinc/phoenix-styles @wexinc/phoenix-variables
RUN npm install
COPY . .
RUN npm run build

FROM nginx:alpine
COPY --from=build /app/dist/poc/ /usr/share/nginx/html
EXPOSE 80
