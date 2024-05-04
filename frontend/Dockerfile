#------------------------------------STAGE 1------------------------------------------------------


FROM node:21-alpine AS Frontend-build

#setup the working dir to /app

WORKDIR /app

# copy the package.json and package-lock.json for dependency  installation

COPY package*.json ./

#install dependency

RUN npm install

#copy the rest of the application code

COPY . .

#------------------------------------STAGE 2------------------------------------------------------

FROM node:21-alpine-slim

#setup the working dir to /app

WORKDIR /app

#copy build assets and dependency from frontend builder

COPY --from=Frontend-Build /app .


#copy the env sample to env local

COPY .env.sample .env.local

#Port for node.js application

EXPOSE 5173

#define the default command from repositroy to run the application

CMD ["npm","run","dev","--","--host"]


