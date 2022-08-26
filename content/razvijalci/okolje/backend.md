---
title: Namestitev razvijalskega okolja za zaledni del (backend)
---

{{< toc >}}

# Namestitev razvijalskega okolja
V tem delu vam predstavim namestitev razvijalskega okolja za zaledni del.

{{< hint type=important title=Pomembno >}}
Glavni razvijalec sistema uporablja JetBrains orodja. Za backend bomo uporabljali GoLand. Več si lahko preberete na prejšnji strani.
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

![image](/developerdocs/backendsetup.svg)

{{< hint type=note title=Obvestilo >}}
OpenSSL ukaz generira digitalne certifikate za digitalno podpisovanje PDF dokumentov. OpenSSL ustvari samopodpisan (self-signed) certifikat, katerega ne bodo programi, ki preverjajo digitalne certifikate v PDF dokumentu, prepoznali, saj ni podpisan s strani veljavne certifikatne avtoritete. Eden izmed programov, ki ne preverja certifikatnih avtoritet, temveč samo preveri za podpis, je [Okular](https://okular.kde.org/).
{{< /hint >}}

# Uporabni ukazi
- `go run -v .` - zažene backend, med grajenjem pa izpiše, katere datoteke se kdaj gradijo
- `go build -v .` - zgradi backend v izvršilno datoteko
- `go mod download` - prenos vseh knjižic lokalno
- `go get -v .` - prenos vseh knjižic lokalno in konfiguracija
