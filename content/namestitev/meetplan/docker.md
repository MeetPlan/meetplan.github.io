---
title: Namestitev Docker orodij
---

Pa pojdimo nazaj na strežnik. Še vedno bi morali biti povezani nanj preko SSH programa, drugače pa ponovite postopek iz nastavitve vašega strežnika.

Prvo bomo posodobili `apt` repozitorije. Naredite naslednje: `sudo apt update`. Vprašalo vas bo za geslo.

Sedaj pa bomo namestili `haveged`. To poskrbi, da je sistemski "entropy" vedno visok, kar je potrebno za Docker. Namesti ta paket preko: `sudo apt install haveged`.

Izvrši (copy-paste) naslednje ukaze, ki namestijo Docker in docker-compose.

Če uporabljate Ubuntu:
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install -y docker-ce
sudo curl -L "https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
echo "Docker version is $(docker --version). docker-compose version is $(docker-compose --version)"
```

Če uporabljate Debian:
```sh
sudo apt install apt-transport-https ca-certificates curl gnupg2 software-properties-common
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/debian $(lsb_release -cs) stable"
sudo apt update
sudo apt install -y docker-ce
sudo curl -L "https://github.com/docker/compose/releases/download/v2.5.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
echo "Docker version is $(docker --version). docker-compose version is $(docker-compose --version)"
```

Traja lahko kar nekaj časa. Če dobite na koncu verzijo Dockerja in docker-composa, ste lahko prepričani, da sta se Docker in docker-compose uspešno namestila in lahko nadaljujete z naslednjim delom.

