# Préparer la VM

Créer un repertoire app
```
mkdir app
```

Cloner le projet nodejs à l'intérieur de ce repertoire
```
git clone <url du dépot github> app
```

Télécharger l'image docker de debian qui sera l'image de base utilisée pour le conteneur
```
docker pull debian
```

Lancer le conteneur en précisant le port à exposer et mapper le repertoire de l'application dans le conteneur
```
docker run -itd --name nodejs-ctnr -p 3000:3000 -v ./app:/app debian
```

Se déplacer dans le conteneur
```
docker exec -it nodejs-ctnr bash
```

# Installer les prérequis et lancer l'application

Installation de `nodejs` et `npm`
```
apt-get update && apt-get install -y nodejs npm
```

Se déplacer dans le repertoire de l'application
```
cd app
```

Installer les dépendances de l'application (nestjs et autres...):
- Rassurez vous d'être à la racine du dossier applicatid (app) car cette commande fait appel au fichier `package.json` pour le téléchargement des dépendences.
- Après l'exécution de cette commande vous verez apparaître un nouveau dossier `node_modules` contenant toutes les dépendances instalées.
```
npm install
```

Lancer l'application
```
npm start
```

Vous pouvez accéder à l'application via le navigateur de votre `machine hôte` à l'url suivante
```
<adresse ip de la VM>:3000
```

Ou alors directemennt sur `la VM` si vous avez une `installation graphique`:
```
localhost:3000
```

**_⚠️Points d'attention_**: 
- Lors de ces différentes étapes vous pourrez avoir des erreurs, rassurez vous de tous les régler en vous rassurant que vous suivez bien les étapes de ce tutoriel.
- Vous pouvez également voir le détail des logs dans le terminal après le lancement de l'application
- Pour arrêter l'application tapez juste ```CTRL+V```
