FROM ubuntu

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Europe/Moscow


RUN apt-get update && \
    apt-get install -y --no-install-recommends nginx php-fpm php-mysql php-curl php-gd php-intl php-mbstring php-soap php-xml php-xmlrpc php-zip wget unzip && \
    wget -qO /tmp/latest.zip https://wordpress.org/latest.zip && \
    unzip /tmp/latest.zip -d /var/www/html/ && \
    rm -f /tmp/latest.zip && \
    chown -R www-data:www-data /var/www/html/wordpress && \
    chmod -R 755 /var/www/html/wordpress && \
    rm -rf /var/lib/apt/lists/*

COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]