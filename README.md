# TP Spring MVC — Gestion des Produits avec Spring Boot, JPA, Thymeleaf et Spring Security

##  Objectif du projet
Le but de ce TP est de développer une application Web basée sur Spring Boot permettant de gérer des produits via un CRUD complet, d’appliquer la validation des données, d’utiliser Thymeleaf pour l’interface et de sécuriser l’accès aux pages avec Spring Security.

---

#  1. Introduction
Ce projet illustre plusieurs modules essentiels de l’écosystème Spring :

- Architecture **Spring MVC**
- Accès aux données avec **Spring Data JPA**
- Mapping ORM avec **Hibernate**
- Interface dynamique avec **Thymeleaf**
- Sécurisation avec **Spring Security**
- Validation avec **JSR-303**
- Base de données **H2 en mémoire**

Le but pédagogique est de comprendre comment assembler ces composants pour construire une application cohérente, modulaire et sécurisée.

---

#  2. Configuration de l’application

## ⚙ Configuration H2 & Spring Boot
Cette configuration active une base H2 en mémoire, met automatiquement à jour les tables selon les entités et démarre l’application sur le port 8084.
<img width="530" height="329" alt="image" src="https://github.com/user-attachments/assets/2cc9e5cf-d4a0-49a0-951c-0a439f5752c5" />

#   3. Structure du projet
Cette organisation respecte l’architecture MVC et sépare proprement les entités, la couche DAO, la sécurité et les vues.
<img width="287" height="424" alt="image" src="https://github.com/user-attachments/assets/47f00196-75c6-4260-8b4a-2f333691c59f" />
<img width="274" height="273" alt="image" src="https://github.com/user-attachments/assets/09f611de-1bc6-4a95-8057-a95b3b8cb348" />

 #  4. Entité Product

Cette capture montre l’entité Product, qui représente les produits enregistrés dans la base de données. Elle contient les attributs id, name, price et quantity, accompagnés de validations JSR-303 pour assurer la cohérence des données. Cette classe est transformée en table H2 grâce à JPA et Hibernate.
<img width="326" height="285" alt="image" src="https://github.com/user-attachments/assets/71317113-4139-41de-86a4-cd1d9f19334e" />





# 5. Repository : ProductRepository

Cette capture illustre le repository ProductRepository, qui hérite de JpaRepository. Il fournit automatiquement toutes les opérations CRUD (ajout, suppression, modification, affichage) sans écrire de SQL. C’est la couche reliant l’application aux données.
<img width="553" height="188" alt="image" src="https://github.com/user-attachments/assets/775bd86b-3fa0-4859-8688-167279067797" />


# 6. Initialisation des données (CommandLineRunner)

Cette capture montre le CommandLineRunner, exécuté au démarrage de l’application. Il injecte automatiquement trois produits dans la base H2 afin de tester rapidement l’interface sans saisie manuelle.
<img width="635" height="270" alt="image" src="https://github.com/user-attachments/assets/eb92052d-b612-4b26-908e-fc47a645d2a9" />




# 7. Sécurité : Spring Security
Cette capture présente l’initialisation des utilisateurs dans Spring Security. Trois comptes (user1, user2 et admin) sont créés avec des rôles distincts. Cela permet de tester les autorisations et l’accès aux pages sécurisées.
<img width="734" height="101" alt="image" src="https://github.com/user-attachments/assets/b033209d-13f3-42ca-bf60-a3ed95680323" />





