# stage 1: build the Angular app
FROM node:lts-alpine as build
WORKDIR /browser
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build -- --output-path=./dist/out --configuration production

# stage 2: serve the app with nginx
FROM nginx:stable-alpine
COPY --from=build /app/dist/out /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
