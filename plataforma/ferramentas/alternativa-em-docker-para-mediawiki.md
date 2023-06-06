---
title: Uma alternativa em Docker para Mediawiki 1.26
description: Registro de operações
published: true
date: 2023-06-06T20:37:47.318Z
tags: compose, docker, mediawiki, mysql, wiki
editor: markdown
dateCreated: 2022-11-28T23:02:31.276Z
---

# Compartilhando composição
Dicas para uso da MW em versão antiga

```
version: '3'

networks:
  suarede:
    
volumes:
  data_mw:
  dados_mw:
  
services:
  mwiki_db:
    image: mysql:5.7
    volumes:
      - data_mw:/var/lib/mysql:rw
    ports:
      - 13306:3306
    environment:
      MYSQL_DATABASE: wiki_db
      MYSQL_ROOT_PASSWORD: rootSENHA
      MYSQL_USER: wikimediaUSER
      MYSQL_PASSWORD: wikimediaSENHA
    networks:
      - suarede
    restart: always

  mwiki:    
    image: bitnami/mediawiki:1.26.3-r1
    ports:
      - 8080:80
    depends_on:
      - mwiki_db
    volumes:
      - dados_mw:/var/www/html/
    environment:
      MEDIAWIKI_DB_HOST: mwiki_db
      MEDIAWIKI_DB_TYPE: mysql
      MEDIAWIKI_DB_NAME: wiki_db
      MEDIAWIKI_DB_USER: wikimediaUSER
      MEDIAWIKI_DB_PASSWORD: wikimediaSENHA
      MEDIAWIKI_SITE_SERVER: //localhost
      MEDIAWIKI_SITE_NAME: MediaWiki
      MEDIAWIKI_SITE_LANG: pt_BR
      MEDIAWIKI_ADMIN_USER: adminUSER
      MEDIAWIKI_ADMIN_PASS: passwordSENHA
      MEDIAWIKI_UPDATE: true
    restart: always
    networks:
      - suarede
````

Após a configuração inicial, baixe LocalSettings.php para o mesmo diretório que usou para executar este yaml e adicione a linha a seguir no volume do mwiki.

      - ./LocalSettings.php:/var/www/html/LocalSettings.php

Use compose para reiniciar o serviço mwiki

### Fontes

Bitnami: https://hub.docker.com/r/bitnami/mediawiki
Wikimedia: https://github.com/wikimedia/mediawiki-containers/blob/master/docker-compose.yml