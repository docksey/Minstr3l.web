# How to run this and multiple other sites on the same Ubuntu machine

1. `git clone this repo to /websites/BOD`
2. `docker build -t local-webserver /websites/BOD`
3. `docker network create nginx-proxy`
4. `docker run -d -p 80:80 --name nginx-proxy --net nginx-proxy -v /var/run/docker.sock:/tmp/docker.sock jwilder/nginx-proxy`
5. `docker run -d --name bod --expose 80 -v /websites/BOD/www:/var/www/html --net nginx-proxy -e VIRTUAL_HOST=butterfliesofdeath.com local-webserver`