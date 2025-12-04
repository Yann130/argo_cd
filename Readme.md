# 🚀 K3s GitOps - Demo ArgoCD

Ce dépôt contient les manifestes Kubernetes pour gérer mes déploiements sur un cluster **K3s** via **ArgoCD**.

## 🎯 Contexte : À la découverte du CD (GitOps)

Ce projet est né d'une volonté de dépasser le déploiement manuel pour maîtriser le **Continuous Deployment (CD)**.

L'objectif est d'implémenter une chaîne de déploiement moderne où **Git est la seule source de vérité**. Grâce à ArgoCD, je n'ai plus besoin de lancer des commandes manuelles sur le serveur : dès que je "push" une modification sur ce dépôt (changement d'image, modification de config), le cluster se met à jour automatiquement.

---

## 📂 Structure du Projet

```text
.
├── argocd/                # Manifestes ArgoCD (Applications)
│   ├── nginx/             # Le serveur web (Test de connectivité)
│   └── wordpress/         # La stack complète (WordPress + MySQL)
