---
title: Proton modul
---

Proton je modul, ki šolam olajša delo z urniki in nadomeščanji, saj avtomatično predlaga najboljše možne rešitve za te probleme.

{{< hint type=note title="Zabavno dejstvo" >}}
Glavno in uradno ime temu modulu je Proton. Proton modul ima poleg "Proton" imena še eno drugo uradno (manj pogosto) ime, in sicer "Guinea pig" modul. Če vas zanima, kako smo prišli do tega imena - no, izkaže se, da ima avtor MeetPlan sistema zelo rad morske prašičke.
{{< /hint >}}

<!--
{{< hint type=caution title=Pozor >}}
Ta del navodil je trenutno v pisanju in vsebuje še neobjavljene funkcije. ***NE ZANAŠAJTE SE NA TA DEL NAVODIL***.
{{< /hint >}}
-->

{{< hint type=note title=Obvestilo >}}
Ta del navodil je na voljo samo specifičnim vlogam v sistemu. O tem se pozanimajte v delu o [pravicah v MeetPlan sistemu](/uporaba/pravice).
{{< /hint >}}

{{< toc >}}

## Funkcije Proton modula
Proton ima za zdaj dve funkciji:
- Avtomatično predlaganje najbolj optimalnih učiteljev za nadomeščanja (v Beta fazi)
- Avtomatično sestavljanje urnikov (v pozni Alfa fazi - to pomeni, da še ni objavljeno, ampak bo kmalu)

## Uporaba Proton modula za nadomeščanje
Pojdite na srečanje, na katerega želite nastaviti nadomeščanje.

