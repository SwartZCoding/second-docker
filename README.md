# Projet Docker : Nuxt 3, AdonisJS 6, PostgreSQL

## Modes de lancement

### Mode Production
```bash
# Lancement standard
docker-compose --profile prod up

# Reconstruction de l'image pour la production
docker-compose --profile prod up --build
```

### Mode Développement

Nous n'utilisons pas la fonction watch de Docker car nous sommes sur une Stack Nuxt & Adonis qui disposent tous les 2 de Hot reload en cas de modification.
```bash
docker-compose --profile dev up

# Reconstruction de l'image pour le dev
docker-compose --profile dev up --build
```

## Structure des secrets

Les secrets doivent être créés dans docker à l'aide des commandes suivantes :

echo "MOTDEPASSESECURISE" | docker secret create db_password -
echo "UNEAPPKEYSECURISE" | docker secret create app_key -

Cette méthode pour gérer les secrets nécessite que Docker Swarm soit activé : 

```bash
docker swarm init    # Si Swarm n'est pas encore activé
```

Les secrets seront montés dans le container sous forme de fichiers temporaires, ce qui améliore la sécurité car ils ne sont pas stockés comme des variables d'environnement.

## Validation de la recette

Nous utilisons `hadolint` pour valider nos Dockerfiles et `docker-compose-validate` pour notre fichier docker-compose.yml.

### Installation des outils de validation
```bash
# Installation de hadolint
docker pull hadolint/hadolint

# Installation de docker-compose-validate (Nécessite Python)
pip install docker-compose-validate
```

### Exemple de validation
```bash
# Validation du Dockerfile
docker run --rm -i hadolint/hadolint < ./backend/Dockerfile
docker run --rm -i hadolint/hadolint < ./frontend/Dockerfile

# Validation du compose.yaml
docker-compose-validate docker-compose.yml
```

## Résultats de validation

```bash
$ docker-compose-validate docker-compose.yml
Validation passed!

$ docker run --rm -i hadolint/hadolint < ./backend/Dockerfile && docker run --rm -i hadolint/hadolint < ./frontend/Dockerfile
No issues detected!
No issues detected!
```
