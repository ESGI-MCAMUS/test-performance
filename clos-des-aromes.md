# Le Clos des Arômes

Website : [Le Clos des Arômes](https://le-clos-des-aromes-restaurant-briare.eatbu.com/?lang=fr)

## Préambule

### Description globale du projet

Le Clos des Arômes est un site de renseignement sur le restaurant `Le Clos des Arômes`.

### Objectifs de l'application

Le site a pour objectif :
- De renseigner sur le client sur les horaires d'ouverture et l'adresse du restaurant
- De renseigner sur le client sur les services proposés par le restaurant
- De renseigner sur le client sur les moyens de paiement acceptés par le restaurant
- De permettre aux clients de contacter le restaurant

### Types d'utilisateur prévu

Les utilisateurs prévus sont de potentiels clients cherchant à se renseigner sur le restaurant
et potentiellement le contacter.

## Architecture de l'application

### Résumé

L'application est un site vitrine sous NGINX développé par Hospitality Digital GmbH avec DISH Website.

### Technologies/Langages utilisés

- Le site a été conçu en utilisant DISH Website.
- Le serveur Web est sous NGINX et OpenResty.
- Le site utilise le framwork Adobe Client Data Layer.
- Le site utilise les librairies jQuery et LazySizes.

## Exigences du test

Le site devra être capable de supporter la connexion d'au moins 200 utilisateurs en simultané.

<table>
    <tr>
        <th>Business Transactions</th>
        <th>User Load</th>
        <th>Response Time</th>
        <th>Transaction per hour</th>
    </tr>
    <tr>
        <td>Accéder à la page d'accueil</td>
        <td>150</td>
        <td>1s</td>
        <td>200</td>
    </tr>
    <tr>
        <td>Envoyer un message</td>
        <td>30</td>
        <td>1s</td>
        <td>75</td>
    </tr>
</table>

## Environnement de test

### Dev
CPU : Intel Core i7-7700K
RAM : 8GB
OS : Linux
Software : Apache/2.4.6

### Prod
CPU : Intel Core i7-11700
RAM : 16GB
OS : Linux
Software: Apache/2.4.6

## Planification des tests

Les types de tests seront de l'Endurance Testing et du Stress Testing. 

Métriques à surveiller :
- Utilisation de la RAM
- Utilisation du CPU
- Utilisation de la bande passante

Les métriques qui définiront le succès des tests seront :
- Utilisation de la RAM
- Utilisation du CPU

## Étapes des tests

<table>
    <tr>
        <th>Step #</th>
        <th>Business Process Name : Accéder à la page d'accueil</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Page d'accueil</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Changer la langue d'affichage</td>
    </tr>
</table>

<table>
    <tr>
        <th>Step #</th>
        <th>Business Process Name : Contacter le restaurant</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Page d'accueil</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Envoyer un message</td>
    </tr>
</table>

## Éxécution des tests

<table>
    <tr>
        <th>Test Run</th>
        <th>Test Scenario Summary</th>
    </tr>
    <tr>
        <td>Cycle 1 - Run 1</td>
        <td>Endurance Test - 3h avec 50% de la capacité</td>
    </tr>
    <tr>
        <td>Cycle 1 - Run 2</td>
        <td>Stress Test - 1h30 avec 125% de la capacité</td>
    </tr>
    <tr>
        <td>Cycle 2 - Run 1</td>
        <td>Endurance Test - 2h avec 50% de la capacité</td>
    </tr>
    <tr>
        <td>Cycle 2 - Run 2</td>
        <td>Stress Test - 1h30 avec 125% de la capacité</td>
    </tr>
</table>

<table>
    <tr>
        <th></th>
        <th>Test Details</th>
    </tr>
    <tr>
        <td>Purpose</td>
        <td>Voir si le site tiens sur la durée avec une charge modérée</td>
    </tr>
    <tr>
        <td>No. of Tests</td>
        <td>2</td>
    </tr>
    <tr>
        <td>Duration</td>
        <td>
            <ul>
                <li>Ramp-up: 25VUser / 15min</li>
                <li>Steady State : 100VUser / 2h15</li>
                <li>Ramp-down: 40VUser / 30min</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>Scenario Name</td>
        <td>Endurance Test</td>
    </tr>
    <tr>
        <td>User Load / Volume</td>
        <td>100</td>
    </tr>
    <tr>
        <td>Validation Criteria</td>
        <td>
            <ul>
                <li>Response Time : < 1s</li>
                <li>Utilisation du CPU : <= 45%</li>
            </ul>
        </td>
    </tr>
</table>

<table>
    <tr>
        <th></th>
        <th>Test Details</th>
    </tr>
    <tr>
        <td>Purpose</td>
        <td>Voir si le site tiens avec un pic de surcharge (Exemple lors de l'heure du midi)</td>
    </tr>
    <tr>
        <td>No. of Tests</td>
        <td>2</td>
    </tr>
    <tr>
        <td>Duration</td>
        <td>
            <ul>
                <li>Ramp-up: 500 Thread / 5min</li>
                <li>Steady State : 500 Thread / 20sec</li>
                <li>Ramp-down: 0 Thread / 1min</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td>Scenario Name</td>
        <td>Stress Test</td>
    </tr>
    <tr>
        <td>User Load / Volume</td>
        <td>250</td>
    </tr>
    <tr>
        <td>Validation Criteria</td>
        <td>
            <ul>
                <li>Response Time : < 3s</li>
                <li>Utilisation du CPU : <= 80%</li>
            </ul>
        </td>
    </tr>
</table>