FROM ubuntu:20.04
#added the ENV debian frontend to resolve the error that stops the build- showing error- debconf: unable to initialize frontend: Dialog 
ENV DEBIAN_FRONTEND=noninteractive
#RUN apt-get -y update \
# install required tools
#&& apt-get install dialog apt-utils -y && apt-get install maven git -y && apt-get install yarn -y
RUN apt-get update && apt-get upgrade -y && \
    apt-get install -y nodejs \
    npm 
#returning the DEBIAN_FRONTEND to its default value
#ENV DEBIAN_FRONTEND=newt
#copy the entire project
#RUN git clone https://github.com/ndiaye-ibrahim/ibmaltc
#WORKDIR /doodlestudent/api
#RUN mvn quarkus:add-extension -Dextensions=quarkus-resteasy-jsonb
#compile the opencv project 
#RUN  mvn package && ./mvnw install && ./mvnw compile quarkus:dev  
#test the built and compiled project, run the application
#CMD ["java", "-Djava.library.path=target/lib", "-jar", "target/code-with-quarkus-1.0.0-SNAPSHOT-runner.jar"]

#WORKDIR /doodlestudent/front
#CMD ["yarn", "start"]

#EXPOSE 8080


#FROM node:10

# Create app directory
WORKDIR /app

# Install app dependencies
# A wildcard is used to ensure both package.json AND package-lock.json are copied
# where available (npm@5+)
COPY package*.json /app/

RUN npm install
# If you are building your code for production
# RUN npm ci --only=production

# Bundle app source
COPY . /app

EXPOSE 8080
CMD [ "npm", "start" ]
