<!-- TITLE: Waterchat -->
<!-- SUBTITLE: DOCUMENTAÇÃO USADA PARA ATUALIZAR O ROCKET CHAT DO AGUAS -->

# Atualizando o Chat ÁguasML

Primeiro faça backup, mais de um backup se possível.

Se estiver utilizando uma VPS veja se pode fazer um snapshot também.


```text
$ ssh root@seudominio.net 
$ sudo su seu-user
$ cd /home/gaia/containers/aguas-rocketchat
$ docker pull rocket.chat:latest
$ docker-compose stop rocketchat
$ docker-compose rm rocketchat
$ docker-compose up -d rocketchat
```



## Software utilizado

**Rocket.Chat Documentation - Docker Compose**
https://rocket.chat/docs/installation/docker-containers/docker-compose/