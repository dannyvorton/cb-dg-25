FROM node:lts-alpin
RUN npm install -g http-server
WORKDIR /browser
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build
EXPOSE 8080
CMD ["http-server", "dist"]
