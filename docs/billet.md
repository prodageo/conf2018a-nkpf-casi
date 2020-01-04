# 20 choses à connaître quand on fait du Kubernetes

## Cartouche d'identification

 - Manifestation : CodeursEnSeine 2019
 - Lieu : Kindarena - Rouen
 - Conférence : [20 choses à connaitre quand on fait du Kubernetes](https://www.codeursenseine.com/2019/programme)
 - Horaire de la conférence : 16h40
 - Durée de la conférence : 45 minutes
 - Conférencier(s) : [Alain Regnier](https://fr.linkedin.com/in/alainregnier)
 - Audience : 
 - Auteur du billet : Nicolas KEMPF
 - Mots-clés : Kubernetes, Conteneurisation, Docker, Google Kubernetes Engine (GKE)
 - URL de l'illustration : ![Photo by chuttersnap on Unsplash](chuttersnap-fN603qcEA7g-unsplash.jpg)


## Support

**Indisponible**

## Résumé

### Intro ###

GKE = offre de google kubernetes

GDG : google developer group = meetups qui parlent des techs google

#### Rappels sur les containers ####

Blabla le truc classique vs le normal vs les vms vs les conteneurs

#### Kubernetes? ####

Solution Open Source pour orchestrer des containers

Au départ crée par google et basée sur Borg

**Principe : déclarer la cible à atteindre et s'y maintenir**

#### GKE ####

  - Kubernetes as a service
  - Managé par google
  - Basé sur l'exp de google depuis 12 ans (4 G de conteneurs démarrés
    chaque semaine)
  - prêt pour la prod
  - haute dispo, montée en charge ..
  - montée en version
  - masters gratuits




### 20 choses ###

#### Définir des alias autour de kubectl ####

  - Parce qu'on l'utilise beaucouo
  - Parce que parfois on fait des erreurs dans les commandes et qu'on
    tape à nouveau
  - Parce qu'on oublie la syntaxe

#### Apprenez à spécifier le format de sortie de kubectl ####

  - Afficher en json et récupérer des éléments spécifiques

  - Récupérer le yaml d'une ressource, très utile pour débugger car tout
    est déclaré en yaml dans kubernetes

  - Egalement vrai pour les commandes gcloud/GKE

#### Regroupez plusieurs fichiers yaml en un ####

Plusieurs fichiers peuvent être regroupés ensemble en utilisant le
séparateur "—"

#### Utilisez le Google Cloud Shell sur GKE ####

  - Petite VM avec un disque persistant et les outils courants
  - Accès facile à vos clsuters GKE
  - Directement dans le navigateur
  - Gratuit
  - Editeur intégré
  - Partagé par tous les projets

#### Activez l'autocomplétion pour kubectl ####

bash autocomplétion, zsh…

#### Utilisez kubectl proxy avec Web Preview sur GKE ####

TOut dans kubernetes passe par une API REST

  - Créez un accès à la Kubernetes API via un port du cloud shell

  - Rendre ce port accessible au navigateur avec Web Preview

#### Utilisez kubectl top ####

  - Permet d'afficher les ressources utilisées par les pods et les nodes

  - Vérifiez que heapster est installé sur le cluster

#### Utilisez un *ingress* pour exposer vos services ####

Avant:

  - Service Type=LoadBalancer est limité, pas toujours dispo et cher

  - *Ingress* Collection de règles permmetant à une connexion externe
    d'atteindre des services à l'intérieur du docker

  - Terminaison SSL

  - Virtual Hosting

  - Chemins Multiples

  - Sur GKE le service doit être de type NodePort ou LoadBalancer

  - Sur GKE utilisez \* comme wildcard

Permet de spliter des chemins vers différents conteneurs

#### Ne déployez jamais vos microservices à la main ####

  - PAS DE KUBECTL RUN car on ne suit pas les dépendances

  - Utilisez toujours des YAML

  - Utilisez des outils de CI/CD comme Jenkins ou concourse

  - utilisez –record avec kubectl pour conserver la commande exécutée
    dans la 'annotation kubernetes.io

#### Stockez les fichiers YAML dans un repository ####

  - Difficile de savoir quelle est la dernière version du YAML
  - Infrastructure as code
  - Considérez l'approche commit-then-Apply et utilisez des tags après
    vérification

#### Profitez de l'intégration StackDriver sur GKE ####

  - permet de gérer les logs
  - Pas besoin de grafana/prometheys
  - Filtrage puissant

#### N'utilisez pas le default Namespace ####

  - Les NS permettent de séparer les ressources en clusters virtuels sur
    un même clsuter Kubernetes

  - Trop facile de faire des bêtises quand on a plusieurs équipes ou
    projets

  - Utilisez les NS pour séparer les env : Dev, Staging

  - Spécifiez le NS directement dans le yaml ou avec le flag –namespace

  - les services sont accessibles par DNS

#### Utilisez port forward pour vous connecter à un POD sur le cluster ####

  - Etablissez une connexion depuis le cloud shell ou votre machine
    locale vers un pod à l'intérieur du cluster
  - Peut être aussi fait vers un service

#### Utilisez les Requests et les Limits ####

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

#### Utilisez les RessourceQuota et LimitRange ####

  - Empêcher une équiper d'utilsier trop de ressources sur le cluster

#### Etudiez les daemonSet et StatefulSet même si pas besoin pour le moment ####

  - Les gens ont tendance à tout faire avec un deployment au départ mais
    pas forcément efficace et difficile

  - DaemonSet:
    
      - Chaque node a une copie du Pod (stockage..)
      - EPeut être restreint à certains Nodes

  - StatefulSet:
    
      - groupe de Pod avec des noms uniques ("pet" vs "cattle")
      - ordre garanti
      - Toujours le même stockage attaché (BD)

#### Utilisez les Probes pour les health checks ####

  - Readliness Probes: permet à Kubernetes de savoir quand une
    application est prête à recevoir des requêtes
  - Liveness Probes: Permet à Kubernetes de savoir qu'une app est en vie

#### Slide passée ####

#### Utilisez les service de GCP depuis GKP ####

#### Apprenez à investiguer un Pod Coincé ####

  - Vérifiez les logs
      - kubectl logs
      - kubectl describe

#### Apprenez à vous connecter sur un livepod ####

  - kubectl exec -it podname -c




## Architecture et facteur qualité

...
	
