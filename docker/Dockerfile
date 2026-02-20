FROM jwilder/docker-gen:latest
COPY nginx.tmpl /etc/docker-gen/templates/nginx.tmpl
COPY dhparam.pem /etc/nginx/dhparam/dhparam.pem
COPY urllo.test.crt /etc/nginx/certs/urllo.test.crt
COPY urllo.test.key /etc/nginx/certs/urllo.test.key
COPY easyredir.test.crt /etc/nginx/certs/easyredir.test.crt
COPY easyredir.test.key /etc/nginx/certs/easyredir.test.key
