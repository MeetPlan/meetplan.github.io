---
title: Zagon MeetPlan sistema
---

Zaganjanje je preprosto - potrebujete samo en ukaz. Če se med zagonom javi kakršnakoli napaka, samo prekličite ukaz (z uporabo CTRL+C) in ga ponovno zaženite. Če tudi to ne pomaga, poskusite popolnoma ustaviti vse kontejnerje z `sudo docker-compose down`
```sh
sudo docker-compose up
```

Prvi zagon se mora vedno zgoditi z zgornjim ukazom, ki sproti prikazuje vse izpise. Če bo vse delovalo (tudi če vtipkate poddomeno v brskalnik), pritisnite CTRL+C in počakajte na Dockerja, da ugasne vse kontejnerje, nakar lahko vse zaženete s pravim ukazom, ki bo vse poganjal v ozadju:
```sh
sudo docker-compose up -d
```

Za pogled po vsej dejavnosti vseh kontejnerjev lahko vtipkate tudi ukaz `sudo docker-compose logs`, pogledate vse zagnane kontejnerje s `sudo docker-compose ps` in ugasnete vse kontejnerje z ukazom `sudo docker-compose down`.

Zahvaljujemo se vam za izbiro MeetPlan sistema in vam želimo čim boljšo izkušnjo. Če naletite na kakršnekoli probleme, prosimo kontaktirajte razvijalce sistema v [GitHub repozitoriju](https://github.com/MeetPlan/MeetPlanFrontend/issues). Z veseljem vam bomo pomagali.

