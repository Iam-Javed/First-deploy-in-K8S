FROM ubuntu:latest
LABEL Author="Javed"
LABEL Project="website"
LABEL version="1.0"
ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && \
    apt-get install -y apache2 git && \
    rm -rf /var/lib/apt/lists/*
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
WORKDIR /var/www/html/
EXPOSE 80
VOLUME ["/var/log/apache2/"]
ADD webimg12.tar.gz /var/www/html/

