# CATASTROPI - Plateforme de Gestion des Catastrophes assistée par IA 🌍🤖

**CATASTROPI** est une plateforme web intelligente conçue pour révolutionner la gestion des catastrophes naturelles et industrielles. Elle permet aux citoyens de signaler des incidents en temps réel, aux responsables de coordonner les secours, et aux agents sur le terrain de remonter leurs besoins. Le tout est supervisé par un module d'Intelligence Artificielle (IA) qui analyse, prédit et priorise les actions à mener.

---

## 🌟 Fonctionnalités Principales

### 1. Interface Multisites (Rôles)
L'application propose des tableaux de bord (dashboards) adaptés aux différents métiers :
- **Citoyen** : Formulaire de signalement d'incidents simplifié. Suivi de son "Trust Score" (indice de fiabilité des signalements).
- **Responsable (Hub Central)** : Vue globale, analyse automatique des signalements par l'IA (détection de fake news, priorisation des zones, estimation de l'impact), validation des rapports et assignation des agents.
- **Agent sur le terrain** : Réception des missions, reporting de l'état d'avancement, et outil de remontée de besoins (médicaux, logistiques, renforts).
- **Administrateur** : Gestion des utilisateurs, des accès, et visualisation des statistiques du système.

### 2. Module d'Intelligence Artificielle (`module_ia.py`)
Au cœur de l'application, l'IA (via Scikit-learn, Random Forest, TF-IDF) traite les données :
- **Détection de Fake News** : Vérification de la véracité des signalements citoyens basée sur l'historique de l'utilisateur, l'analyse NLP de la description, et le volume de signalement dans la même zone.
- **Évaluation du Risque & Impact** : Prédiction du niveau de risque et estimation détaillée des dégâts (victimes, blessés, destruction matérielle).
- **Priorisation & Allocation** : L'IA calcule le meilleur itinéraire et l'allocation optimale des ressources (ambulances, pompiers, kits) pour minimiser les pertes.
- **Apprentissage Continu** : Chaque interaction humaine (Responsable acceptant/rejetant une alerte) réentraîne le modèle.

### 3. Design Premium "Glassmorphism" & Cinématique
L'interface visuelle `index.html` a été sublimée avec :
- Un fond animé WebGL simulé (style enfumé/cyberpunk).
- Un rendu "Glassmorphism" : cartes semi-transparentes floutées (backdrop-filter) parfaitement lisibles en mode sombre.
- Une expérience sans rechargement de page en Single Page Application (Vanilla JS).

---

## 🛠️ Stack Technique

**Backend :**
- Python 3
- Flask (Serveur Web)
- Flask-SQLAlchemy avec base de données **SQLite** intégrée (`database.db`).
- Flask-JWT-Extended (Authentification)
- Flask-SocketIO (WebSockets pour le temps réel)

**Intelligence Artificielle :**
- scikit-learn (Machine Learning & NLP)
- Pandas / NumPy
- Jeu de données historique (`historique_catastrophes.xlsx`).

**Frontend :**
- HTML5 / CSS3 / Vanilla JavaScript (sans framework de type React ou Vue pour des performances maximales du portail unique).
- Leaflet.js (Cartographie interactive).
- Chart.js (Dashboard statistiques administrateur).

---

## 🚀 Installation & Lancement

### Prérequis
Assurez-vous d'avoir [Python 3.9+](https://www.python.org/downloads/) d'installé.

Cloner le projet puis installer les dépendances (l'utilisation d'un environnement virtuel est recommandée) :

```bash
pip install Flask Flask-SQLAlchemy Flask-SocketIO Flask-CORS Flask-JWT-Extended pandas scikit-learn werkzeug reportlab
```

### Lancement du serveur
```bash
python app.py
```
Le serveur démarrera sur `http://localhost:5000`.

*Lors du tout premier lancement, la base de données SQL (`database.db`) sera automatiquement générée à partir des modèles SQLAlchemy si elle n'existe pas, et le module IA se calibrera avec Excel.*

---

## 🔒 Accès par défaut
Une fois authentifié sur la page de connexion cinématique, utilisez l'adresse email de test associée au rôle souhaité (généralement initialisés via des scripts d'imports ou le compte Administrateur par défaut). 

*(Note : Pour le mode test, le portail contient parfois des liens cliquables sur la page de login "Utiliser un compte de test" qui pré-remplissent le formulaire pour vous).*
