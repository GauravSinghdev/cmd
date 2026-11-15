## *__Install NGINX__*
sudo apt update
sudo apt install nginx


## *__edit the NGINX file__*

sudo rm sudo vi /etc/nginx/nginx.conf
sudo vi /etc/nginx/nginx.conf


    events {}

    http {
    map $http_upgrade $connection_upgrade {
        default upgrade;
        ''      close;
    }

    server {
        listen 80;
        server_name test.codewithkara.com;

        location / {
            proxy_pass http://127.0.0.1:3000;
            proxy_http_version 1.1;

            proxy_set_header Host $host;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection $connection_upgrade;
        }
    }

    server {
        listen 80;
        server_name prac.codewithkara.com;

        location / {
            proxy_pass http://127.0.0.1:3001;
            proxy_http_version 1.1;

            proxy_set_header Host $host;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection $connection_upgrade;
        }
    }
}


## *__Reload NGINX__*

sudo nginx -s reload