---
title: Rádio Digital
description: Uma rádio com código livre na internet
published: true
date: 2023-06-06T20:39:14.235Z
tags: biluga, digital, ferramentas, libretime, nginx, plataforma, rádio, tudo para sua casa, ubuntu, vps
editor: markdown
dateCreated: 2022-11-28T23:04:02.840Z
---

# Novidades da Rádio Bilu.ga

Vamos atualizar nossa rádio, melhorando os serviços!

Software escolhido é um fork do Airtime atual, atualizando em http://libretime.org/install/

# Notas de instalação
Caso você pretenda criar um webrádio especial, esperamos que você já saiba o que está fazendo, então alguns passos são genéricos

* Se usa o Windows, instale o Puttygen
* Pareie as chaves e crie sua imagem UBUNTU no VPS
* Entre com ssh root@IP


.
## Instalando o Libretime


```text
git clone https://github.com/LibreTime/libretime.git
cd /libretime
sudo ./install
```


Digite Y e aperte  ENTER quando preciso.

E aguarde para ver seu site rodando. A partir do seu IP, continue a configuração do Libretime



.
## Dicas waterops do Libretime
Algumas anotações importantes para o processo

.
### Definir local, erro airtime-playout
A instalação não tem um local mínimo setado, faça isso



```text
localectl set-locale LANG="en_US.utf8"

# check status
systemctl status airtime-playout

# look at logs:
journalctl -u airtime-playout

# follow logs:
journalctl -u airtime-playout -fn
```

E reinicie

.
### Verificando e resolvendo o apache2

Caso você receba o erro: `AH00558: apache2: Could not reliably determine the server's fully qualified domain name`


Edite o arquivo de config do Apache2
```text



sudo nano /etc/apache2/apache2.conf
```

E adicione a seguinte linha
```text
ServerName seudominio.org
```


Teste e reinicie o Apache2
```text
sudo apache2ctl configtest
sudo systemctl restart apache2

```

Reinicie o sistema, de novo

.
### Infos sobre o Libretime

A seguir outros possíveis "erros" no Libretime


```text
sudo a2dismod mpm_event
sudo a2enmod mpm_prefork
```

E ai?

.
### Storage Libretime

Pasta de armazenamento do Libretime


```text
/srv/airtime/stor
```

Fuce

.
### reinstalando o Libretime

Delete o arquivo `/etc/airtime/airtime.conf` e rode o instalador novamente


.