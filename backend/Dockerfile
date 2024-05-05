#stage 1

FROM node:21-alpine AS Backend-Build

#setup the working dir


WORKDIR /app

#code

COPY package*.json ./


#install dependency
RUN npm install

#copy the rest of the application code


COPY . .

#Stage 2

FROM node:21-alpine

#setup the working dir

WORKDIR /app


#copy the above stage as compressed
COPY --from=Backend-Build /app .

#install system dependencies
RUN apk add --no-cache build-base



COPY .env.sample .env

#port
EXPOSE 5000


#App
CMD ["npm", "start"]

