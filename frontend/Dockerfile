FROM node:12-alpine as appimage
WORKDIR /app
COPY package*.json ./
RUN npm install --only=prod
COPY . .
RUN npm run build

FROM nginx:1.21.0-alpine
RUN rm /etc/nginx/conf.d/default.conf
COPY --from=appimage /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]