FROM ubuntu:20.04 as build-step
#added the ENV debian frontend to resolve the error that stops the build- showing error- debconf: unable to initialize frontend: Dialog 
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y nodejs \
    npm 

WORKDIR /app
COPY package*.json /app/
RUN npm install
COPY . /app
RUN npm run build -- --outputPath=./dist/out
FROM bunkerity/bunkerized-nginx as prod

#WORKDIR /app

COPY --from=build-step /app/dist/out/ /www/
ADD api.conf /server-confs/api.conf
ADD pad.conf /server-confs/pad.conf
ADD myadmin.conf /server-confs/api.conf

EXPOSE 8080
CMD [ "npm", "start" ]
