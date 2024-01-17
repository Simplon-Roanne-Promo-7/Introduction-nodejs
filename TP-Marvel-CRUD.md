# TP Marvel CRUD

Bienvenue dans le projet Marvel CRUD ! L'objectif de ce projet est de vous apprendre à créer une application web pour gérer les personnages et les équipes de l'univers Marvel en utilisant NodeJS, Express, Mustache, MySQL, Nodemon et Pico.css.

## 1. Initialisation du projet

Dans un nouveau projet, une fois que vous avez lancé `npm init`, installez les paquets suivants :
`npm install express mustache mustache-express mysql @picocss/pico`

Picocss est un framework CSS très léger, il est très simple à utiliser et ne contient que le strict minimum pour faire du CSS. https://picocss.com/docs/

Mustache est un moteur de template qui permet de générer du HTML à partir de données Dans nos routes.
Mustache-express est un paquet qui permet d'utiliser Mustache avec Express.
https://www.npmjs.com/package/mustache
https://www.npmjs.com/package/mustache-express

Nous utilisons ces paquets afin de simplifier au maximum cet exercice.

## 2. Création de la base de données

La base de données sera elle aussi très simple, elle contiendra deux tables : "personnages" et "equipes".
Histoire de vous rafraîchir la mémoire, Nous allons créer la base de données dans phpMyAdmin à la main !

Créer la base de données "marvel"

Créer la table "personnages"
Ajoutez les colonnes suivantes :
id : INT, clé primaire, auto-incrément
nom : VARCHAR(255), non nul
description : TEXT, nullable
photo : VARCHAR(255), nullable
equipe_id : INT, nullable

Créer la table "equipes"
Ajoutez les colonnes suivantes :
id : INT, clé primaire, auto-incrément
nom : VARCHAR(255), non nul

Ajoutez une relation entre les deux tables avec une clé étrangère (Eh oui, symfony n'est pas là pour vous macher le travail !)

## 3. Connexion à la base de données

`npm install mysql`

Créez un fichier "database.js" à la racine du projet, et complétez le code suivant :

```javascript
// Importer le module MySQL
const mysql = require("mysql");

// Créer une connexion à la base de données en utilisant les paramètres de connexion
// https://www.npmjs.com/package/mysql#introduction

// Établir la connexion à la base de données

// Exporter la connexion pour pouvoir l'utiliser dans d'autres modules
```

## 4. Configuration du serveur Express et du moteur de template Mustache

- Créez un fichier `index.js` dans le dossier du projet.
- Créez un dossier `views` qui contiendra les fichiers de template Mustache.
- Ajoutez le code suivant pour configurer le serveur Express et le moteur de template Mustache :

```javascript
const express = require("express");
const mustacheExpress = require("mustache-express");
const app = express();

/**
 * Configuration de mustache
 * comme moteur de template
 * pour l'extension .mustache
 */
app.engine("mustache", mustacheExpress());
app.set("view engine", "mustache");
app.set("views", __dirname + "/views");

/**
 * Configuration de express
 * pour récupérer les données d'un formulaire
 * et pour servir les fichiers statiques
 * (css, js, images, etc.)
 */
app.use(express.static("public"));
app.use(express.urlencoded({ extended: true }));

// Routes à ajouter ici

app.listen(3000, () => {
  console.log("Server is running on port 3000");
});
```

Vous ajouterez les routes dans la partie `// Routes à ajouter ici` pour les exercices suivants.

## 5. Affichage de la liste des personnages avec Mustache

- Créez une route GET `/personnages` qui affiche la liste des personnages avec leur équipe
- Créez une route GET `/personnages/:id` qui affiche le détail d'un personnage avec son équipe

Créez un fichier `personnages.mustache` dans le dossier `views` et utilisez le pour afficher le rendu de la liste des personnages dans la route `/personnages`. Ne mettez aucun code html dans votre fichier `index.js`, tout doit être dans les fichiers de template.
Même chose pour la route `/personnages/:id` qui doit afficher le détail d'un personnage.

Il vous faut utiliser le fichier `database.js` en utilisant la constante qui contient la connexion à la base de données que vous avez exporté.

Pour la requête SQL, vous pouvez utiliser la méthode `query` de la connexion à la base de données en code SQL pur.
https://www.npmjs.com/package/mysql#performing-queries

## 6. Ajout d'un personnage

- Ajoutez une route pour afficher le formulaire de création de personnages et d'équipes dans le fichier index.js
- Créez un fichier create.mustache dans le dossier views et ajoutez le code HTML pour le formulaire de création de personnages et d'équipes.
- Ajoutez une route pour gérer la soumission du formulaire et insérer les données dans la base de données.

à la fin de l'insertion, vous pouvez rediriger l'utilisateur vers la liste des personnages avec la méthode `redirect` de la réponse.
https://expressjs.com/en/4x/api.html#res.redirect

## 7. Finalisation du CRUD

- Ajoutez le reste des routes pour finir ce CRUD : Edit et Delete
- Ajoutez tout le CRUD pour la gestion des équipes et l'assignation des Héros à une équipe de héros

# Conclusion

À travers ce TP Marvel CRUD, nous avons revisité les fondamentaux du CRUD en reprenant une approche plus basique, sans utiliser d'ORM comme sur Symfony, pour renforcer ou rafraîchir vos acquis datant de la POO PHP. Ce projet a servi de premier pas significatif sur Node.js pour préparer le terrain à des concepts plus avancés.

L'expérience acquise ici sert de base solide pour notre prochaine exploration : le NoSQL. Dans le TP suivant, nous nous concentrerons sur MongoDB avec Mongoose, où vous pourrez appliquer et étendre votre compréhension des bases de données dans un contexte NoSQL. Cette progression logique, de MySQL à MongoDB, vous permet de vous adapter à diverses situations et exigences de stockage de données dans le monde du développement web.

Nos aventures précédentes avec Symfony vous ont dotés d'une perspective polyvalente, et ce retour aux sources est une étape clé pour solidifier votre savoir-faire technique. Elle présente une transition parfaite vers l'agilité et la performance offertes par le NoSQL.
