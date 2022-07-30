---
title: Vzpostavitev domene in poddomene
---

V tem vodiču predvidevamo, da že imate domeno. Če ne, jo lahko dobite zastonj na [dot.tk](https://dot.tk), oz. od [Arnesa](http://www.arnes.si/storitve/splet-posta-strezniki/registracija-si-domene/), če ste slovenska šola oz. organizacija znotraj AAI omrežja. Odprite konfiguracijo za svojo domeno. Pojdite na "DNS management" oz. nekaj podobnega. Na dot.tk-ju izgleda nekako tako:

![image](https://user-images.githubusercontent.com/52399966/167690989-751cb5f1-568a-4079-8d92-51b0bb3206c1.png)

Pojdite na "Add records" sekcijo. Vpišite ime poddomene, na primer "meetplan" (če to vpišete, bo nastala naslednja poddomena: `meetplan.mojadomena.si`, s tem da je `mojadomena.si` ime vaše domene). Nastavite tip DNS zapisa na `A` in `TTL` na `3600`. Cilj/destinacija bi moral biti IP naslov do strežnika. Moja konfiguracija je naslednja:

![image](https://user-images.githubusercontent.com/52399966/167691584-540a5637-de88-4f31-aa11-f268650457a6.png)

Kliknite na shrani spremembe in ***bum***, poddomena je pripravljena. Kar preprosto, a ne?

{{< hint type=important title=Pomembno >}}
Poddomena lahko včasih vzame tudi do 24 ur, da se zapiše v DNS strežnike, čeprav se spremembe dejansko največkrat zgodijo v roku desetih minut. Nujno je biti potrpežljiv.
{{< /hint >}}
