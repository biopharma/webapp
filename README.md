# Biopharma-intranet
Code source se la demo biopharma-intranet-2018.

# Prérequis
La demo a été réalisée sur un serveur debian-9.4.0. Les pré-requis à installer se trouvent dans le fichier setup.sh, notamment Jenkins et Docker.

# Mise en place Jenkins
Par défaut, Jenkins sera accessible sur le port 8080. Le mot de passe du compte admin est généré automatiquement à cet emplacement ~/.jenkins/secrets/initialAdminPassword. Créer un utilisateur et installer les plugins recommandés par Jenkins.
On va autoriser le user Jenkins à utiliser Docker sur le serveur:
  sudo usermod -a -G docker jenkins
On va également installer deux plugins sur jenkins (Manage Jenkins => Manage plugin => Available) :
  - Publish Over SSH : pour le déploiement sur le serveur de production en ssh
  - Blue Ocean : la nouvelle interface pour visualiser les démploiements
Créer un projet test, de type Multibranch Pipeline => Branch Sources = GitHub => choisir owner + repository

# Webhooks
Se rendre sur son compte github => Settings => Developer settings => personnal access tokens => generate (en autorisant  cocher admin:repo_hook)
Se rendre ensuite dans Jenkins => credentials => Jenkins => Manage jenkins => Configure System => add github server :
add credentials => jenkins => Kind = Secret Text => 
  Secret = token de GitHub
  ID + Description = github_credentials
On peut alors vérifier sur GitHub, dans les settings de notre projet => Webhooks. Si notre serveur jenkins n'est pas accessible depuis internet, on peut utiliser l'utilitaire ngrok, présent à la racine du projet, pour créer un tunel avec une url publique aléatoire:
  ./ngrok http 8080
Ajuster ensuite l'url du hook dans github.
