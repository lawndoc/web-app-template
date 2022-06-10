FROM nginx:stable

# DEFAULT ARGS that can be changed
ARG DOMAIN="example.com"

# set environment variables for site config generation
ENV DOMAIN=$DOMAIN
ENV DOLLAR='$'

# generate secure diffie-hellman key
RUN openssl dhparam -out /etc/nginx/dhparam.pem 4096

COPY nginx.conf /etc/nginx/nginx.conf
COPY nginxconfig.io/ /etc/nginx/nginxconfig.io/

# generate site config
COPY sites-available/example.com.conf /etc/nginx/sites-available/${DOMAIN}.conf.template
RUN mkdir /etc/nginx/sites-enabled
RUN envsubst < /etc/nginx/sites-available/${DOMAIN}.conf.template > /etc/nginx/sites-available/${DOMAIN}.conf

# enable site
RUN ln -s /etc/nginx/sites-available/${DOMAIN}.conf /etc/nginx/sites-enabled/${DOMAIN}.conf