# devops-app
# Build le projet

## Pre-requis

- Docker
- Docker Compose

## Étapes de Buid

1. Clonez le dépôt.
2. Exécutez la commande suivante dans le répertoire racine du projet :
   docker-compose up
Le projet sera build et le serveur démarrera par défaut sur le port 8060. Pour accéder au serveur, ouvrez [http://localhost:8060](http://localhost:8060) dans votre navigateur.

## Questions et Réponses

### Pourquoi devons-nous exécuter le conteneur avec l'option `-e` pour fournir les variables d'environnement ?
L'option `-e` est utilisée pour passer les variables d'environnement au conteneur, ce qui est crucial pour configurer le conteneur à l'exécution. En utilisant l'option `-e`, nous nous assurons que le conteneur dispose des paramètres nécessaires pour que l'application fonctionne correctement.

### Lorsque nous parlons de `/docker-entrypoint-initdb.d`, cela signifie à l'intérieur du conteneur, donc vous devez copier le contenu de votre répertoire dans le répertoire du conteneur.
Le répertoire `/docker-entrypoint-initdb.d` est utilisé pour configurer la base de données au démarrage du conteneur. Les scripts de ce répertoire s'exécutent au démarrage pour créer et remplir la base de données.

### Pourquoi devons-nous attacher un volume à notre conteneur PostgreSQL ?
Nous attachons un volume au conteneur PostgreSQL pour sauvegarder les données. Sans volume, les données sont perdues lorsque le conteneur s'arrête. Un volume permet de conserver les données sur la machine hôte, les maintenant ainsi en sécurité.

### Pourquoi avons-nous besoin d'une construction multi-étapes ?
Une construction multi-étapes aide à rendre l'image finale plus petite. Nous construisons l'application dans une première étape, puis nous copions uniquement les fichiers nécessaires dans l'étape finale. Cela permet de réduire la taille de l'image.

### Pourquoi avons-nous besoin d'un reverse proxy ?
Un reverse proxy dirige les requêtes vers le bon service backend. Il peut équilibrer la charge, router les requêtes par chemin et gérer le SSL. Il ajoute également des fonctionnalités de sécurité comme la limitation de débit et l'authentification.

### Pourquoi Docker Compose est-il si important ?
Docker Compose est important car il permet de définir et d'exécuter facilement des applications multi-conteneurs. Nous listons les services, réseaux et volumes dans un seul fichier et gérons l'application avec des commandes simples.

### Que fait la commande `mvn clean verify` ?
`mvn clean verify` est une commande Maven qui nettoie le projet, compile le code, exécute les tests et empaquette l'application. Elle est utilisée pour s'assurer que l'application est prête à être déployée.

### Qu'est-ce que Testcontainers ?
Testcontainers est une bibliothèque Java qui utilise des conteneurs Docker pour les tests. Elle aide à créer et gérer des conteneurs dans les tests, facilitant ainsi les tests des applications avec des bases de données et d'autres services.

### Pourquoi sécuriser les variables dans GitHub ?
Sécuriser les variables dans GitHub est important pour garder les informations sensibles comme les clés API et les mots de passe en sécurité. Si ces informations sont exposées, des utilisateurs non autorisés pourraient accéder à l'application et la compromettre.
