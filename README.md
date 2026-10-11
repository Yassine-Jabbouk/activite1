# Microservice de Gestion des Comptes Bancaires

## 1. Présentation du projet

Ce projet consiste à développer un microservice de gestion des comptes bancaires avec Spring Boot. Il permet de manipuler les informations des comptes bancaires à travers plusieurs interfaces : une API REST, une API GraphQL et une API REST générée avec Spring Data REST.

Le projet a été réalisé dans le cadre d'un travail pratique portant sur le développement de microservices avec l'écosystème Spring.

## 2. Objectifs

Les principaux objectifs du projet sont :

- Créer et gérer une entité bancaire avec JPA.
- Accéder aux données à l'aide de Spring Data JPA.
- Tester la couche DAO et les opérations sur la base de données.
- Développer un service RESTful pour gérer les comptes bancaires.
- Tester les API avec un client REST comme Postman.
- Générer une documentation interactive avec Swagger / OpenAPI.
- Utiliser Spring Data REST et les projections.
- Structurer l'application avec des DTOs et des mappers.
- Séparer la logique métier dans une couche Service.
- Exposer les données à travers une API GraphQL.

## 3. Technologies utilisées

- **Java 17** : langage de programmation.
- **Spring Boot** : création et configuration de l'application.
- **Maven** : gestion des dépendances et compilation.
- **Spring Web** : développement des API REST.
- **Spring Data JPA** : accès aux données et opérations de persistance.
- **H2 Database** : base de données relationnelle.
- **Lombok** : réduction du code répétitif.
- **Spring Data REST** : exposition des repositories REST.
- **Spring for GraphQL** : interrogation des données avec GraphQL.
- **SpringDoc OpenAPI / Swagger UI** : documentation et test des API REST.

## 4. Architecture du projet

L'application est organisée en plusieurs couches afin de séparer les responsabilités.

- **Entities** : représentent les objets persistés en base de données, notamment `BankAccount`.
- **Repositories** : assurent l'accès aux données grâce à Spring Data JPA.
- **Web / Controllers** : exposent les fonctionnalités à travers les API REST et GraphQL.
- **Services** : contiennent la logique métier.
- **DTOs** : définissent les objets utilisés pour transférer les données.
- **Mappers** : assurent la conversion entre les entités et les DTOs.
- **Resources** : contiennent notamment le schéma GraphQL et la configuration de l'application.

## 5. Fonctionnalités réalisées

### 5.1 Gestion des comptes bancaires

L'entité `BankAccount` représente un compte bancaire. Elle contient notamment les informations suivantes :

- Identifiant du compte.
- Date de création.
- Solde.
- Devise.
- Type de compte.

La persistance est assurée par JPA et Spring Data JPA, avec H2 comme base de données.

### 5.2 Couche DAO et Repository

L'interface `BankAccountRepository` permet d'accéder aux comptes bancaires et d'utiliser les opérations de persistance fournies par Spring Data JPA.

Cette couche permet de séparer l'accès aux données du reste de l'application.

### 5.3 API REST

Le microservice expose des services REST permettant de manipuler les comptes bancaires selon les opérations implémentées dans le projet.

Les API peuvent être testées avec Postman ou un autre client HTTP.

### 5.4 Documentation Swagger / OpenAPI

SpringDoc OpenAPI génère une documentation des API REST et fournit une interface interactive permettant de consulter les endpoints et de tester les requêtes disponibles.

URL habituelles en environnement local :

- Swagger UI : `http://localhost:8080/swagger-ui.html`
- Documentation OpenAPI : `http://localhost:8080/v3/api-docs`

### 5.5 Spring Data REST et projections

Spring Data REST permet d'exposer les fonctionnalités des repositories sous forme de ressources REST. Les projections permettent de sélectionner les propriétés à afficher selon les besoins.

### 5.6 DTOs et Mappers

Les DTOs permettent de transférer les données sans exposer directement toutes les propriétés des entités. Les mappers assurent la conversion entre les objets métier et les objets de transfert.

### 5.7 Couche Service

La couche Service centralise la logique métier et sépare les opérations applicatives des contrôleurs et de la persistance.

### 5.8 API GraphQL

L'application propose également une API GraphQL permettant de récupérer les informations des comptes bancaires.

Exemple de requête pour récupérer la liste des comptes :

```graphql
query MyQuery {
  accountsList {
    id
    balance
    currency
    type
  }
}
```

Exemple de requête pour rechercher un compte par son identifiant :

```graphql
query MyQuery {
  bankAccountById(id: "8b20d6de-a195-4613-953f-7d6635de6b84") {
    balance
    type
  }
}
```

L'identifiant de cet exemple doit être remplacé par celui d'un compte existant.

Le schéma GraphQL définit les types et les opérations disponibles. Les méthodes annotées avec `@QueryMapping` assurent le traitement des requêtes correspondantes.

## 6. Installation et exécution

### Prérequis

- JDK 17.
- Git.
- Maven, ou le Maven Wrapper fourni avec le projet.

### Cloner le projet

```bash
git clone <URL_DU_REPOSITORY>
cd bank-account-service
```

### Compiler le projet

Sous Windows PowerShell :

```powershell
.\mvnw.cmd clean compile
```

### Exécuter les tests

```powershell
.\mvnw.cmd test
```

### Lancer l'application

```powershell
.\mvnw.cmd spring-boot:run
```

Par défaut, l'application Spring Boot utilise le port 8080, sauf configuration différente dans le projet.

## 7. Tests

Les fonctionnalités peuvent être vérifiées à l'aide des outils suivants :

- **Maven** : compilation et exécution des tests automatisés.
- **Postman** : envoi de requêtes HTTP aux API REST.
- **Swagger UI** : consultation et test des endpoints documentés.
- **GraphQL** : exécution de requêtes pour récupérer les informations des comptes.

## 8. Bilan

Ce projet a permis de mettre en pratique les concepts fondamentaux du développement de microservices avec Spring Boot : persistance des données, architecture en couches, API REST, documentation OpenAPI, Spring Data REST, DTOs, mappers et GraphQL.

Il constitue une base pour approfondir le développement d'applications backend modulaires et l'exposition de données à travers différentes interfaces.

## 9. Auteur

Projet réalisé dans le cadre d'un travail pratique sur la gestion des comptes bancaires avec Spring Boot.