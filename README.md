# Facture App — Deployment

Configuration Docker de la base de données PostgreSQL utilisée par l'application de gestion de factures.

## Technologies

- Docker
- Docker Compose
- PostgreSQL 16

## Prérequis

- Docker Desktop installé et démarré
- Docker Compose disponible

## Configuration

Créer un fichier `.env` à partir de `.env.example` :

```bash
POSTGRES_PASSWORD=change_me
```

Remplacer `change_me` par un mot de passe adapté à l'environnement local.

Ne jamais publier le fichier `.env` ni les identifiants de la base de données.

## Démarrage

Lancer PostgreSQL :

```bash
docker compose up -d
```

Vérifier l'état du conteneur :

```bash
docker compose ps
```

Consulter les journaux :

```bash
docker compose logs postgres
```

Arrêter le service :

```bash
docker compose down
```

Le service utilise un volume Docker nommé `facture_data` pour conserver les données entre les redémarrages du conteneur. La commande `docker compose down` ne supprime pas ce volume par défaut.

## Paramètres de connexion

- Hôte : `localhost` depuis l'ordinateur hôte
- Port : `5432`
- Base de données : `facturedb`
- Utilisateur : `postgres`
- Mot de passe : défini dans `.env`

Ces paramètres doivent correspondre à la configuration du backend Spring Boot.

## Dépôts du projet

- Frontend : https://github.com/belkis2023/facture-frontend
- Backend : https://github.com/belkis2023/facture-backend
- Extraction Python : https://github.com/belkis2023/facture-python
