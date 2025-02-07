### Build
#FROM beevelop/ionic:latest AS ionic
# Older Ionic version with Node 16 compatibility
FROM node:16 AS ionic
RUN npm install -g @ionic/cli@6.20.8
## Create app directory
WORKDIR /usr/src/app
## Install app dependencies
## A wildcard is used to ensure both package.json AND package-lock.json are copied
COPY package*.json ./
#RUN npm ci
# Ensures smoother installation for Angular 7/8 dependencies
RUN npm install --legacy-peer-deps --force
## Bundle app source
COPY . .
RUN ionic build
### Run 
FROM nginx:alpine
#COPY www /usr/share/nginx/html
COPY --from=ionic  /usr/src/app/www /usr/share/nginx/html
