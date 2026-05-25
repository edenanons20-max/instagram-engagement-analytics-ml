# 📊 Instagram Engagement Analytics — ML Project

> **Analyse end-to-end** de l'engagement Instagram avec exploration des données, modélisation machine learning et analyse temporelle — 119 posts, 13 variables, 2 modèles ML.

---

## 🎯 Objectifs du projet

Ce projet vise à :
- **Comprendre** les facteurs qui influencent le taux d'engagement sur Instagram
- **Prédire** le niveau d'engagement d'un post (régression et classification)
- **Identifier** des recommandations concrètes pour optimiser la stratégie de contenu

---

## 📁 Structure du projet

```
instagram-engagement-analytics-ml/
│
├── data/
│   └── Instagram data.csv          # Dataset brut (119 posts, 13 features)
│
├── notebooks/
│   ├── Phase_2_Exploration.ipynb          # EDA, feature engineering, corrélations
│   ├── Phase_3_4_Modelisation.ipynb       # Régression linéaire & logistique
│   └── Phases_5_Analyse_temporelle.ipynb  # Séries temporelles, ARIMA
│
├── visuals/                         # Graphiques exportés
│   ├── Matrice de corrélation ...png
│   ├── Engagement en fonction du nombre de hashtags.png
│   ├── Engagement en fonction de la longeur de la légende.png
│   ├── Sources moyennes des impressions.png
│   ├── Engagement moyen par jour de la semaine.png
│   └── Tendance du taux d'engagement.png
│
├── reports/
│   └── instagram_analysis_report_public.pdf   # Rapport d'analyse complet
│
├── requirements.txt                 # Dépendances Python
└── README.md
```

---

## 📊 Le dataset

| Variable | Description |
|---|---|
| `Impressions` | Nombre total de vues du post |
| `From Home` | Impressions depuis le fil d'accueil |
| `From Hashtags` | Impressions via les hashtags |
| `From Explore` | Impressions via la page Explorer |
| `From Other` | Autres sources |
| `Saves` | Nombre d'enregistrements |
| `Comments` | Nombre de commentaires |
| `Shares` | Nombre de partages |
| `Likes` | Nombre de j'aime |
| `Profile Visits` | Visites de profil générées |
| `Follows` | Abonnements générés |
| `Caption` | Texte de la légende |
| `Hashtags` | Liste des hashtags utilisés |

**Features engineered :**
- `engagement` = (Likes + Comments + Shares + Saves) / Impressions × 100
- `caption_length` = longueur de la légende (en caractères)
- `hashtags_count` = nombre de hashtags utilisés

---

## 🔬 Phases du projet

### Phase 2 — Exploration & préparation
- Statistiques descriptives et détection des valeurs manquantes
- Création des features dérivées (`engagement`, `caption_length`, `hashtags_count`)
- Matrice de corrélation et analyse des sources d'impressions
- Visualisations : scatter plots, heatmaps, bar charts

### Phase 3 — Régression linéaire
- **Objectif** : prédire le taux d'engagement (variable continue)
- **Features** : `hashtags_count`, `caption_length`, `Impressions`
- **Résultat** : R² = 0.12 — modèle de baseline, relations complexes non linéaires

### Phase 4 — Classification
- **Objectif** : prédire si un post aura un fort engagement (> médiane)
- **Modèles** : Régression logistique + Arbre de décision
- **Résultat** : Accuracy = 66.7% (régression logistique, test set)

### Phase 5 — Analyse temporelle
- Simulation de dates et analyse de tendance
- Engagement moyen par jour de la semaine
- Modèle ARIMA (1,1,1) pour la prévision

---

## 📈 Principaux résultats

| Insight | Détail |
|---|---|
| 🏷️ **Hashtags optimaux** | 6–10 hashtags → engagement moyen de 8.03% |
| ✍️ **Longueur légende** | 151–200 caractères → engagement de 7.23% |
| 🏠 **Source principale** | 43% des impressions viennent du fil Home |
| 💾 **Métriques clés** | Saves (corr. 0.32) et Shares (0.31) > Likes (0.15) |
| 📊 **Engagement moyen** | 6.38% sur l'ensemble du dataset |

---

## 🚀 Installation & usage

```bash
# 1. Cloner le dépôt
git clone https://github.com/<votre-username>/instagram-engagement-analytics-ml.git
cd instagram-engagement-analytics-ml

# 2. Créer un environnement virtuel
python -m venv venv
source venv/bin/activate        # Linux/macOS
venv\Scripts\activate           # Windows

# 3. Installer les dépendances
pip install -r requirements.txt

# 4. Lancer Jupyter
jupyter notebook
```

> **Note** : les notebooks utilisent un chemin relatif vers les données. Assurez-vous de les exécuter depuis la racine du projet, ou adaptez le chemin :
> ```python
> df = pd.read_csv("../data/Instagram data.csv", encoding="latin1")
> ```

---

## 🛠️ Stack technique

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-2.x-150458?logo=pandas)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter)

| Librairie | Usage |
|---|---|
| `pandas` | Manipulation et nettoyage des données |
| `numpy` | Calculs numériques |
| `matplotlib` / `seaborn` | Visualisations statiques |
| `scikit-learn` | Modèles ML (LinearRegression, LogisticRegression, DecisionTree) |
| `statsmodels` | Modèle ARIMA (analyse temporelle) |

---

## 🔮 Améliorations futures

- [ ] **Feature engineering avancé** : heure de publication, type de contenu (image/vidéo/reel), analyse de sentiment de la légende
- [ ] **Modèles plus puissants** : Random Forest, XGBoost, LightGBM
- [ ] **NLP sur les hashtags** : clustering thématique, popularité des hashtags
- [ ] **Cross-validation** : évaluation plus robuste (K-Fold)
- [ ] **Pipeline sklearn** : encapsulation preprocessing + modèle
- [ ] **Dashboard interactif** : Streamlit ou Dash pour explorer les résultats

---

## 📄 Rapport

Le rapport complet est disponible dans [`reports/instagram_analysis_report_public.pdf`](reports/instagram_analysis_report_public.pdf).

---

## 👤 Auteur

Projet réalisé dans le cadre d'une formation en Data Science / Machine Learning.

---

*Dataset source : kaggle
