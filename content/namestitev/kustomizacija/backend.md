---
title: Kustomizacija zalednega dela (backenda)
---

{{< hint type=note title=Obvestilo >}}
Ta del ni obvezen, ampak je priporočljiv, če želite vgraditi svoje šolske logotipe v MeetPlan sistem.
{{< /hint >}}
{{< hint type=important title=Pomembno >}}
Za ta del je potrebno, da imate GitHub račun.
{{< /hint >}}

{{< toc >}}

## Kopiranje repozitorijev na svoj GitHub račun (forkanje)
{{< hint type=important title=Pomembno >}}
GitHub Packages in GitHub Actions tokeni so narejeni tako dobro, da [ne dovolijo dostopa forkanim repozitorijem](https://docs.github.com/en/actions/security-guides/automatic-token-authentication#permissions-for-the-github_token). Namesto tega, moramo uporabljati (mučen) način z uporabo Gita, ampak ne skrbite - vsi ukazi bodo ustrezno obrazloženi.
{{< /hint >}}

Prvo kot prvo, pojdite do plus ikonice v zgornjem desnem kotu. Kliknite jo in izberite "New repository". Moralo bi vas popeljati do naslednje spletne strani:
![image](https://user-images.githubusercontent.com/52399966/167313596-f55b0afb-bb90-40fc-a5fa-cf1806f8e79c.png)

Poimenujte repozitorij "MeetPlanBackend" in mu dajte poljuben opis. Ne inicializirajte česarkoli - brez README-ja, brez gitignore datoteke in brez licence. Repozitorij je lahko zaseben, če želite, ampak GitHub bo v tem primeru omejeval kvoto, kar pa ni tako problematično za zaledni del (backend).

Kliknite "Create repository", nakar bi se moralo prikazati naslednje.
![image](https://user-images.githubusercontent.com/52399966/167313685-35877891-a874-40ac-8b34-f849a5c5e2d6.png)

Pojdite na nastavitve repozitorija, do "Actions" dela in izberite "General". Podrsajte do nastavitve z imenom "Workflow permissions", nakar izberite "Read and write permissions" namesto "Read repository contents permission" in kliknite gumb "Save". Sedaj ste uredili avtomatično grajenje aplikacije in Docker kontejnerjev v GitHub Container Registry.

[Namestite Git](https://git-scm.com/downloads) na vaš sistem. Ne pozabite ga dodati v PATH vrednost, če vas namestitveni program vpraša za to.

Sedaj bomo klonirali MeetPlanovo kodo. Odpreti morate terminal, da lahko tipkate te komande (`cmd` ali `PowerShell` na Windowsu).
```sh
git clone https://github.com/MeetPlan/MeetPlanBackend
```

Premaknimo se v direktorij:
```sh
cd MeetPlanBackend
```

Dodajte svoj URL do ***SVOJEGA*** repozitorija kot remote:
```sh
git remote add myfork <moj URL do repozitorija>
```
V mojemu primeru je to:
```sh
git remote add myfork https://github.com/mytja/MeetPlanBackend
```

Sedaj pa dajmo vse objaviti.
```sh
git push myfork
```

## Kustomizacija zalednega dela z novimi slikami in logotipi
MeetPlan sistem uporablja svoje logotipe namesto šolskih logotipov. Lahko spremenite te logotipe za čim boljšo uporabniško izkušnjo.

Pojdite na "Code" sekcijo na vašem repozitoriju
![image](https://user-images.githubusercontent.com/52399966/167299972-40437c65-1a72-4798-a042-d6af7cadb55a.png)
*To je stara slika, pri kateri nisem sledil prejšnjim korakom, zato je uporabniški vmesnik čisto malo drugačen, ampak princip ostane enak*

Sedaj kliknite `.` (piko na tipkovnici) kjerkoli na spletni strani. Morali bi priti v spletno instanco urejevalnika besedil Visual Studio Code.

Odprite `icons` mapo v navigatorju (na levi strani). Ponovno naložite vse datoteke s svojimi s tem da jih povlečete (iz lokalnega raziskovalca) v `icons` mapo v Visual Studio Code oknu. Prepričajte se, da ste zamenjali vse stare datoteke.
Imena datotek ***MORAJO*** biti enaka tistim v `icons` mapi/direktoriju. MeetPlanov logotip navadno pomeni šolski logotip, "banner" pa mora biti zamenjan s šolskim "bannerjem".

Ko ste enkrat vse naložili, bi morale datoteke biti zelene.

![image](https://user-images.githubusercontent.com/52399966/167306191-eff9ed28-e7d9-4770-9e6a-c5dae52eac4b.png)

Kliknite na gumb, ki ima dvojko na moji sliki. Pravimo mu tudi "Git gumb".

Morali bi videti nekaj takega

![image](https://user-images.githubusercontent.com/52399966/167306268-120023d5-58de-4964-9c68-ad35b8a9fa2e.png)

Pojdite čez del, na katerem piše "Changes". Videli boste dva nova gumbka - eden je "Discard all changes", medtem ko je drugi "Stage all changes". Kliknite na "Stage all changes" gumb. Sedaj ste stagali datoteke.

![image](https://user-images.githubusercontent.com/52399966/167306379-f8861bfe-0e52-4c2a-97f8-9a4a5c010e6e.png)

Vpišite poljubno sporočilo, recimo `zamenjal stare logotipe z novimi` in kliknimo gumb z kljukico zgoraj (če greste čez ta gumb, bi moralo pisati "Commit and Push").

![image](https://user-images.githubusercontent.com/52399966/167306437-40123df4-9db7-466b-870b-9397396cf048.png)

Čestitke. Uspešno ste objavili spremembe.

Pojdite nazaj na repozitorij. Kliknite na gumb "Actions", kjer bi morali videti akcijo v poteku. Počakajte približno pet minut, nakar bi morali videti zeleno kljukico.
![image](https://user-images.githubusercontent.com/52399966/167306504-26877085-35e4-4f5a-9039-af9f27f20672.png)
*To je stara slika, pri kateri nisem sledil prejšnjim korakom, zato je uporabniški vmesnik čisto malo drugačen, ampak princip ostane enak. GitHub Akcija je v poteku - počakajte, dokler se ne pojavi zelena kljukica*

Sedaj lahko preidete na naslednji korak.
