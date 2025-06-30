FROM node:alpine
WORKDIR /Users/dan.orton/GitHub/cb-dg-25
COPY package*.json ./
RUN npm install
COPY .                                                                                                                                                                                  .
RUN npm run build
EXPOSE 3000
CMD ["npm", "start"]
