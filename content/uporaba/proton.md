---
title: Proton modul
---

Proton je modul, ki šolam olajša delo z urniki in nadomeščanji, saj avtomatično predlaga najboljše možne rešitve za te probleme.

{{< hint type=note title="Zabavno dejstvo" >}}
Glavno in uradno ime temu modulu je Proton. Proton modul ima poleg "Proton" imena še eno drugo uradno (manj pogosto) ime, in sicer "Guinea pig" modul. Če vas zanima, kako smo prišli do tega imena - no, izkaže se, da ima avtor MeetPlan sistema zelo rad morske prašičke.
{{< /hint >}}

{{< hint type=caution title=Pozor >}}
Ta del navodil je trenutno v pisanju in vsebuje še neobjavljene funkcije. ***NE ZANAŠAJTE SE NA TA DEL NAVODIL***.
{{< /hint >}}

{{< toc >}}

## Funkcije Proton modula
Proton ima za zdaj dve funkciji:
- Avtomatično predlaganje najbolj optimalnih učiteljev za nadomeščanja (v Beta fazi)
- Avtomatično sestavljanje urnikov (v pozni Alfa fazi - to pomeni, da še ni objavljeno, ampak bo kmalu)

## Uporaba Proton modula za nadomeščanje


## Proton konfiguracija
### Tipi Proton konfiguracij
#### Tip 0 - 
#### Tip 1 - 
#### Tip 2 - 
#### Tip 3 - 
#### Tip 4 - 

### Ustvarjanje Proton konfiguracije

### Urejanje Proton konfiguracije
Urejanje proton konfiguracije (še) ***NI NA VOLJO***. Če želite Proton konfiguracijo urediti, morate izbrisati tisti del, katerega želite urediti in ga na novo ustvariti.

### Brisanje Proton konfiguracije




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

### Urnik, sestavljen s Proton modulom ni lep. Kaj lahko naredim?
Ponovite post procesiranje nekajkrat in poglejte, če bo kaj lepši. Če je še vedno luknjast, preprosto kliknite možnost "Ponovno sestavljanje urnika" in se vam bo začel generirati nov urnik.
