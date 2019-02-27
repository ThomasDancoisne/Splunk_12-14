# Splunk_12-14

## Workshops

### Stockage

Exemples de fichiers de log : https://github.com/ThomasDancoisne/Splunk_12-14

Settings > Add data > Upload from my computer

### requêtage

N'importe quelle app > onglet search

Calculer le temps de réponse moyen lors d’un login

Trouver l’utilisateur ayant mis le plus de temps à se loguer

Lister tous les utilisateurs ayant échoué à se connecter (status >= 400)

Bonus : 
Utiliser le lookup status_by_code.csv pour expliciter les erreurs



### Restitution

Suivre l’évolution du nombre de logins au fil du temps dans un graphique en lignes
Faire de même découpé par utilisateur
Enregistrer le panneau dans un nouveau dashboard
Ajouter un sélecteur d’utilisateur et un sélecteur de temps
Relier le panneau aux sélecteurs

Dans un nouveau dashboard, faire de même pour suivre l’évolution des codes retour au fil du temps dans un histogramme en barres
Ajouter un sélecteur de code retour et un sélecteur de temps

Tracer le nombre de requêtes que VOUS avez fait au cours du temps découpé par méthode (index=_internal sourcetype=splunk_ui_access)
Trouver le navigateur le plus utilisé

Index=_introspection  suivre l’état des containers splunk (host/process)
