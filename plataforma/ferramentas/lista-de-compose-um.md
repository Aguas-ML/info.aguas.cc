---
title: Lista de docker-compose para plataformas digitais hídricas
description: Anotações importantes para estudo de docker e Data Science
published: true
date: 2023-06-06T20:38:45.781Z
tags: código aberto, data, docker, lista, science, software
editor: markdown
dateCreated: 2022-11-28T23:03:33.255Z
---

# Anotando coisa boa
Importante poder achar isso quando for necessario, em alguma demonstração.


## RStudio com Neo4j

```
version: '3.7'

services:
  neo4j:
    image: neo4j:3.5
    container_name: "neo4j"
    volumes:
      - ./plugins:/home/rstudio/plugins
      - ./data:/home/rstudio/data
      - ./import:/home/rstudio/import
      - ./neo4j/data:/data
      - ./neo4j/conf:/conf
      - ./neo4j/import:/import
      - ./neo4j/plugins:/plugins
      - ./neo4j/logs:/logs
    ports:
      - "7474:7474"
      - "7473:7473"
      - "7687:7687"
    environment:
      NEO4J_AUTH: neo4j/password
      NEO4J_apoc_export_file_enabled: "true"
      NEO4J_apoc_import_file_enabled: "true"
      NEO4J_apoc_import_file_use__neo4j__config: "true"
      NEO4J_dbms_security_procedures_unrestricted: "apoc.\\*"
      NEO4J_dbms_memory_heap_initial__size: "512m"
      NEO4J_dbms_memory_heap_max__size: "2G"
  rstudio:
    image: rocker/tidyverse
    ports:
      - "8787:8787"
    environment:
      - USER=pessoadaagua
      - PASSWORD=suasenha
    volumes:
      - ./:/home/rstudio/
    links:
      - neo4j
```

Fontes e exemplos:

- https://rocker-project.org/
- https://github.com/Btibert3/docker-recipes/ 