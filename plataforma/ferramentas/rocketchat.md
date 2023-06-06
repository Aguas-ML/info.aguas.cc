---
title: WaterOps e o chat hídrico
description: Documentação para a manutenção ativa do Chat ÁguasML
published: true
date: 2023-06-06T20:39:28.359Z
tags: águas, chat, ferramentas, plataforma, rocket, vps
editor: markdown
dateCreated: 2022-11-28T23:04:16.532Z
---

# Rotina para atualizar o Chat ÁguasML

URL: https://chat.aguas.win

* **Versão 2018**

Primeiro faça backup, mais de um backup se possível.

Se estiver utilizando uma VPS veja se pode fazer um snapshot também.


```text
$ ssh root@seudominio.win
$ sudo su seu-user
$ cd /home/SEU-HOST/containers/aguas-rocketchat
$ docker pull rocket.chat:latest
$ docker-compose stop rocketchat
$ docker-compose rm rocketchat
$ docker-compose up -d rocketchat
```




-----


## Software utilizado

**Rocket.Chat Documentation - Docker Compose**
https://rocket.chat/docs/installation/docker-containers/docker-compose/

.