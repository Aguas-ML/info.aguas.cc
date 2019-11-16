<!-- TITLE: Nova Web Rádio -->
<!-- SUBTITLE: Uma nova web rádio -->

# Notas de instalação

* Instalando Puttygen
* Pareando chaves e criando VPS
* Login ssh root@

`sudo apt-get install git curl wget nano`

### Edite o arquivo /etc/apt/sources.list com estas linhas:
deb http://archive.ubuntu.com/ubuntu bionic main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-security main multiverse restricted universe
deb http://archive.ubuntu.com/ubuntu bionic-updates main multiverse restricted universe

### Atualize e instale:

`sudo apt update`
`sudo apt-get upgrade`
`sudo apt-get install ufw`
`sudo ufw allow OpenSSH
sudo ufw enable`
`date`
`sudo apt update && sudo apt upgrade && sudo apt dist-upgrade`



### Instalar PHP
`sudo apt-get install php
sudo apt-get install php-{bcmath,bz2,intl,gd,mbstring,mysql,zip,fpm}`

https://soka.gitlab.io/RadioLibre/man/libretime_y_virtualbox/
https://www.p-node.org/documentation/hardwares/serveur-2