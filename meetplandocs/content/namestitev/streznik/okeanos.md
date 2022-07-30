---
title: ~okeanos global
---

V tem delu se boste naučili, kako se ustvari virtualno mašino (glej tudi "virtualni strežnik" oz. "strežnik") s storitvijo ~okeanos global, ki je na voljo vsem uporabnikom Arnes AAI storitev.

{{< toc >}}

## Prijava z Arnes AAI računom
Pojdite na [Arnesovo AAI spletno stran](https://aai.arnes.si) in se tam prijavite s svojim Arnes AAI računom. Iz seznama storitev izberite "~okeanos global". Preusmerilo vas bo na ~okeanosovo spletno stran, na kateri v zgornjem desnem kotu kliknete "Sign in".

![image](https://user-images.githubusercontent.com/52399966/181916035-5b416b82-96fa-4c49-94c0-d604bd8b696a.png)

Preusmeriti bi vas moralo na zgornjo stran, na kateri kliknete "Academic login".

![image](https://user-images.githubusercontent.com/52399966/181916102-0c92757f-d1dc-4234-bfeb-941229186165.png)

Na zemljevidu izberite Slovenijo, nakar se bi vam moral prikazati seznam slovenskih AAI organizacij. Izberite Arnes (oz. vašo šolo, če je na seznamu) in potrdite pošiljanje podatkov (če Arnes to zahteva od vas). Če prvič uporabljate storitev, bo od vas zahtevalo, da vpišete nekaj podatkov.

Na seznamu se vam pokažeta dve storitvi - Pithos in pa Cyclades. Izberite Cyclades.

![image](https://user-images.githubusercontent.com/52399966/181916214-67fcb76c-3b0f-46f3-8f48-3b00930b8195.png)

## Ustvari nov par ključev
Ključi so zelo pomembna stvar v kriptografiji. Uporabljamo jih, ker so praktično nemogoče za ugotoviti, saj so popolnoma naključni in veliko veliko daljši od gesel.

{{< hint type=important title=Pomembno >}}
Ta par ključev boste uporabili za dostop do strežnika kasneje, zato je pomembno, da jih ne izgubite.
{{< /hint >}}
{{< hint type=note >}}
Ta par ključev o katerih govorimo, niso dejanski (fizični) ključi. Namesto tega so datoteke, katere se shranjuje na trdemu disku.
{{< /hint >}}

Pojdite na del spletne strani, na kateremu generirate ključe (pojdite na ikono ključa in kliknite nanjo). Izgledati bi moralo nekako tako:
![image](https://user-images.githubusercontent.com/52399966/167488609-3778c69c-42be-41ee-b89d-7ac7fd767e1e.png)

Kliknite na gumb "New Keypair". Pokazati bi se vam moralo naslednje:

![image](https://user-images.githubusercontent.com/52399966/167488698-2bb5c949-8455-4c03-86dc-e178fd2faee5.png)

V ~okeanos globalu lahko preprosto generirate pare ključev. Samo kliknite gumb "generate new" v zgornjem desnem kotu, nakar bi se vam moralo prikazati nekaj takega:

![image](https://user-images.githubusercontent.com/52399966/167489439-2431513c-bb3a-4683-9629-2bb87f640f9a.png)

{{< hint type=important title=Pomembno >}}
Prenesite zasebni ključ. POD NOBENIM POGOJEM GA NE SMETE POZABITI PRENESTI ALI KAKORKOLI IZGUBITI, drugače bo to imelo velike posledice. USB ključki in trdi diski se pokvarijo, zato lahko ključ shranite tudi v raznih oblačnih storitvah, kot je npr. Google Drive za čim večjo varnost.
{{< /hint >}}

{{< hint type=note >}}
Prenešena datoteka mora biti v ".pem" formatu (ne potrebuje končnice .pem, da je v .pem formatu).
{{< /hint >}}

Ko ste uspešno shranili ključ, kliknite "close" in pojdite na del spletne strani, kjer piše virtualne mašine.

## Ustvarite virtualno mašino
Kliknite na "New Machine". Prikazati bi se moral nov dialog.

![image](https://user-images.githubusercontent.com/52399966/167490100-44885958-309f-4989-96b5-05d2f34d6f20.png)

Vedno se držite tako imenovanih sistemskih slik (image), saj so te preizkušene in delujoče.

{{< hint type=tip title=Nasvet >}}
Na ~okeanos globalu, priporočam Ubuntu 16.04 LTS Linux, saj je to najbolj preprost operacijski sistem za namestitev Dockerja, zato bom uporabljal ta operacijski sistem v tem priročniku.
{{< /hint >}}

{{< hint type=note title=Obvestilo >}}
Ubuntu 16.04 LTS je zastarel in nepodprt operacijski sistem, saj ~okeanos global ne nalaga novih slik operacijskih sistemov. Priporoča se, da se posodobi operacijski sistem na novejšo verzijo (priporočljivo do 20.04 LTS ali 22.04 LTS).
{{< /hint >}}

{{< hint type=important title=Pomembno >}}
Ubuntu 16.04 LTS **NI** Windows ali kakorkoli podoben Windowsu. Ubuntu je t.i. Linux sistem, ki temelji na Unix sistemih. MacOS je Unix sistem, zato so Linux komande zelo podobne MacOS komandam v terminalu/konzoli.
{{< /hint >}}

{{< hint type=important title=Pomembno >}}
Ubuntu 16.04 LTS **NI** sistem z grafičnim uporabniškim vmesnikom. To pomeni, da ta sistem uporablja samo in izključno konzolo oz. terminal.
{{< /hint >}}

Minimalne zahteve MeetPlan sistema so:
- Operacijski sistem na Linux kernelu
- 1 (virtualno) procesorsko jedro
- 0.5 GB pomnilnika (RAM-a)
- Okoli 8GB trdega diska

Priporočljive specifikacije so 2 (virtualni) procesorski jedri in 2GB pomnilnika (RAM-a). Izberite 40GB trdega diska. Morate ustvariti oz. izbrati IP naslov.

{{< hint type=tip title=Nasvet >}}
Če niste prepričani, da je IP že v uporabi s strani druge virtualne mašine, samo ustvarite novega.
{{< /hint >}}

Kliknite "next". Poimenujte strežnik, kakor ga želite. Izbrati morate tudi SSH ključ, katerega smo ustvarili v prejšnjem poglavju.

![image](https://user-images.githubusercontent.com/52399966/167491384-def45e4e-0ca9-49c3-9bca-00544f5d91bb.png)

Naslednje je moja končna konfiguracija strežnika:

![image](https://user-images.githubusercontent.com/52399966/167491468-95c9a6ab-3005-4ba2-864b-1f539827852b.png)

Ko ste zadovoljni s konfiguracijo, kliknite "create machine". Moralo bi vas obvestiti z geslom, katerega si **MORATE** shraniti. Počakajte, da se mašina zgradi, nakar se boste lahko priklopili nanjo z SSH programom, kot je [PuTTY](https://www.putty.org/).

Sledite [temu vodiču](https://devops.ionos.com/tutorials/use-ssh-keys-with-putty-on-windows/) (napisan v angleščini), s tem, da izpustite poglavji "Create New Public and Private Keys" in pa "Copy Public Key to Server". PuTTY vas bo obvestil, da je ključ nepoznan, zato moramo potrditi z klikom na gumb, nakar vtipkate uporabniško ime "user", nakar boste videli nekaj takega:
```sh
Welcome to Ubuntu 16.04.3 LTS (GNU/Linux 4.4.0-109-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

254 packages can be updated.
180 updates are security updates.


user@snf-58132:~$
```

Če vidite zgornje, veste, da ste znotraj strežnika in lahko preidete na naslednji korak.
