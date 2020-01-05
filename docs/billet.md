# 20 choses à connaître quand on fait du Kubernetes

## Cartouche d'identification

 - Manifestation : CodeursEnSeine 2019
 - Lieu : Kindarena - Rouen
 - Conférence : [20 choses à connaitre quand on fait du Kubernetes](https://www.codeursenseine.com/2019/programme)
 - Horaire de la conférence : 16h40
 - Durée de la conférence : 45 minutes
 - Conférencier(s) : [Alain Regnier](https://fr.linkedin.com/in/alainregnier)
 - Audience : ~100 personnes
 - Auteur du billet : Nicolas KEMPF
 - Mots-clés : Kubernetes, Conteneurisation, Docker, Google Kubernetes Engine (GKE)
 - URL de l'illustration : ![Photo by chuttersnap on Unsplash](chuttersnap-fN603qcEA7g-unsplash.jpg)


## Support

**Indisponible**

## Résumé

### Introduction

En cette fin de journée de Codeurs En seine j'ai pu assister à cette conférence sur 20 bonnes pratiques à connaître quand on fait du kubernetes. Cette dernière était animée par Alain Regnier, CTO chez Alto Labs et certifié Google Developer Expert Cloud. 

La conférence commece donc par un bref rappel de ce qu'est un container, Docker et Kubernetes. Il nous présente aussi Google Kubernetes Engine, qui est un Kubernetes as a service, géré par Google et prêt pour la production. Plusieurs fois dans la conférence GKE sera utilisé pour illustrer certains exemples.

Après cette courte introduction s'en suit un déroulé de bonnes pratiques à mettre quand on fait du Kubernetes. 

### Top 20 des astuces sur Kubernetes! ###

1. Définir des alias pour kubectl

	En effet très pratique pour des commande qu'on utilise souvent afin d'éviter les erreurs ou encore pour éviter d'oublier la syntaxe.

2. Apprenez à spécifier le format de sortie de kubectl

	Très utile pour afficher en json afin de récupérer des élements spécifiques. Ou encore pour récupérer le YAML d'une ressource à des fins de débuggage. 

3. Regroupez plusieurs fichiers YAML en un avec le séparateur `-`

4. Utilisez le Google Cloud Shell sur GKE
	
	Il s'agit d'une petite VM avec un disque persistant et des outils courants. Présent directement dans la navigateur il permet un accès facile à tous les clusters GKE. 

5. Activez l'autocomplétion pour kubectl avec bash autocomplétion ou zsh

6. Utilisez kubectl proxy avec Web Preview sur GKE 
   
   Vu que tout dans kubernetes passe par une API REST vous pouvez créer un accès l'API via un port du cloud shell puis rendre ce port accessible au navigateur avec Web Preview.

7. Utilisez `kubectl top` pour visualiser les ressources utilisées par les pods et nodes 

6. Utilisez un *Ingress* pour exposer vos services 
   
   Un LoadBalancer étant limité, pas toujours disponible et cher. Il vaut mieux utiliser un Ingress. Il s'agit d'une collection de règles permmetant à une connexion externe d'atteindre des services à l'intérieur du docker. On peut donc y faire une terminaison SSL, du virtual Hosting ou encoure de séparer des chemins vers différents conteneurs

7. Ne déployez jamais vos microservices à la main

  - PAS DE KUBECTL RUN car on ne suit pas les dépendances

  - Utilisez toujours des YAML

  - Utilisez des outils de CI/CD comme Jenkins ou concourse

  - utilisez –record avec kubectl pour conserver la commande exécutée
    dans la 'annotation kubernetes.io

8. Stockez les fichiers YAML dans un repository 

  - Difficile de savoir quelle est la dernière version du YAML
  - Infrastructure as code
  - Considérez l'approche commit-then-Apply et utilisez des tags après
    vérification

9. Profitez de l'intégration StackDriver sur GKE 

  - permet de gérer les logs
  - Pas besoin de grafana/prometheys
  - Filtrage puissant

10. N'utilisez pas le default Namespace 

  - Les NS permettent de séparer les ressources en clusters virtuels sur
    un même clsuter Kubernetes

  - Trop facile de faire des bêtises quand on a plusieurs équipes ou
    projets

  - Utilisez les NS pour séparer les env : Dev, Staging

  - Spécifiez le NS directement dans le yaml ou avec le flag –namespace

  - les services sont accessibles par DNS

11. Utilisez port forward pour vous connecter à un POD sur le cluster

  - Etablissez une connexion depuis le cloud shell ou votre machine
    locale vers un pod à l'intérieur du cluster
  - Peut être aussi fait vers un service

12. Utilisez les Requests et les Limits 

  - Requets ce qu'un container est garanti d'avoir
  - Limits: le max de ressources qu'un container peut utiliser avant
    d'être restreint
  - Si au dessus de la CPU limit: le CPU sera artificiellement restreint
    mais pas de suppressions
  - Si au dessus de la Memory Limit: le container pourra etre supprimé
  - Les Requests sont notamment utilisées par le scheduler pour savoir
    ou scheduler le pod
  - Les Pods sans requests sont les premiers candidats pour être
    supprimés même si ils sont Healthy

13. Utilisez les RessourceQuota et LimitRange

  - Empêcher une équiper d'utilsier trop de ressources sur le cluster

14. Etudiez les daemonSet et StatefulSet même si pas besoin pour le moment

  - Les gens ont tendance à tout faire avec un deployment au départ mais
    pas forcément efficace et difficile

  - DaemonSet:
    
      - Chaque node a une copie du Pod (stockage..)
      - EPeut être restreint à certains Nodes

  - StatefulSet:
    
      - groupe de Pod avec des noms uniques ("pet" vs "cattle")
      - ordre garanti
      - Toujours le même stockage attaché (BD)

15. Utilisez les Probes pour les health checks 

  - Readliness Probes: permet à Kubernetes de savoir quand une
    application est prête à recevoir des requêtes
  - Liveness Probes: Permet à Kubernetes de savoir qu'une app est en vie

16. Utilisez les service de GCP depuis GKP

17. Apprenez à investiguer un Pod Coincé 

  - Vérifiez les logs
      - kubectl logs
      - kubectl describe

18. Apprenez à vous connecter sur un livepod 

  - kubectl exec -it podname -c





## Architecture et facteur qualité


	
