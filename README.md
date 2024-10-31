# Projet Docker : Nuxt 3, AdonisJS 6, PostgreSQL

## Prérequis
- Docker
- Docker Compose

## Installation

1. Clonez le dépôt :
   ```bash
   git clone <url-du-dépôt>
   cd first-docker 
   ```

2. Structure du projet
- /backend : Backend AdonisJS 6
- /frontend : Frontend Nuxt 3
- docker-compose.yml : Configuration des conteneurs Docker

3. Persistance des données
Les données PostgreSQL sont persistées grâce au volume Docker pgdata.

4. Réseaux Docker
Tous les conteneurs communiquent via le réseau Docker app-network.

## Lancement

1. Construire et lancer les containers
   ```bash
   docker-compose up --build
   Accédez au frontend à l'adresse : http://localhost:3000
   Accédez au frontend à l'adresse : http://localhost:3333
   ```