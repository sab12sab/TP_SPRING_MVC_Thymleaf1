# TP Spring MVC — Gestion des Produits avec Spring Boot, JPA, Thymeleaf et Spring Security

##  Objectif du projet
Le but de ce TP est de développer une application Web basée sur Spring Boot permettant de gérer des produits via un CRUD complet, d’appliquer la validation des données, d’utiliser Thymeleaf pour l’interface et de sécuriser l’accès aux pages avec Spring Security.



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



#  2. Configuration de l’application

## ⚙ Configuration H2 & Spring Boot
Cette configuration active une base H2 en mémoire, met automatiquement à jour les tables selon les entités et démarre l’application sur le port 8084.
<img width="530" height="329" alt="image" src="https://github.com/user-attachments/assets/2cc9e5cf-d4a0-49a0-951c-0a439f5752c5" />

#   3. Structure du projet
Cette organisation respecte l’architecture MVC et sépare proprement les entités, la couche DAO, la sécurité et les vues.
<img width="287" height="424" alt="image" src="https://github.com/user-attachments/assets/47f00196-75c6-4260-8b4a-2f333691c59f" />
<img width="274" height="273" alt="image" src="https://github.com/user-attachments/assets/09f611de-1bc6-4a95-8057-a95b3b8cb348" />

 #  4. Entité Product

Cette capture montre l’entité Product, qui représente les produits enregistrés dans la base de données. 
Elle contient les attributs id, name, price et quantity, accompagnés de validations JSR-303 pour assurer la cohérence des données. 
Cette classe est transformée en table H2 grâce à JPA et Hibernate.
<img width="326" height="285" alt="image" src="https://github.com/user-attachments/assets/71317113-4139-41de-86a4-cd1d9f19334e" />





# 5. Repository : ProductRepository

Cette capture illustre le repository ProductRepository, qui hérite de JpaRepository. 
Il fournit automatiquement toutes les opérations CRUD (ajout, suppression, modification, affichage) sans écrire de SQL. 
C’est la couche reliant l’application aux données.
<img width="553" height="188" alt="image" src="https://github.com/user-attachments/assets/775bd86b-3fa0-4859-8688-167279067797" />


# 6. Initialisation des données (CommandLineRunner)

Cette capture montre le CommandLineRunner, exécuté au démarrage de l’application. 
Il injecte automatiquement trois produits dans la base H2 afin de tester rapidement l’interface sans saisie manuelle.


<img width="635" height="270" alt="image" src="https://github.com/user-attachments/assets/eb92052d-b612-4b26-908e-fc47a645d2a9" />




# 7. Sécurité : Spring Security
Cette capture présente l’initialisation des utilisateurs dans Spring Security. Trois comptes (user1, user2 et admin) sont créés avec des rôles distincts. 
Cela permet de tester les autorisations et l’accès aux pages sécurisées.


<img width="734" height="101" alt="image" src="https://github.com/user-attachments/assets/b033209d-13f3-42ca-bf60-a3ed95680323" />





### 8. password_encoder.png — BCryptPasswordEncoder  
Cette capture montre la configuration du `PasswordEncoder` utilisant l’algorithme **BCrypt**.  
Il sert à chiffrer les mots de passe avant de les stocker, ce qui garantit une sécurité renforcée des informations utilisateurs.  
BCrypt est l’encodeur recommandé par Spring Security pour la protection des mots de passe.



### 9. access_rules.png — Règles d’accès Spring Security  
Cette capture présente les règles d’accès configurées dans `SecurityConfig`.  
Certaines ressources comme **/public/** et **/webjars/** sont accessibles sans authentification, alors que toutes les autres pages nécessitent une connexion.  
En cas d’accès à une ressource protégée sans permis, l’utilisateur est automatiquement redirigé vers une page d’erreur dédiée.



### 10. not_authorized.png — Page d’accès refusé  
Cette capture montre la page **Not Authorized**, affichée lorsqu'un utilisateur tente d’accéder à une page pour laquelle il n’a pas les droits.  
Elle avertit clairement l’utilisateur et améliore l’expérience grâce à un message explicatif adapté.



### 11. layout.png — Layout principal Thymeleaf  
Cette capture illustre le layout principal de l'application, qui sert de modèle pour toutes les pages.  
Il contient la barre de navigation, le nom de l’utilisateur connecté (affiché via Spring Security) et une zone dynamique gérée avec `layout:fragment`.  
Toutes les pages héritent automatiquement de ce layout pour maintenir une interface cohérente et professionnelle.

### 12. products_list.png — Liste des produits  
Cette capture montre la page affichant la liste de tous les produits stockés dans la base de données.  
On y retrouve un tableau contenant l’identifiant, le nom, le prix et la quantité de chaque produit.  
Le bouton **Delete** n’apparaît que pour les utilisateurs ayant le rôle **ADMIN**, grâce à la directive `sec:authorize`.


### 13. form_add.png — Formulaire d’ajout  
Cette capture représente la page permettant d’ajouter ou de modifier un produit.  
Le formulaire utilise les validations Thymeleaf pour afficher automatiquement les erreurs (comme un nom trop court ou une quantité invalide), ce qui améliore la qualité de la saisie utilisateur.


### 1️4. login.png — Page de connexion  
Cette capture montre la page de connexion personnalisée de l’application.  
Elle fonctionne entièrement avec Spring Security et respecte les champs obligatoires **username** et **password**.  
Cette page permet d’authentifier l’utilisateur avant qu’il accède aux fonctionnalités protégées.



### 1️5. project_structure.png — Structure du projet  
Cette capture montre l’arborescence générale du projet dans l’IDE.  
Elle met en avant l’organisation MVC : entités, repository, sécurité, démarrage Spring Boot, templates Thymeleaf et fichiers de configuration.  
Cette structure respecte les bonnes pratiques recommandées par Spring Boot.



### 1️6. h2_console.png — Console H2  
Cette capture illustre l’accès à la console H2 intégrée.  
Elle permet d’examiner la structure de la table `Product`, d’inspecter les données enregistrées et de vérifier le fonctionnement de JPA/Hibernate.  
C’est un outil essentiel pour le débogage et la compréhension du schéma relationnel.






