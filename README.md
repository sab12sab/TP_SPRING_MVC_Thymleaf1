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

L’entité Product représente les produits gérés par l'application. Elle intègre la validation JSR-303 et utilise Lombok pour générer automatiquement getters, setters et constructeurs.



# 5. Repository : ProductRepository

Le repository étend JpaRepository, ce qui fournit automatiquement toutes les opérations CRUD :

# 6. Initialisation des données (CommandLineRunner)

Lors du démarrage de l’application, des produits sont insérés automatiquement dans la base :
