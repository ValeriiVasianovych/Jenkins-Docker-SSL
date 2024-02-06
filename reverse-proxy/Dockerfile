FROM nginx:latest

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
        net-tools \
        neovim \
    && apt-get autoremove -y \
    && apt-get clean \
    && apt-get install certbot -y \
    && apt-get install python3-certbot-nginx -y \
    && rm -rf /etc/nginx/conf.d/default.conf \
    && rm -rf /var/lib/apt/lists/*

COPY config/jenkins.conf /etc/nginx/conf.d/
COPY nginx.conf /etc/nginx/nginx.conf

EXPOSE 80 443 22

CMD ["nginx", "-g", "daemon off;"]