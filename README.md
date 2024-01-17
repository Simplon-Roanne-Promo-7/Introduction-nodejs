### Introduction à NodeJS

Présentation : https://docs.google.com/presentation/d/1ONt37sT6kANSkq8qx9jVX3Ubfex4m3TUGma6n0yJwgQ/edit?usp=sharing

# Exercice découverte

## 1. Installe NodeJS et NPM

Pour commencer, rendez-vous sur la page officielle de NodeJS.org et téléchargez la version LTS ( qui veut dire la dernière version stable ) pour Windows ou votre plateforme.
L'installeur spécial Windows installe à la fois NodeJS et NPM.

L'installation de NodeJS va ajouter la commande `node` dans Powershell et Vscode.

NPM permet d'ajouter des librairies, que l'on appelle 'paquets' et qui finirons dans vos dossiers 'node modules', c'est la même chose que le vendor des projets php.

Vérifiez l'installation avec `node -v` et `npm -v` dans un terminal pour afficher les versions installées.

## 2. Initialisayion du projet

Ouvrez un nouveau dossier vide dans VSCode.
Dans le terminal, tapez la commande : `npm init` et suivez les instructions pour créer un fichier `package.json`.

Le but du fichier `package.json` est de contenir la liste des librairies installées dans votre projet.

## 3. Installe le paquet ExpressJS

`npm install express`

Créez un fichier index.js à la racine du projet, et copiez collez le code suivant :

https://expressjs.com/en/starter/hello-world.html

Ensuite dans un nouveau terminal dans VSCode, il n'y as plus qu'à lancer la commande :
`node index.js`

Ceci va executer le programme NodeJS. Est ce que ça marche ?
Si ça marche, tu devrais pouvoir aller à l'adresse `http://localhost:3000`

## 4. Première route GET /ma-page

Le but de cet exercice est très simple, il suffit créer une deuxieme route en GET qui aura pour adresse
"/ma-page" donc qui donnera l'url `http://localhost:3000/ma-page`.
vous pouvez mettre ce que vous voulez dans la réponse, du texte, du html, du json, un console.log, etc...
Lisez la documentation pour vous aider : https://expressjs.com/en/starter/basic-routing.html

> ⚠️ **Attention** ⚠️
> Lorsque vous modifiez le code, il faut relancer le serveur en faisant CTRL+C dans le terminal et relancer `node index.js`
> Vous pouvez aussi installer le paquet nodemon qui permet de relancer automatiquement le serveur à chaque modification du code.

## 5. Ajoutons une route POST avec un formulaire

Créez une route GET qui aura pour adresse "/mon-formulaire" donc qui donnera l'url `http://localhost:3000/mon-formulaire`.
Cette route doit afficher un formulaire HTML avec un champ texte et un bouton submit.
Lorsque l'on soumet le formulaire en POST, il faut afficher le contenu du champ texte dans la réponse d'une nouvelle route POST "/traitement-formulaire".

> ⚠️ **Attention** ⚠️
> Pour récupérer les données du formulaire, il faut utiliser le paquet `body-parser` et le middleware `urlencoded`.
> https://expressjs.com/en/resources/middleware/body-parser.html

Pour vous aider dans votre debug, utilisez le try catch pour afficher les erreurs :
https://expressjs.com/en/guide/error-handling.html

# Mini TP : Marvel CRUD

[Clickez ici pour la suite](./TP-Marvel-CRUD.md)
