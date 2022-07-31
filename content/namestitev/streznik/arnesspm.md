---
title: Arnes SPM
---

{{< hint type=note title=Obvestilo >}}
Arnes SPM je priporočena storitev, saj je vse gosteno na Arnesovih strežnikih in strežniki nikoli ne potečejo.
{{< /hint >}}

Najlepša hvala [Arnesu](https://www.arnes.si) za dostop do te storitve. Brez dostopa ne bi moral narediti tega priročnika. Hvala :pray:.

{{< toc >}}

## Prijava v Arnes SPM
Odprite [to](https://spm.arnes.si) povezavo in se prijavite z AAI prijavo.

![image](https://user-images.githubusercontent.com/52399966/182016629-96384325-1298-46e4-97bb-85782cda88ee.png)

## Ustvarjanje nove virtualne mašine
Ko se prijavite, bi se moralo prikazati nekaj takega:
![image](https://user-images.githubusercontent.com/52399966/182017039-cfb28358-2265-45cc-9dbd-0ae3ca473bcb.png)

Preprosto kliknite "Nov virtualni strežnik".

{{< hint type=tip title=Nasvet >}}
Virtualni strežnik, virtualna mašina, VPS so popolnoma isti izrazi z istim pomenom. Naj vas ne zmoti, če kje uporabljam določen izraz, kje drugje pa kak drug izraz.
{{< /hint >}}

### Izbiranje kvote
Izberite kvoto - v mojemu primeru je to "Projekt Meetplan", ampak za vaš strežnik bo to verjetno "Osnovna šola __________" ipd.
![image](https://user-images.githubusercontent.com/52399966/182017164-72e33ae7-4059-4394-9f29-7838a14492af.png)

### Izbiranje predloge
Predloga je zelo pomembna. Izbrali bomo kar predpripravljeno predlogo, priporočam Ubuntu 20.04 LTS (oz. katerakoli novejša verzija Ubuntuja).
![image](https://user-images.githubusercontent.com/52399966/182017369-7aee85a2-48f5-41d8-a32f-312b5252e2c8.png)

{{< hint type=important title=Pomembno >}}
Ubuntu 20.04 LTS **NI** Windows ali kakorkoli podoben Windowsu. Ubuntu je t.i. Linux sistem, ki temelji na Unix sistemih. MacOS je Unix sistem, zato so Linux komande zelo podobne MacOS komandam v terminalu/konzoli.
{{< /hint >}}

{{< hint type=important title=Pomembno >}}
Ubuntu 20.04 LTS **NI** sistem z grafičnim uporabniškim vmesnikom. To pomeni, da ta sistem uporablja samo in izključno konzolo oz. terminal.
{{< /hint >}}

### Izbiranje paketa
Koliko strežniških storitev želite pokloniti MeetPlanu? Priporočljiva vrednost je 2GB pomnilnika, 2 CPE-ja, to je v našem primeru "Srednji", ampak bodo čisto vsi paketi delali z MeetPlan sistemom brez problema.

{{< hint type=tip title=Nasvet >}}
Če veste, da ne boste potrebovali več kot enega strežnika, tj. boste imeli samo MeetPlan, se vedno priporoča izbrati 4GB pomnilnika in 4 procesorske enote, ampak tako ne boste morali več ustvariti novih virtualnih naprav, saj ste dosegli kvoto. Če niste prepričani ali pa veste, da boste imeli več strežnikov, se izbere toliko strežniških storitev, da boste lahko vse strežnike stlačili v kvoto.
{{< /hint >}}

{{< hint type=tip title=Nasvet >}}
Kadarkoli lahko spremenite paket, torej niste obtičali s to izbiro.
{{< /hint >}}

Jaz bom za MeetPlan izbral srednji paket.

### Poimenovanje strežnika
Na tem koraku samo preimenujete strežnik. Jaz sem ga preimenoval v "MeetPlan".
![image](https://user-images.githubusercontent.com/52399966/182017703-c5ac4d70-0bb5-4a9f-97fb-04d9755fdb8d.png)

Nato samo kliknete na "Ustvari" in počakajte, da se status strežnika spremeni v "Strežnik je ugasnjen", nakar bomo nadaljevali s priklopom na strežnik.

## Priklop na strežnik
### Prižig strežnika in pridobivanje IP naslova strežnika
Prvo kot prvo se je treba prepričati, da je strežnik prižgan. Če ni, lahko to uredimo preko Arnesove spletne strani.
![image](https://user-images.githubusercontent.com/52399966/182017954-5748344e-8671-4cfe-8117-5fd0ca5052f8.png)

Izberite svoj strežnik (v mojemu primeru "MeetPlan").

![image](https://user-images.githubusercontent.com/52399966/182018030-d524435f-1fc4-472e-b975-bebd068c6eb5.png)

{{< hint type=important title=Pomembno >}}
Prepričajte se, da je izbrana možnost "Zaženi iz diska", drugače se operacijski sistem ne bo zagnal.
{{< /hint >}}

Kliknite gumb "Zaženi" in počakajte, da se status strežnika spremeni v "Strežnik je zagnan". Možno je, da se bo strežnik večkrat ponovno zagnal, zato ne nadaljujte do nalednjega koraka, dokler se status ne neha spreminjati (čakajte kakih 5 minut).

Na strežnik se priklopite s konzolo. (Gumb na desni strani)

Odpreti bi se vam moralo novo okno, v katerem bi vas moralo pozvati za prijavo. Preprosto vpišite `root` in kliknite ENTER (na tipkovnici). Naslednje, kar bi se vam moralo prikazati je tole:
![image](https://user-images.githubusercontent.com/52399966/182018734-c7523128-41b5-4b55-a130-f11b1cee04e6.png)
Pozvalo vas bo za novo geslo. Izmislite si čim boljšega (uporabljajte tudi simbole, velike, male črke, številke) in čim daljšega.

{{< hint type=important title=Pomembno >}}
VNC konzola ne sledi pravilno vsem vašim znakom - nekateri simboli se ne prikažejo pravilno. Priporoča se, da se za začetek ***NE*** naredi gesla s simboli, in se ga kasneje preko PuTTY-ja spremeni z ukazom `passwd`.
{{< /hint >}}

Sedaj bi vas moralo pozvati, da se ponovno prijavite.
![image](https://user-images.githubusercontent.com/52399966/182018945-50382302-0856-4bb3-8a14-e9b6d6664af0.png)

Mi tega ne bomo naredili, zato bomo samo zaprli to okno in šli nazaj na Arnes SPM portal in osvežili stran.

Ko boste osvežili stran, se vam bo prikazal IP strežnika.
![image](https://user-images.githubusercontent.com/52399966/182018974-895aad07-025a-42a4-bc6b-47945938c02c.png)

### Namestitev PuTTY programa in priklop na strežnik
Prenesite in namestite [PuTTY](https://www.putty.org/). S tem programom se bomo priklapljali na strežnik.

![image](https://user-images.githubusercontent.com/52399966/182019048-9e5496dd-391a-4b87-9276-d1d86e24eb66.png)

V okvir "Host Name (or IP address)" preprosto vtipkajte svoj IP naslov in kliknite gumb "Open".

Ob prvi prijavi na strežnik se vam bo pokazalo nekaj takega:

![image](https://user-images.githubusercontent.com/52399966/182019108-fdeb81f3-2f60-46cd-b47a-b5019ddc0b63.png)

Samo kliknite "Accept" in nadaljujte.

Prijavite se z uporabniškim imenom `root` in geslom, katerega ste si prej izmislili.
![image](https://user-images.githubusercontent.com/52399966/182019149-a238db30-b396-4158-9234-102e51109336.png)

Sedaj pa lahko nadaljujete na naslednji korak.
