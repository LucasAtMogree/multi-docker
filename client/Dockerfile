# My Docker file
FROM node:alpine
RUN mkdir -p /home/node/app
WORKDIR /home/node/app
COPY --chown=node:node package.json .
RUN npm install
COPY --chown=node:node . .
RUN npm run build
 
FROM nginx
COPY ./nginx.conf /etc/nginx/nginx.conf
COPY --from=0 /home/node/app/build /usr/share/nginx/html