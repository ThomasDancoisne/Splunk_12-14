# Splunk

## Documentation

* [Search Reference](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference)
* [Command List](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/ListOfSearchCommands)
* [PDF: quick reference guide](https://www.splunk.com/pdfs/solution-guides/splunk-quick-reference-guide.pdf)
* [PDF: Search command cheatsheat](http://wiki.splunk.com/images/a/a3/Splunk_4.x_cheatsheet.pdf)

## Aller plus loin

* [Formations Splunk](https://www.splunk.com/fr_fr/view/education/SP-CAAAAH9)
* [Splunk Fundamentals 1 (gratuit en ligne)](https://www.splunk.com/en_us/training/courses/splunk-fundamentals-1.html)
* [CGI Splunk community (Grand Sud)](https://ensemble.ent.cgi.com/business/260253/SitePages/Accueil.aspx)


# Mise en pratique

## 1. Stockage

[Exemples de fichiers de log](./exemples/)

Pour ajouter un fichier, un fois connecté se rendre, dans la barre d'en-tête, dans le menu : **Settings > Add data > Upload from my computer**

## 2. Le requêtage et la transformation 

Si ce n'est pas déjà le cas, retournez dans l'onglet **Search** de l'application **Search & Reporting** (via la barre d'en-tête)

### Calculer le temps de réponse moyen lors d’un login

Les données se trouve dans l'index **idx_apache**. Première étape remonter les evénement pour voir le format

```
index="idx_apache"
```

Maintenant utilisez la commande ```stats``` pour calculer le temps moyen d'éxecution d'un login.
[Doc de la commande stats](https://docs.splunk.com/Documentation/Splunk/latest/SearchReference/Stats)


### Trouver l’utilisateur ayant mis le plus de temps à se loguer

Pour cela la commande ```top``` est un bon candidat ou la commande ```sort```.

### Lister tous les utilisateurs ayant échoué à se connecter

On va donc regarder les requête en erreur (status >= 400) pour un login.

### Bonus : Utiliser le lookup status_by_code.csv pour expliciter les erreurs

Tips: regardez du coté de la commande ```lookup```


## 3. Restitution

### Analyse des logs de l'interface Web de Splunk

Les données qui nous intéresse se trouve dans les logs internes de Splunk

```
index="_internal" sourcetype="splunkd_ui_access"
```

#### Code status

Maintenant que vous avez les événements, créez un graphique affichant l'évolution dans le temps du status de retour des requêtes web sur Splunk. Ensuite ajoutez le dans un nouveau dashboard.

Une fois ce dashboard créé ajoutez un sélecteur de temps et liez le à votre graphique.

#### Requête par utilisateur

Créez un autre graphique pour suivre le nombre de requêtes que **vous** avez fait au cours du temps découpé par méthode

Ajoutez le au dashboard que vous aviez précédemment créé. Et lié au sélecteur de temps qu'il contient.

#### Bonus

* Trouver le navigateur le plus utilisé
* Lister les dernière erreur survenue

### Suivre l'état des Processus Splunk

Pour accéder au données :

```
index="_introspection" sourcetype=splunk_resource_usage
```

#### TODO:

* Graphez l'utilisation CPU et Mémoire du serveur
* Lister tous les processus et afficher dans un tableau leurs PID et depuis combien de temps ils sont lancé.
