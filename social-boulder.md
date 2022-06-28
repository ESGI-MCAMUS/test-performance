# Social Boulder - Cachier des charges de test de performances

Site web: [sboulder.com](https://www.sboulder.com/)

Rédacteur du document: Milan CAMUS – IW2

Groupe de travail: [@Arkeonn](https://github.com/ThomasGeoffron), [@MisterGoodDeal](https://github.com/MisterGoodDeal) et [@Haborym](https://github.com/Haborym)

## Préambule

Le but de ce projet est de mesurer les performances du site [sboulder.com](https://www.sboulder.com/). Nous devons nous assurer que le site peut encaisser des pics de charges lors des évènements organisés par les salles d'escalade ainsi que de verifier que le site reste stable avec une charge moyenne sur le traffic utilisateur global.

### A quoi sert Social Boulder ?

Social Boulder est un site web qui permet aux utilisateurs de partager des informations sur leur activité dans le cadre de l'escalade. Ils peuvent accéder aux différentes salles inscrites sur le réseau et aux informations sur les activités organisées par les salles.

### Quel type d'utilisation prévue ?

- En temps normal, une activitée quotidienne d'environ 10K utilisateurs répartis sur la journée de 9h00 à 23h00.
- Lors d'évènements, des utilisateurs peuvent se connecter à l'application pour participer à l'évènement en validant les voies complétées. L'infrastructure doit être capable de gérer environ 100 requêtes par minutes toutes les 5 minutes et cela pendant un période de 4h00 (généralement de 21h00 à 00h00) et pour chaque salle organisant un évènement.

### Autres informations

Social Boulder est disponible dans toute l'Europe, et sera hébergé sur un serveur :

- AWS `eu-west-2` – London

## Architecture de l'application

- Réalisé avec Material Design
- Serveur: Amazon AWS EU (`t3.medium`)
- Base de données: Amazon RDS (`db.t3.large`)
- Stack technique: React et NodeJS

## Exigence des tests

La création de tests de performances est requise afin de vérifier que le site reste stable et performant, même lors de l'organisation de plusieurs évènements par les salles, évènements pouvant stresser fortement les serveurs.

### Capacités max (connexions simultanées)

Selon Amazon pour caculer les capacités max des serveurs, on peut faire le calcul suivant `{InstanceClassMemory/12582880}`

- VPS : `4096 * 1024 * 1024 / 12582880 = 341`
- Base de données : `8192 * 1024 * 1024 / 12582880 = 683`

### Processus non-fonctionnels

| Business Transactions | User Load | Response Time | Transactions per hour |
| --------------------- | :-------: | :-----------: | :-------------------: |
| Page de connexion     |    200    |       1       |          500          |
| Page d'inscription    |    50     |       1       |          100          |
| Page d'accueil        |    500    |       1       |         1.5K          |
| Visionner une voie    |    500    |       1       |          10K          |
| Reussir une voie      |    500    |       1       |          8K           |

## Environnements

### Dev

- CPU: Intel Core i7 6 cœurs @ 2,6GHz
- RAM: 16Go DDR4 3200MHz
- OS: MacOS Montery 12.3.1
- Node 16.13.0

### Prod

- CPU: Intel AVX2 (2 vCPU)
- RAM: 8Go
- Linux
- Node 16.13.0

Coéfficient proportionnel : `0.33`
