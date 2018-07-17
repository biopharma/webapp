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
  - Blue Ocean : la nouvelle intefarce de visualisation des déploiements

# Mise en place Jenkins
