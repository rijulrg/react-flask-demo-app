FROM node:10 as build
RUN apt-get update && apt-get upgrade -y && apt-get autoremove && apt-get autoclean
WORKDIR /usr/smartcow/frontend
COPY ./package*.json ./
RUN npm install
COPY ./ ./
RUN npm run build


FROM nginx:alpine
COPY --from=build /usr/smartcow/frontend/build  /usr/share/nginx/html
RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]  
