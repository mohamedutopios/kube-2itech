Créer un pod Kubernetes nommé shared-volume-pod contenant deux conteneurs :
Le premier conteneur utilise l’image busybox.
Il écrit toutes les 5 secondes un fichier index.html contenant la date et un message dans un répertoire /usr/share/data.
Le deuxième conteneur utilise l’image nginx.
Il sert en HTTP ce fichier index.html via le chemin /usr/share/nginx/html.
Les deux conteneurs doivent partager un volume de type emptyDir monté à leurs emplacements respectifs.
Aucun service ne doit être créé. Une fois le pod déployé, utilisez la commande kubectl port-forward pour accéder au serveur nginx sur http://localhost:8080.