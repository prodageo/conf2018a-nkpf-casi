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

8. Ne déployez jamais vos microservices à la main

	Ne jamais déployer via un `kubectl run` car on ne peut pas suivre les dépendances. Toujours utiliser des YAML et des outils de CI/Cd. Utilisez –record avec kubectl pour conserver la commande exécuté dans l'annotation kubernetes.io

9. Stockez les fichiers YAML dans un repository 

10. Profitez de l'intégration StackDriver sur GKE qui permet de gérer les logs

11. N'utilisez pas le default Namespace 

	Il est trop facile de faire des erreurs entre plusieurs équipes. Les namespaces permettent de séparer les ressources en clusters virtuels sur un même cluster Kubernetes. Ils sont spécifiables dans le YAML et de plus accessibles via un DNS.

12. Utilisez port forward pour vous connecter à un Pod sur le cluster

	Permet d'établir une connexion depuis le cloud shell ou votre machine locale vers un pod ou un service à l'intérieur du cluster.

13. Utilisez les Requests et les Limits 

	Deux notions importantes mises en avant ici:
	- Requests ce qu'un container est garanti d'avoir comme ressources
	- Limits: le max de ressources qu'un container peut utiliser avant d'être restreint
	
	**Attention: Des Pods sans requests sont les premiers candidats pour être supprimés même si ils sont Healthy.**

14. Utilisez les RessourceQuota et LimitRange
	
	Utile pour empêcher une équipe d'utiliser trop de ressources sur le cluster.

15. Etudiez les daemonSet et StatefulSet 

	Par défaut our le controller Kubernetes on utilise le Deployment, cependant d'autres peuvent être utiles.
	- DaemonSet:
		- Chaque node a une copie du Pod 
		- Et peut être restreint à certains Nodes
	- StatefulSet:
		- Groupe de Pod avec des noms uniques ("pet" vs "cattle")
		- Ordre garanti
		- Toujours le même stockage attaché

16. Utilisez les Probes pour faire des health checks 
   
   Avec par exemple:
   - Readliness Probes qui indique si une application est prête à recevoir des requêtes.
   - Liveness Probes qui permet de savoir si une application est en vie

17. Utilisez les service de GCP depuis GKP

18. Apprenez à investiguer un Pod Coincé avec `kubectl logs` ou `kubectl describe`

19. Apprenez à vous connecter sur un livepod `kubectl exec -it podname -c`

Le lecteur attentif aura remarqué qu'il n'y a pas 20 points mais seulement 19. La conférence s'étant un peu allongée certains points ont été passés très rapidements voire passés.

## Architecture et facteur qualité


	
