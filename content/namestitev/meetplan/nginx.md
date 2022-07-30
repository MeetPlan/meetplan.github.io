---
title: NGINX konfiguracija
---

Odprite datoteko `default.conf` z `nano` urejevalnikom besedil - `nano default.conf`.

Zamenjajte VSE omembe `example.com` s svojo poddomeno, v mojemu primeru je to `meetplan.meetplan.ml`.

Morale bi biti 4 vrstice, ki vsebujejo to domeno, od tega dve vrstici `server_name`, ena `ssl_certificate` vrstica in ena `ssl_certificate_key` vrstica.

Končna konfiguracija bi morala izgledati nekako tako:
```nginx
server {
    listen 80;
    listen [::]:80;
    server_name meetplan.meetplan.ml;

    location ~ /.well-known/acme-challenge {
        allow all;
        root /var/www/html;
    }

    location / {
        rewrite ^ https://$host$request_uri? permanent;
    }
}

server {
   listen 443 ssl http2;
   listen [::]:443 ssl http2;
   server_name meetplan.meetplan.ml;

   server_tokens off;

   ssl_certificate /etc/letsencrypt/live/meetplan.meetplan.ml/fullchain.pem;
   ssl_certificate_key /etc/letsencrypt/live/meetplan.meetplan.ml/privkey.pem;

   ssl_buffer_size 8k;

   ssl_dhparam /etc/ssl/certs/dhparam-2048.pem;

   ssl_protocols TLSv1.2 TLSv1.1 TLSv1;
   ssl_prefer_server_ciphers on;

   ssl_ciphers ECDH+AESGCM:ECDH+AES256:ECDH+AES128:DH+3DES:!ADH:!AECDH:!MD5;

   ssl_ecdh_curve secp384r1;
   ssl_session_tickets off;

   ssl_stapling on;
   ssl_stapling_verify on;
   resolver 8.8.8.8;

   client_max_body_size 250M;

   location / {
      proxy_pass http://frontend:3000;
   }

   location /api/ {
      proxy_pass http://backend/;
   }

   root /var/www/html;
   index index.html index.htm index.nginx-debian.html;
}
```

Ko ste končali z urejanje, shranite datoteko z CTRL+O -> Enter -> CTRL+X pritiski na tipkovnici.

Nadaljujte na zadnji korak :tada:.
