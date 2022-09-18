---
title: Namestitev vsega potrebnega in zagon MeetPlan sistema
---

{{< toc >}}

---

# Avtomatična namestitev MeetPlan sistema
Vpišite naslednji ukaz in ga poženite: `chmod +x setup.sh && ./setup.sh`

Zagnalo bo uradno avtomatsko namestitveno orodje za MeetPlan sistem. Vse kar morate delati, je to, da sledite navodilom, katera se vam sproti izpisujejo.

![image](https://user-images.githubusercontent.com/52399966/190896099-f3b33c71-220f-435b-bb4d-2dd1f43b93d9.png)

# Vzdrževanje strežnika po namestitvi
{{< hint type=important title=Pomembno >}}
Za vse te ukaze morate biti v direktoriju MeetPlanDocker, v katerega lahko greste z ukazom `cd ~/MeetPlanDocker`, če ste sledili navodilom.
{{< /hint >}}

{{< hint type=important title=Pomembno >}}
Kadar govorimo o strežniku v tem delu, v resnici mislimo MeetPlan sistem. (Dejanski) strežnik se v resnici ne bo ugasnil, če boste pognali ukaz za ugašanje (spodaj).
{{< /hint >}}

## Razni ukazi
- Ukaz za ponoven zagon strežnika: `./prodrestart.sh`
- Ukaz za pridobitev strežniških izpisov: `sudo docker-compose logs`

## Drugi (povečini nepotrebni) ukazi
- Ukaz za ugašanje strežnika `sudo docker-compose down`
- Ukaz za zagon strežnika v ospredju: `sudo docker-compose up`
- Ukaz za zagon strežnika v ozadju: `sudo docker-compose up -d`

# Zaključne besede
Zahvaljujemo se vam za izbiro MeetPlan sistema in vam želimo čim boljšo izkušnjo. Če naletite na kakršnekoli probleme, prosimo kontaktirajte razvijalce sistema v [GitHub repozitoriju](https://github.com/MeetPlan/MeetPlanFrontend/issues). Z veseljem vam bomo pomagali.

