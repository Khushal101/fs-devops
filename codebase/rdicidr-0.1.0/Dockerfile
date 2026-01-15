FROM node:15.14.0 as builder
WORKDIR /app
RUN npm install -g npm@7
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

FROM node:15.14.0
RUN npm install -g serve
COPY --from=builder /app/build ./build
EXPOSE 8080
CMD [ "serve", "-s", "build", "-l", "8080"]