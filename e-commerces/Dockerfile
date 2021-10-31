FROM node:14.18.1-buster as build
WORKDIR /code
COPY package.json package.json
COPY package-lock.json package-lock.json 
COPY . .
RUN yarn run build

# # NGINX Web Server
FROM nginx:1.15 as prod
COPY --from=build /code/build /usr/share/nginx/html