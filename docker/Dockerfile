FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p Metamfitamin.com/img && \
    chmod -R 754 /var/www/Metamfitamin.com/ && \
    useradd artem && groupadd marchenkov && usermod -aG marchenkov artem && \
    chown -R artem:marchenkov /var/www/Metamfitamin.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/Metamfitamin.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user artem/g' /etc/nginx/nginx.conf
ADD index.html /var/www/Metamfitamin.com/
ADD img.png /var/www/Metamfitamin.com/img/
CMD ["nginx", "-g", "daemon off;"]