---
title: ChatOps com o Mattermost
description: Dicas para usar o Chat Águas Mídia Livre
published: true
date: 2023-07-21T15:31:22.687Z
tags: águas, chat, mattermost, plataforma, ubuntu
editor: markdown
dateCreated: 2022-11-28T23:05:05.615Z
---

# ChatOps usando o Mattermost
O [Chat Águas ML](https://chat.aguas.dev) conta com com aplicativo para celulares, notebooks e desktops, podendo também ser utilizado via navegadores, muito útil caso queiramos sair dos servidores das grandes empresas de internet.

Com adoção, se a dinâmica e as pessoas curtirem, podemos usar com tranquilidade chats privados, grupos livres, etc. Ainda conta com uma gama interessante de integrações com outros aplicativos e sistemas.

Veja nosso manual de uso: https://aguas.win/manual-de-uso/

.
## Links para utilização
A seguir, uma lista com possibilidades de acesso ao chat

- Pelo navegador: https://chat.aguas.dev
- Com aparelhos Android: https://play.google.com/store/apps/details?id=com.mattermost.rn
- Com aparelhos Apple: https://apps.apple.com/us/app/mattermost/id1257222717
- Programas para computadores Windows, MAC e Linux: https://mattermost.com/download/

.
## Temas para usar
Alguns sites com temas para você procurar um bacana para você:
- Temas [para Mattermost](https://avasconcelos114.github.io/mattermost-themes/)
- Temas [para Slack](https://slackthemes.net/#/aubergine) que também podemos utilizar


Este código é um exemplo de um tema dark, utilizado pela waterops

```
{"awayIndicator":"#ff9e64","buttonBg":"#7aa2f7","buttonColor":"#1a1b26","centerChannelBg":"#1a1b26","centerChannelColor":"#c0caf5","codeTheme":"tokio-night","dndIndicator":"#f7768e","errorTextColor":"#f7768e","linkColor":"#7aa2f7","mentionBg":"#414868","mentionBj":"#cfc9c2","mentionColor":"#a9b1d6","mentionHighlightBg":"#414868","mentionHighlightLink":"#7aa2f7","newMessageSeparator":"#ff9e64","onlineIndicator":"#9ece6a","sidebarBg":"#1a1b26","sidebarHeaderBg":"#1a1b26","sidebarHeaderTextColor":"#a9b1d6","sidebarTeamBarBg":"#1a1b26","sidebarText":"#a9b1d6","sidebarTextActiveBorder":"#9ece6a","sidebarTextActiveColor":"#7aa2f7","sidebarTextHoverBg":"#414868","sidebarUnreadText":"#c0caf5"}
```

.
## Faça a sua instalação
Para instalar em seu servidor, escolha um guia na [documentação oficial](https://docs.mattermost.com/guides/administrator.html#installing-mattermost)

.
### Dicas úteis

Renovando SSL
A cada 3 meses é preciso renovar o SSL, caso receba erros na renovação automática

Para tanto, atualize o sistema, instale ou atualize o git, baixe o let´s encrypt mais recente do github, pare o nginx, instale ou atualize o let´s encrypt e rode-o. Tentamos renovar somente, com erros. Até descobrirmos que se você usar o comando de instalação, ele identificará que já existe um certificado e vai renovâ-lo para você.

```text
sudo apt-get update

sudo apt-get install git

git clone https://github.com/letsencrypt/letsencrypt

cd letsencrypt

sudo systemctl stop nginx

./letsencrypt-auto certonly --standalone

sudo systemctl start nginx
```

Depois reinicie o servidor, para garantir
```text
reboot
```