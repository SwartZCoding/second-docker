# Projet Docker : Nuxt 3, AdonisJS 6, PostgreSQL

## Modes de lancement

### Mode Production
```bash
# Lancement standard
docker compose up -d

# Reconstruction des images
docker compose build --no-cache
docker compose up -d
```

### Mode Développement
```bash
# Lancement avec watch mode
docker compose -f docker-compose.yml --env-file .env.dev watch

# Reconstruction pour le dev
docker compose -f docker-compose.yml --env-file .env.dev build
```

## Structure des secrets

Les secrets doivent être créés dans docker à l'aide des commandes suivantes :

echo "MOTDEPASSESECURISE" | docker secret create db_password -
echo "UNEAPPKEYSECURISE" | docker secret create app_key -

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
docker run --rm -i hadolint/hadolint < Dockerfile

# Validation du compose.yaml
docker-compose-validate docker-compose.yml
```

## Résultats de validation

```bash
$ docker-compose-validate docker-compose.yml
Validation passed!

$ docker run --rm -i hadolint/hadolint < Dockerfile
No issues detected!
```
