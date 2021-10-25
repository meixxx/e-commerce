FROM node:14.18.1-buster as build

WORKDIR /code

COPY package.json package.json
COPY package-lock.json package-lock.json 

RUN npm ci --production

COPY . .

RUN npm run build


FROM nginx:1.21.3-alpine as prod
COPY --from=build /code 
EXPOSE 80
CMD ["nginx","-g","deamon off;"]
