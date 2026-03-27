# Set up notes (Second try - this time with help of Claude)

For (re)starting after installation see `./notes.md`.


# W A R N I N G

After the workshop remove `$USER` from the group `docker` - otherwise
`$USER` (or an attacker that has gained access to `$USER`) can excute commands with root power!


## zsh history

## Tidied copy of zsh history

```zsh

# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF



uname --all
git clone https://github.com/rciak/42-WS-26-03-30-Rudi-practice-software-testing
cd 42-WS-26-03-30-Rudi-practice-software-testing


------- Trying to install stuff via Claude Output ----
# Alte Versionen entfernen (schadet nicht)
sudo apt-get remove -y docker docker-engine docker.io containerd runc

# Abhängigkeiten installieren
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg

# Docker GPG-Key hinzufügen
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Docker-Repository hinzufügen
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Docker installieren
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
ls /etc/apt/keyrings/docker*

-----Lösche und versuche es dann neu -----
sudo rm -f /etc/apt/sources.list.d/docker.list
sudo rm -f /etc/apt/keyrings/docker.gpg
sudo rm -f /etc/apt/keyrings/docker.asc
sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo tee /etc/apt/keyrings/docker.asc > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

sudo usermod -aG docker $USER
newgrp docker

docker --version
docker compose version

cd /home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing

docker compose -f docker-compose.prod.yml up --pull missing -d
docker compose -f docker-compose.prod.yml logs -f
docker compose -f docker-compose.prod.yml down
cd /home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing
docker compose up -d
docker compose logs -f

------- Jetzt zeigt   http://localhost:4200    Toolshop an; jedoch Werden einige Bilder noch nicht angezeigt -------

```


## Untidied copy of zsh history

```zsh
modprobe kvm
man modprobe
----------------------------------First command above
kvm-ok
man kvm
# Add Docker's official GPG key:
sudo apt update
sudo apt install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF

sudo apt update
sudo apt install gnome-terminal
open .
sudo apt-get update
sudo apt install ./Downloads/docker-desktop-amd64.deb
sudo apt-get update
sudo apt install docker-desktop
sudo apt install ./Downloads/docker-desktop-amd64.deb
uname -all
uname --all
cd github
git difftool
git pull --rebase
git stash
git stash pop
git push
git clone https://github.com/rciak/42-WS-26-03-30-Rudi-practice-software-testing
cd 42-WS-26-03-30-Rudi-practice-software-testing
pwd
cd
------- Trying to install stuff via Claude Output ----
# Alte Versionen entfernen (schadet nicht)
sudo apt-get remove -y docker docker-engine docker.io containerd runc

# Abhängigkeiten installieren
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg

# Docker GPG-Key hinzufügen
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Docker-Repository hinzufügen
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Docker installieren
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
ls /etc/apt/keyrings/docker*
-----Lösche und versuche es dann neu -----
sudo rm -f /etc/apt/sources.list.d/docker.list
sudo rm -f /etc/apt/keyrings/docker.gpg
sudo rm -f /etc/apt/keyrings/docker.asc
sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | \
  sudo tee /etc/apt/keyrings/docker.asc > /dev/null
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
fish
ln -s $HOME/github/42-WS-26-03-30-Rudi-practice-software-testing $HOME/WS
ls
ls -l
ls /home/rene/WS/
touch .zsh_inc
ls -al /home/rene/WS/
mv .zsh_inc WS
sudo usermod -aG docker $USER
newgrp docker
docker --version
docker compose version
cd /home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing
docker compose -f docker-compose.prod.yml up --pull missing -d
docker compose -f docker-compose.prod.yml logs -f
docker compose -f docker-compose.prod.yml down
cd /home/rene/github/42-WS-26-03-30-Rudi-practice-software-testing
docker compose up -d
docker compose logs -f
rm .zsh_inc
git checkout reciak
git status
ls -al
ls z_reciak
ls -al z_reciak
ls /home/rene/WS/reciak/
ls /home/rene/WS
exit
zshrc
zsh
cd ..
cd general-synced-configs
git log
git pull
git commit -a
git commit
git diff
exit
git push
------- Jetzt zeigt   http://localhost:4200    Toolshop an; jedoch Werden einige Bilder noch nicht angezeigt -------


```















# OLD_TRY - did not work    Set up notes

The following was done for Ubuntu 24.04.4 LTS running in a Virtual Machine.

```zsh
lsb_release --all

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 24.04.4 LTS
Release:        24.04
Codename:       noble
```

## Installation of Docker

* Following essentially [Docker Installation for Ubuntu via apt](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository) to

  * install docker (but used sudo, since otherwise it did not directly work (seems *potentially dangerous* to use sudo here but for the local testing Workshop it should be ok)) and
  * check if installation worked by running a simple greeting program.

```zsh
  sudo apt update
  sudo apt install ca-certificates curl
  sudo install -m 0755 -d /etc/apt/keyrings
  sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
  sudo chmod a+r /etc/apt/keyrings/docker.asc
  sudo tee /etc/apt/sources.list.d/docker.sources <<EOF\nTypes: deb\nURIs: https://download.docker.com/linux/ubuntu\nSuites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")\nComponents: stable\nSigned-By: /etc/apt/keyrings/docker.asc\nEOF
  sudo apt update
  sudo systemctl status docker

  sudo docker run hello-world
```

## Getting the test-practicing repo ready

On github first a fork of the practice-software-testing Repo was performed and then cloned from
that fork.

```zsh
  git clone git@github.com:rciak/practice-software-testing.git
  cd practice-software-testing
  sudo docker compose up -d
  sudo docker compose exec laravel-api php artisan migrate
  sudo docker compose exec laravel-api php artisan migrate:fresh --seed
```
