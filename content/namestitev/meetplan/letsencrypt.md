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

Spremenite `<yourusername>` v Linux sistemsko uporabniško ime (če uporabljate ~okeanos, je `user` (za Ubuntu) ali `debian` (za Debian)).

Če ste spreminjali (modificirali/kustomizirali) backend (zaledni del), pojdite malo bolj navzgor (proti začetku datoteke), dokler ne najdete nečesa takega, drugače pa pojdite na naslednji odstavek (To je to):
```yml
  backend:
    image: ghcr.io/meetplan/backend
    volumes:
      - ./config.json:/app/config.json
```
Spremenite `ghcr.io/meetplan/backend` v `ghcr.io/<uporabniško ime na githubu>/backend`, v mojemu primeru sem spremenil v `ghcr.io/mytja/backend`.



To je to. Shranite datoteko (s prej omenjenim zaporedjem).

{{< hint type=tip title=Nasvet >}}
Let's Encrypt ni edina možna izbira za SSL certifikate, ampak je edina uradno podprta s strani MeetPlan razvijalcev. Če ne boste uporabljali Let's Encrypt certifikatov, ne morete računati na podporo z (možnimi) nadaljnimi produkti MeetPlan razvijalcev (MeetPlan sistem bo še vedno podprt, tudi z drugimi certifikati).
{{< /hint >}}

Sedaj, vse kar potrebujete, je izvesti naslednje ukaze. Ti ukazi bodo namestili Let's Encrypt SSL certifikat (kateri so popolnoma zastonj, ampak lahko tudi donirate - [Let's Encrypt donation link](https://letsencrypt.org/donate), [EFF donation link](https://eff.org/donate-le)).
```sh
chmod +x getdhparam.sh
chmod +x initcert.sh
chmod +x initschoolcert.sh
./getdhparam.sh
./initcert.sh
./initschoolcert.sh
sudo docker-compose down
```

Ko ste to opravili, lahko nadaljujete z naslednjim korakom.
