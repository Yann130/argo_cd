# 🚀 K3s GitOps - Demo ArgoCD

Ce dépôt contient les manifestes Kubernetes pour gérer mes déploiements sur un cluster **K3s** via **ArgoCD**.

## 🎯 Contexte : À la découverte du CD (GitOps)

Ce projet est né d'une volonté de dépasser le déploiement manuel pour maîtriser le **Continuous Deployment (CD)**.

L'objectif est d'implémenter une chaîne de déploiement moderne où **Git est la seule source de vérité**. Grâce à ArgoCD, je n'ai plus besoin de lancer des commandes manuelles sur le serveur : dès que je "push" une modification sur ce dépôt (changement d'image, modification de config), le cluster se met à jour automatiquement.

---

## 📂 Structure du Projet

```text
app_customize/
├── base/                       # 🧱 Le socle commun (modèle)
│   ├── deployment.yaml         # Définition du Pod Nginx
│   ├── service.yaml            # Service générique (Type: NodePort)
│   └── kustomization.yaml      # Agrège les ressources de base
│
└── overlays/                   # 🎨 Les spécificités par environnement
    ├── staging/
    │   ├── namespace.yaml      # Crée le namespace "staging"
    │   ├── service-patch.yaml  # Fixe le NodePort à 30045
    │   └── kustomization.yaml  # Force l'image v1.24.0
    │
    └── production/
        ├── namespace.yaml      # Crée le namespace "production"
        ├── service-patch.yaml  # Fixe le NodePort à 30046
        ├── replicas-patch.yaml # Passe à 2 Réplicas (Haute dispo)
        └── kustomization.yaml  # Garde l'image stable v1.23.0
