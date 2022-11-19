---
title: Namestitev podatkovne baze (PostgreSQL)
---

{{< toc >}}

# Namestitev
## Linux distribucije
### Fedora/RPM distribucije
```shell
sudo dnf install postgresql postgresql-server postgresql-contrib
sudo postgresql-setup --initdb --unit postgresql
sudo systemctl start postgresql
sudo systemctl enable postgresql
```
![postgres](https://user-images.githubusercontent.com/52399966/202866109-b328edef-1e7d-4479-89a6-ebd79affdec5.svg)

### Debian/Ubuntu in derivati
{{< hint type=warning title=Opozorilo >}}
Priporočljivo je uporabljati Fedoro oz. katerokoli distribucijo, ki uporablja RPM format in dnf.
Na .deb distribucijah ni bilo nikoli testirano, a vseeno tukaj objavljam približna navodila.
{{< /hint >}}
```shell
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo postgresql-setup --initdb --unit postgresql
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

### Arch
{{< hint type=warning title=Opozorilo >}}
POGRUNTAJTE SAMI! Ne uporabljam Archa in ga tudi verjetno nikoli ne bom.
{{< /hint >}}

## Windows
{{< hint type=warning title=Opozorilo >}}
NI PODPRTO, UPORABITE LINUX.
{{< /hint >}}

## MacOS
{{< hint type=warning title=Opozorilo >}}
NI PODPRTO, UPORABITE LINUX.
{{< /hint >}}

# Ustvari podatkovno bazo
{{< hint type=note title=Obvestilo >}}
Ta postopek bi moral delati na vseh Linux operacijskih sistemih.
{{< /hint >}}

![postgres2](https://user-images.githubusercontent.com/52399966/202866876-fc6383e6-dba1-413c-a5d2-603f0a61920e.svg)

# Dovoli povezavo do SQL podatkovne baze preko uporabniškega imena in gesla
1. Geslo spremenite na `postgres`
2. Na spodnji sliki vidite, kje morate zamenjati `ident` z `md5`. Izbrisal sem vse, očitno je program za snemanje terminala tega ni zaznal, in je ostal `i `. Ignorirajte to in vpišite samo `md5`.

![postgres4](https://user-images.githubusercontent.com/52399966/202866682-0985ba37-22e1-4fa4-af3e-f7f6efe13a27.svg)





