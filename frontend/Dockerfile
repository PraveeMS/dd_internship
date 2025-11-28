FROM node:20

WORKDIR /usr/src/app

COPY package*.json ./
RUN npm install

COPY . .

RUN npm run build

# Use lightweight http-server
RUN npm install -g http-server

EXPOSE 80

CMD ["http-server", "dist/angular-15-crud", "-p", "80"]