![image](https://user-images.githubusercontent.com/52399966/186739373-8e4b82f5-f3b3-412c-ad37-156ff8fa2168.png)

Spodaj boste videli stikalo "Je nadomeščanje". Obkljukajte to, nakar se vam bo prikazal seznam oseb, urejen po točkah. Več točk ima oseba, bolj primerno nadomeščanje je. Proton vam hkrati tudi obrazloži vsako izbiro.

## Proton konfiguracija
### Kje lahko najdem Proton modul?
![image](https://user-images.githubusercontent.com/52399966/186736100-8606413a-8914-4568-b4cd-ec69381b5224.png)

### Tipi Proton konfiguracij
Proton konfiguracije so potrebne in zelo pomembne zato, da Proton modul ve, kako naj ustvari urnik - tj. po specifičnih pravilih.

V tem delu vam predstavimo vse možne tipe konfiguracij.

#### Tip 0 - Polni dnevi učitelja na šoli
![image](https://user-images.githubusercontent.com/52399966/186736429-a2b26dc3-4f2b-42e3-a51d-e0ca7b883c57.png)

Če si učitelja delita dve (ali več šol), ali pa preprosto ni zaposlen poln čas na tej šoli, potem lahko uporabite to nastavitev in vpišete dneve, ko je učitelj v celoti na šoli (ne štejejo se dnevi, ko je učitelj na šoli nekaj ur - mora biti prisoten vse ure - za ta namen je na voljo tip 1).

#### Tip 1 - Ure učitelja na šoli
![image](https://user-images.githubusercontent.com/52399966/186737089-f57a2d7e-4edb-48fa-b7d8-ff6223b473f9.png)

Če je učitelj na določene dni samo nekaj ur na šoli, potem se izbere to pravilo. Izbrati morate dneve, ko je učitelj na vaši šoli samo nekaj ur in ure, katere je učitelj na teh dneh na vaši šoli.

#### Tip 2 - Skupina predmetov
![image](https://user-images.githubusercontent.com/52399966/186737427-7a74148f-848a-4987-8638-1536b9b35e31.png)

Skupina predmetov se ustvari, kadar želite, da se določeni predmeti izvajajo na isti čas (npr. heterogene/homogene skupine, ure športne vzgoje ipd.).

Izberite predmete, za katere želite, da se izvajo na isti čas. Vsako skupino morate narediti posebej.

#### Tip 3 - Predmeti pred ali po pouku
![image](https://user-images.githubusercontent.com/52399966/186737917-4e95b630-286e-42f3-a819-3b998f0bd6c3.png)

Izberite predmete, za katere želite, da se izvajajo pred ali po pouku (izbirni predmeti, dopolnilni/dodatni pouk ipd.).

#### Tip 4 - Predmeti z blok urami
![image](https://user-images.githubusercontent.com/52399966/186738147-00b9fb8d-d587-41c4-a78c-d4b12cc1ac75.png)

Izberite predmete, za katere želite, da imate blok ure (zaporedne ure).

### Ustvarjanje Proton konfiguracije
Izberite tip izmed naštetih, nakar sledite navodilom in kliknite "OK", nakar se vam bo to pravilo dodalo.

### Urejanje Proton konfiguracije
Urejanje proton konfiguracije (še) ***NI NA VOLJO***. Če želite Proton konfiguracijo urediti, morate izbrisati tisti del, katerega želite urediti in ga na novo ustvariti.

### Brisanje Proton konfiguracije
![image](https://user-images.githubusercontent.com/52399966/186738407-dea8e753-410d-40b1-9437-3f35b1377555.png)

Preprosto kliknite "Izbriši pravilo" in je pravilo izbrisano.

## Sestavljanje urnika
Urnik se sestavi s klikom gumba "Sestavi urnik".

Bodite potrpežljivi, sestavljanje urnika lahko traja dolgo časa, odvisno od tega, koliko razredov imate.

Generalno velja ta tabela za sestavljanje urnika:
| št. razredov/izmerjen čas sestavljanja urnika [s] | Najmanjši | Največji | Povprečni |
| ------------------------------------------------- | --------- | -------- | --------- |
| En razred                                         | 3         | 17       | 10        |
| Dva razreda                                       | 10        | 95       | 40        |
| Trije razredi                                     | 15        | 300      | 120       |

### Delovanje algoritma
#### Algoritem za sestavljanje urnika
Algoritem je popolnoma naključen, zato potrebuje toliko časa, da se urnik sestavi. Naključni algoritem zagotavlja popolnoma naključne urnike, vsakič ko kliknete "Sestavi urnik".

Urniki, sestavljeni so primerni za praktično vse osnovne šole, kot tudi srednje šole in gimnazije (z nekaj izjemami - npr. popoldanski pouk ni vgrajen, kar pomeni, da ga nekatere šole, kot je npr. Vegova za zdaj ne bodo morale uporabljati).

#### Post procesirna suita
Naš naključni algoritem bolj ali manj nameče učne ure vsepovsod po urniku, kar odpravimo z delom, kateremu pravimo post procesiranje urnika. Ta del skrbi za:
- ni lukenj za učence z uporabo naslednjih metod:
    - polnjenje lukenj z nenormalnimi (bingljajočimi) urami
    - zamenjava lukenj in motečih ur z nenormalnimi urami
    - ...

Ta del je najpomembnejši, saj je od tega odvisno, ali bo urnik prišel dober ali slab (čeprav, če dobi slab urnik že od algoritma za sestavljanje, bo težko kaj popravil).

### Ponavljanje post procesiranje urnika
Urnik včasih ne pride po prvem post procesiranju najlepši. Damo vam možnost ponavljanja post procesiranja urnika z gumbom "Ponovi post-procesiranje urnika".

{{< hint type=tip title=Nasvet >}}
Priporoča se, da poskušate z obemi možnostmi - tj. s hitrim post procesiranjem, kot tudi brez hitrega post procesiranja. Izjemno zaželjeno je, da malo eksperimentirate z generiranjem različnih urnikov in z različnimi opcijami, preden začnete sestavljati pravega ;-)
{{< /hint >}}

### Urnik, sestavljen s Proton modulom ni lep. Kaj lahko naredim?
Ponovite post procesiranje nekajkrat in poglejte, če bo kaj lepši. Če je še vedno luknjast, preprosto kliknite možnost "Ponovno sestavljanje urnika" in se vam bo začel generirati nov urnik.
