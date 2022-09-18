---
title: Vzpostavitev domene in poddomene
---

V tem vodiču predvidevamo, da že imate domeno. Če ne, jo lahko dobite brezplačno na [dot.tk](https://dot.tk), oz. od [Arnesa](http://www.arnes.si/storitve/splet-posta-strezniki/registracija-si-domene/), če ste slovenska šola oz. organizacija znotraj AAI omrežja. Odprite konfiguracijo za svojo domeno. Pojdite na "Urejanje DNS zapisov" oz. nekaj podobnega. Na Neoservu izgleda nekako tako:

![image](https://user-images.githubusercontent.com/52399966/190896740-2caa5612-cd4c-45c2-8be7-e69db016b201.png)

Kliknite na "Dodaj DNS zapis" sekcijo. Vpišite ime poddomene, na primer "demo" (če to vpišete, bo nastala naslednja poddomena: `demo.mojadomena.si`, s tem da je `mojadomena.si` ime vaše domene). Nastavite tip DNS zapisa na `A` in `TTL` na `3600`. Cilj/destinacija bi moral biti IP naslov do strežnika. Moja konfiguracija je naslednja:

![image](https://user-images.githubusercontent.com/52399966/190896633-69691760-23f4-4871-82eb-2708e352d8b7.png)

Kliknite na "Dodaj" in ***bum***, poddomena je pripravljena. Kar preprosto, a ne?

{{< hint type=important title=Pomembno >}}
Poddomena lahko včasih vzame tudi do 24 ur, da se zapiše v DNS strežnike, čeprav se spremembe dejansko največkrat zgodijo v roku desetih minut. Ključno je biti potrpežljiv.
{{< /hint >}}
