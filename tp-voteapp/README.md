## 🎯 **Objectif du TP : Déployer l’application “vote” avec Kubernetes**

### 🧩 **Contexte**
L'application "vote" est une architecture composée de plusieurs microservices communiquant entre eux. Elle permet aux utilisateurs de voter pour une option (par exemple : "Cats" ou "Dogs") et d'afficher les résultats en temps réel. Cette application est souvent utilisée comme exemple pour illustrer un déploiement multi-conteneurs.

---

### 🔧 **Composants de l'application**

| Composant  | Rôle                                                                 |
|------------|----------------------------------------------------------------------|
| `vote`     | Frontend web (écrit en Python/Flask), pour voter                     |
| `result`   | Frontend web (écrit en Node.js), pour voir les résultats             |
| `worker`   | Service backend (écrit en .NET), lit les votes depuis Redis et les stocke dans Postgres |
| `redis`    | File d’attente (in-memory queue) pour stocker les votes temporairement |
| `postgres` | Base de données relationnelle pour stocker les résultats des votes   |

---

### 📦 **Travail demandé**

1. **Créer un cluster Kubernetes (local ou distant)**  
   - Option : Minikube, Kind, K3s, MicroK8s ou un cluster cloud (GKE, AKS, EKS)

2. **Définir les manifests YAML nécessaires**
   - 1 Deployment par service : `vote`, `result`, `worker`, `redis`, `postgres`
   - 1 Service par composant, dont certains en `ClusterIP`, d'autres en `NodePort` ou `LoadBalancer`

3. **Configurer les services**
   - `vote` et `result` doivent être accessibles depuis le navigateur
   - `worker` n’est pas exposé, il communique en interne avec Redis et Postgres
   - `redis` et `postgres` sont uniquement accessibles depuis les autres pods

4. **Déployer tous les composants dans un namespace dédié**  
   Exemple : `vote-app`


5. **Tester l’application**
   - Accéder à l’interface de vote
   - Voter plusieurs fois
   - Vérifier que les résultats s’affichent en temps réel

