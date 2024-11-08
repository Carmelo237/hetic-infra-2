

1. Composants AWS nécessaires

a. Elastic Container Service (ECS) avec Fargate
Description : ECS avec Fargate permet d'exécuter des conteneurs Docker de manière serverless sans avoir besoin de gérer les serveurs sous-jacents.
Rôle : Il sera utilisé pour déployer et orchestrer les conteneurs Docker de l'application backend et frontend.

b. Elastic Load Balancer (ELB)
Description : ELB distribue le trafic de manière équilibrée entre plusieurs instances de l'application, ce qui permet de garantir la haute disponibilité.
Rôle : Distribuer le trafic vers les conteneurs ECS (backend et frontend) déployés dans plusieurs zones de disponibilité pour résilience en cas de défaillance.

c. Amazon RDS (optionnel, pour base de données)
Description : Si votre application nécessite une base de données, RDS fournit un service de base de données managée et durable.
Rôle : Héberger la base de données de manière sécurisée et avec haute disponibilité.

d. Amazon S3 (Simple Storage Service)
Description : S3 est utilisé pour stocker de manière sécurisée les ressources statiques, comme les fichiers ou images utilisés par l'application frontend.
Rôle : Stockage durable et scalable pour les fichiers statiques.

e. Amazon CloudFront (optionnel)
Description : Service de distribution de contenu qui utilise le réseau global d'AWS pour améliorer les temps de chargement des applications.
Rôle : Accélérer la distribution du contenu statique en cache pour améliorer la performance utilisateur.

f. Amazon ECR (Elastic Container Registry)
Description : ECR permet de stocker et de gérer les images Docker de manière sécurisée.
Rôle : Héberger les images Docker backend et frontend, prêtes à être déployées sur ECS.

g. Route 53
Description : Service de DNS géré par AWS, utilisé pour gérer les noms de domaine.
Rôle : Faciliter la gestion du nom de domaine pour rendre l'application accessible sur internet.


2. Schéma de l'infrastructure

![image](C:\Users\brice\OneDrive\Bureau\HETIC\python_projects\2ème projet\Architecture et infrastructure\Infrastructure.png)


3. Justification des choix techniques

Elastic Container Service (ECS) avec Fargate : Choisi pour sa simplicité de gestion serverless, ECS Fargate prend en charge l'infrastructure sous-jacente, permettant de se concentrer sur le déploiement de l'application sans avoir à gérer les serveurs.

Elastic Load Balancer (ELB) : Un Load Balancer est essentiel pour répartir le trafic de manière uniforme entre les conteneurs dans les différentes zones de disponibilité, assurant ainsi la haute disponibilité en cas de panne dans une zone.

Amazon RDS : Solution idéale pour gérer une base de données relationnelle avec haute disponibilité et backups automatisés, sans avoir à administrer la base de données.

Amazon S3 et CloudFront : S3 permet de stocker les ressources statiques de manière scalable et durable, tandis que CloudFront améliore les performances en mettant en cache les ressources proches des utilisateurs.

Amazon ECR : ECR est un registre Docker sécurisé, directement intégré avec ECS, facilitant la gestion et le déploiement des images Docker sans soucis de compatibilité.

Route 53 : Permet de gérer facilement le DNS pour l'application et de fournir une interface stable pour accéder à l'application sur internet.





4. Bonus : Service utilisé pour le stockage des images Docker

Pour uploader les images Docker et les rendre disponibles dans AWS, nous utilisons Amazon Elastic Container Registry (ECR). ECR est un registre de conteneurs sécurisé, entièrement intégré avec ECS, ce qui simplifie le déploiement direct depuis les images Docker vers ECS.