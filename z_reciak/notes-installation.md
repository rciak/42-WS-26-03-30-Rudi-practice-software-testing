# Set up notes

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
