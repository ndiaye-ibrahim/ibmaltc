FROM ubuntu
#WORKDIR /app

ENV DEBIAN_FRONTEND=noninteractive
COPY . .

#RUN apt-get -y install required tools
#&& apt-get install dialog apt-utils -y && apt-get install maven git -y && apt-get install npm -y
#returning the DEB
RUN apt-get update && apt-get install --no-install-recommends -y\
	openjdk-11-jdk && apt-get install dialog apt-utils -y && apt-get install maven git -y && apt-get install npm -y
RUN git clone https://github.com/ndiaye-ibrahim/ibmaltc
WORKDIR /ibmaltc/api
RUN mvn package -Dmaven.test.skip=true 
EXPOSE 8080
CMD ["java","-jar","target/tlcdemoApp-1.0.0-SNAPSHOT-runner.jar","-Dsurefire.suiteXmlFiles=/app/abc.xml"]
