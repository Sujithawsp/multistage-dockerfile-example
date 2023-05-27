FROM ubuntu
MAINTAINER name mail
RUN apt update -y && apt install curl -y && apt install openjdk-11-jre -y
RUN curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key |  tee \
  /usr/share/keyrings/jenkins-keyring.asc > /dev/null
RUN echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \
  https://pkg.jenkins.io/debian-stable binary/ |  tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
RUN apt update -y && apt install jenkins -y
RUN systemctl enable jenkins
COPY test.txt /home
ADD https://dlcdn.apache.org/tomcat/tomcat-11/v11.0.0-M6/bin/apache-tomcat-11.0.0-M6.zip /home
EXPOSE 8080
CMD ["/usr/bin/jenkins", "run"]
