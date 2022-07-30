---
title: Pridobivanje SSL certifikata od Let's Encrypt organizacije
---

Vsaka spletna stran potrebuje SSL certifikat za čim večjo varnost, saj tako napadalci ne bodo mogli prestreči podatkov. Z SSL certifikatom se HTTP nadgradi v HTTPS.

Malo bomo morali spremeniti določene Docker konfiguracijske datoteke. Prvo bomo odprli `initcert.sh` datoteko z `nano` urejevalnikom besedil. Uporabite naslednji ukaz: `nano initcert.sh`.

{{< hint type=tip title=Nasvet >}}
`nano` je terminalski urejevalnik besedil. Po njem se ne premikate z miško, temveč s puščicami na tipkovnici.
{{< /hint >}}

Pojdite do vrstice 3. Spremenite elektronski naslov (`test@example.org`) v svoj zasebni/službeni/šolski elektronski naslov in domeno (`example.org`) v vašo poddomeno, katera je v mojemu primeru `meetplan.meetplan.ml`.

{{< hint type=important title=Pomembno >}}
To mora biti izpolnjeno pravilno, drugače generacija SSL certifikatov ne bo delovala
{{< /hint >}}

Shranite datoteko in spremembe z naslednjim zaporedjem ukazov: CTRL+O -> Enter -> CTRL+X

Pa odprimo `docker-compose.yml` datoteko. Uporabimo nano, da jo odpremo: `nano docker-compose.yml`.

Pojdite na dno datoteke, kjer bi morali videti nekaj takega:
```yml
  dhparam:
    driver: local
    driver_opts:
      type: none
      device: /home/<yourusername>/MeetPlanDocker/dhparam/
      o: bind
```

Change `<yourusername>` to your Linux system username (if you are using Okeanos, it's either `user` (for Ubuntu) or `debian` (for Debian)).

Head a little bit up in the file until you find something like this:
https://github.com/MeetPlan/MeetPlanDocker/blob/cf005a3599dc53808635958373df5e6003766eaf/docker-compose.yml#L42-L45

You have to change the `ghcr.io/meetplan/backend` to `ghcr.io/<your github fork username>/backend`, in my case it's `ghcr.io/mytja/backend`.

That's it. Write out the file as described a few lines above and you are good to go.

Now, all you have to do is to execute the following. These commands will install Let's Encrypt SSL certificates (which are fully free of charge, but you can donate anytime - [Let's Encrypt donation link](https://letsencrypt.org/donate), [EFF donation link](https://eff.org/donate-le)) and all the necessary dependencies for it.
```sh
chmod +x getdhparam.sh
chmod +x initcert.sh
./getdhparam.sh
./initcert.sh
sudo docker-compose down
```

##### 3.2.6. Change nginx configuration.
Open the file `default.conf` using `nano` - `nano default.conf`.

Replace ALL the mentions of `example.com` with your domain name, for example `meetplan.meetplan.ml`.

There should be 4 lines that contain this domain name, two `server_name` lines, one `ssl_certificate` line and one `ssl_certificate_key` line.

Final config should be something like this:
```
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

Once you are done, write out file using CTRL+O -> Enter -> CTRL+X keystrokes.

##### 3.2.7. Running the Docker containers.
Running is as simple as one command. If there are any errors, just exit the command (using CTRL+C) and rerun it. If that doesn't help, try to shutdown Docker containers using `sudo docker-compose down`
```sh
sudo docker-compose up
```

First run should be with above command (test run command). Once everything is working, press CTRL+C and wait for Docker to shut down all the containers. After that, you can truly deploy everything. Everything will be running in background using this command:
```sh
sudo docker-compose up -d
```

Now, you can view the logs using `sudo docker-compose logs`, view running containers using `sudo docker-compose ps` and shut down the containers using `sudo docker-compose down`.


Thank you for selecting MeetPlan and wish you a very good experience with it. If you have any problems, please contact me in the [GitHub repo](https://github.com/MeetPlan/MeetPlanDocker) in the "Issues" section. I will be happy to assist.
