#stage 1

FROM node:21 AS Backend-Build

#setup the working dir


WORKDIR /app

#code

COPY . .

RUN npm i

#Stage 2

FROM node:21-slim

#setup the working dir

WORKDIR /app


#copy the above stage as compressed
COPY --from=Backend-Build /app .

COPY .env.sample .env

#port
EXPOSE 5000


#App
CMD ["npm", "start"]

