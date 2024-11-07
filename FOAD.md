Théo CHANNAROND 
Mehdi BEN CHEIKH

### Composants AWS utilisés

1. **VPC (Virtual Private Cloud)**  
   Le VPC permet de créer un réseau isolé où l’on peut gérer des ressources AWS en toute sécurité. Cela inclut des sous-réseaux publics et privés pour séparer les accès externes et internes, réduisant ainsi la surface d'attaque et augmentant la sécurité de l’application.

2. **Public Subnet et Private Subnet**  
   - **Public Subnet** : Utilisé pour héberger les services qui nécessitent un accès direct depuis l'Internet, comme l'Elastic Load Balancer (ELB) et le NAT Gateway. Cela permet de gérer les connexions entrantes et de rediriger le trafic vers les instances dans le sous-réseau privé.
   - **Private Subnet** : Héberge les containers de l’application (backend et frontend) dans ECS/Fargate. En gardant ces containers dans un sous-réseau privé, ils ne sont pas directement accessibles depuis l'Internet, ce qui améliore la sécurité de l'application.

3. **Elastic Load Balancer (ELB)**  
   Le rôle de l'ELB est de distribuer le trafic réseau de manière équilibrée entre les différents containers de frontend et backend. En assurant la répartition de charge, l'ELB permet d'améliorer la résilience et la performance de l'application en évitant la surcharge d'une seule instance. De plus, il peut offrir des fonctionnalités de redondance et de tolérance aux pannes.

4. **NAT Gateway**  
   Le NAT Gateway est nécessaire pour que les ressources en sous-réseau privé puissent accéder à Internet et aux services externes sans exposer directement ces ressources. Cela peut être utile pour que les containers puissent télécharger des mises à jour, accéder à des APIs externes ou d'autres services sans risquer une exposition publique.

5. **ECS (Elastic Container Service) avec Fargate**  
   ECS avec Fargate simplifie la gestion des containers sans nécessiter de serveur sous-jacent, ce qui permet de déployer facilement les images Docker pour le backend et frontend. Fargate s'occupe du dimensionnement, de la gestion de l'infrastructure et de la mise à jour automatique, permettant de se concentrer sur l'application elle-même plutôt que sur la gestion des serveurs.

6. **IAM Roles (Identité et Gestion des Accès)**  
   Les rôles IAM sont essentiels pour gérer les permissions d'accès à différentes ressources AWS. Par exemple, les containers exécutés sur ECS auront besoin de rôles IAM pour accéder à d'autres services AWS si nécessaire. Cela garantit que chaque composant de l'infrastructure dispose uniquement des permissions nécessaires, renforçant ainsi la sécurité.






### Justification des Choix Techniques pour les Investisseurs

1. **Sécurité**  
   En utilisant des sous-réseaux publics et privés, NAT Gateway et des rôles IAM, nous construisons une architecture sécurisée où seuls les composants nécessaires sont accessibles depuis l'Internet. Cela réduit les risques d’attaques pour l'application.

2. **Évolutivité**  
   L'utilisation d'Elastic Load Balancer et d'ECS/Fargate permet à l'infrastructure de s'adapter automatiquement aux fluctuations de trafic, garantissant des performances optimales même en cas de forte demande.

3. **Simplicité de Gestion**  
   ECS avec Fargate permet une gestion sans serveur de l'infrastructure, réduisant les besoins en maintenance et en expertise technique pour les opérations quotidiennes.

4. **Optimisation des coûts**  
   L'architecture repose sur des services gérés (comme Fargate), ce qui permet de réduire les coûts liés à l'infrastructure en ne payant que pour les ressources utilisées. Cela maximise le retour sur investissement pour l'entreprise.

5. **Haute Disponibilité**  
   Avec des composants comme l'Elastic Load Balancer, l'architecture est conçue pour être hautement disponible et résiliente aux pannes. Cela garantit une expérience utilisateur continue et fiable, ce qui est essentiel pour fidéliser les clients.

