# Exercice 1 : Validation d’acquis

### 1. Qu’est ce qu’un conteneur ?
   Un conteneur est une unité de logiciel qui regroupe le code et toutes ses dépendances afin que l'application s'exécute rapidement et de manière fiable d'un environnement informatique à un autre.

### 2. Est-ce que Docker a inventé les conteneurs Linux ? Qu’a apporté Docker à cette technologie ?
   Docker n'a pas inventé les conteneurs Linux.
   Il a simplifié leur utilisation grâce à une interface utilisateur conviviale, des outils de gestion, et un écosystème riche d'images et de registres.

### 3. Pourquoi est-ce que Docker est particulièrement pensé et adapté pour la conteneurisation de processus sans états ?
   Car il permet de créer des environnements isolés et éphémères, facilement reproductibles.

### 4. Quel artefact distribue-t-on et déploie-t-on dans le workflow de Docker ? Quelles propriétés désirables doit-il avoir ?
   On distribue et déploie des images Docker. Elles doivent être petites, sécurisées et facilement versionnables.

### 5. Quelle est la différence entre les commandes `docker run` et `docker exec` ?
   `docker run` crée et lance un nouveau conteneur, tandis que `docker exec` exécute une commande dans un conteneur existant en cours d'exécution.

### 6. Peut-on lancer des processus supplémentaires dans un même conteneur docker en cours d’execution ?
   Oui en utilisant la commande `docker exec`.

### 7. Pourquoi est-il fortement recommandé d’utiliser un tag précis d’une image et de ne pas utiliser le tag `latest` dans un projet Docker ?
   Car le tag `latest` peut changer et introduire des incompatibilités ou des bugs inattendus.

### 8. Décrire le résultat de cette commande : `docker run -d -p 9001:80 --name my-php -v "$PWD":/var/www/html php:7.2-apache`.
   Cette commande se divise en 5 parties :
       - Elle lance un conteneur en arrière-plan (`-d`), 
       - Elle expose le port 80 du conteneur sur le port 9001 de l'hôte (`-p 9001:80`), 
       - Elle nomme le conteneur `my-php` (`--name my-php`),
       - Elle monte le répertoire courant de l'hôte dans `/var/www/html` du conteneur (`-v "$PWD":/var/www/html`),
       - ceci en utilisant l'image `php:7.2-apache`.

### 9. Avec quelle commande docker peut-on arrêter tous les conteneurs ?
   `docker stop $(docker ps -a -q)`

### 10. Quelles précautions doit-on prendre pour construire une image afin de la garder de petite taille et faciliter sa reconstruction ?
    Utiliser des images de base minimalistes, nettoyer les fichiers temporaires et les caches, utiliser des instructions `COPY` et `RUN` et éviter d'installer des packages inutiles.

### 11. Lorsqu’un conteneur s’arrête, tout ce qu’il a pu écrire sur le disque ou en mémoire est perdu. Vrai ou faux ? Pourquoi ?
    Cela va dépendre si les données écrites sur le disque persistent, si elles ont été stockées dans un volume ou une bind mount par exemple. Sans ces derniers, les données sont perdues lorsque le conteneur s'arrête. Donc c'est faux.

### 12. Lorsqu’une image est créée, elle ne peut plus être modifiée. Vrai ou faux ?
    Faux, de nouvelles couches peuvent être créé au-dessus de l'image existante, mais l'image originale reste immuable.

### 13. Comment peut-on publier et obtenir facilement des images ?
    On peut utiliser Docker Hub ou un registre privé.

### 14. Comment s’appelle l’image de plus petite taille possible ? Que contient-elle ?
    L'image `scratch` qui ne contient rien par défaut.

### 15. Par quel moyen le client docker communique avec le serveur dockerd ? Est-il possible de communiquer avec le serveur via le protocole HTTP ? Pourquoi ?
    Le client Docker communique avec le démon Docker (dockerd) via une API REST sur une socket UNIX ou TCP. 
    Oui, il est possible de communiquer via HTTP en configurant dockerd pour écouter sur une interface TCP.

### 16. Un conteneur doit lancer un processus par défaut que l’on pourra override à l’exécution. Quelle commande faut-il utiliser pour lancer ce processus : `CMD` ou `ENTRYPOINT` ?
    Utiliser `ENTRYPOINT` pour définir le processus principal et `CMD` pour les arguments par défaut.
