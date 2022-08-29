FROM ubuntu:latest
LABEL "Author"="Samson"
LABEL "Project"="nano"
ENV DEBIAN FRONTEND=noninteractive
RUN apt update && apt install git -y
RUN apt install apache2 -y
CMD ["/usr/sbin/apache2ctl","-D", "FOREGROUND"]
EXPOSE 80
WORKDIR /var/www/html
VOLUME /var/log/apache2
ADD nano.tar.gz /var/www/html
# COPY nano.tar.gz /var/www/html



