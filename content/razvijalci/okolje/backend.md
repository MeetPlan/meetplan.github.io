---
title: Namestitev razvijalskega okolja za zaledni del (backend)
---

{{< toc >}}

# Namestitev Go compilerja
## Debian/Ubuntu in derivati
```shell
sudo apt update
sudo apt install golang
```

## Fedora in RPM distribucije
```shell
sudo dnf install golang
```
![golang](https://user-images.githubusercontent.com/52399966/202867725-b3d74182-738f-4e88-a2fb-3afe914b7282.svg)

# Namestitev OpenSSL programa
{{< hint type=note title=Obvestilo >}}
Ta postopek je specifičen za Fedoro.
{{< /hint >}}
![openssl](https://user-images.githubusercontent.com/52399966/202867450-0300567d-75a3-404a-8af6-db5d541a2dc1.svg)

# Namestitev razvijalskega okolja
V tem delu vam predstavim namestitev razvijalskega okolja za zaledni del.

{{< hint type=important title=Pomembno >}}
Glavni razvijalec sistema uporablja JetBrains orodja. Za backend bomo uporabljali GoLand. Več si lahko preberete na prejšnji strani.

Navodila so relativno splošna, zato lahko tudi preskočite uporabo IDE-ja in uporabljate samo terminal.
{{< /hint >}}

Ko ste klonirali repozitorij (prejšnja stran), odprite novo mapo z GoLand IDE-jem. Odpreti bi se vam moralo nekaj podobnega:
![image](/developerdocs/backendopen.png)

Odprite terminal v vrstici spodaj.
![image](/developerdocs/backendterminalopen.png)

Sedaj pa samo tipkajte naslednje ukaze:
```shell
go get -v .
mkdir cacerts
openssl req \
	-newkey rsa:2048 \
	-subj /CN=MeetPlanCA \
	-nodes   \
	-keyout cacerts/key.pem \
	-x509 \
	-addext keyUsage=digitalSignature   \
	-out cacerts/cert.pem \
	2>/dev/null
openssl pkcs12 \
	-inkey cacerts/key.pem \
	-in cacerts/cert.pem \
	-export \
	-passout pass: \
	-out cacerts/key-pair.p12 \
	-certpbe PBE-SHA1-3DES \
	-keypbe PBE-SHA1-3DES \
	-macalg sha1
go run .
```

![backend](https://user-images.githubusercontent.com/52399966/202867566-a0d2a29f-4579-4e55-9331-c31e5758f3bb.svg)

{{< hint type=note title=Obvestilo >}}
OpenSSL ukaz generira digitalne certifikate za digitalno podpisovanje PDF dokumentov. OpenSSL ustvari samopodpisan (self-signed) certifikat, katerega ne bodo programi, ki preverjajo digitalne certifikate v PDF dokumentu, prepoznali, saj ni podpisan s strani veljavne certifikatne avtoritete. Eden izmed programov, ki ne preverja certifikatnih avtoritet, temveč samo preveri za podpis, je [Okular](https://okular.kde.org/).
{{< /hint >}}

# Zagon
```shell
go run -v .
```
![backend8](https://user-images.githubusercontent.com/52399966/202867791-d63d3151-a3e7-4111-986e-96adb48f7f01.svg)

# Uporabni ukazi
- `go run -v .` - zažene backend, med grajenjem pa izpiše, katere datoteke se kdaj gradijo
- `go build -v .` - zgradi backend v izvršilno datoteko
- `go mod download` - prenos vseh knjižic lokalno
- `go get -v .` - prenos vseh knjižic lokalno in konfiguracija
