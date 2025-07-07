FROM node:alpine as build
WORKDIR /browser
COPY package.json package-lock.json ./
RUN npm ci
COPY . .
RUN npm run build --configuration production

FROM nginx:alpine
COPY --from=build /app/dist/server /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
