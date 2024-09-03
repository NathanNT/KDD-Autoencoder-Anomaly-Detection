### Classification de Trafic Réseau par Autoencodeur (Dataset KDD)

Ce projet utilise un autoencodeur pour détecter les anomalies dans le trafic réseau à partir du dataset KDD, couramment utilisé pour la détection d'intrusions.

### Méthodologie

- **Prétraitement des données :**
  - Chargement des données du dataset KDD.
  - Encodage des colonnes catégorielles.
  - Normalisation des données.
  - Binarisation des étiquettes : `0` pour le trafic normal, `1` pour les autres classes.

- **Modèle Autoencodeur :**
  - **Architecture :**
    - Couches d'encodage et de décodage symétriques.
    - Fonction d'activation Leaky ReLU et Dropout pour régularisation.
    - Couche bottleneck pour capturer la représentation compacte.
  - **Entraînement :**
    - Entraîné uniquement sur le trafic normal pour apprendre sa distribution.
    - Utilisation de la perte `categorical_crossentropy` et de l'optimiseur `rmsprop`.
  - **Détection d'anomalies :**
    - Calcul de l'erreur quadratique moyenne (MSE) entre les données originales et reconstruites.
    - Seuil défini pour détecter les anomalies en fonction du percentile du MSE.

### Résultats

- **Entraînement :**
  - Visualisation de la perte d'entraînement et de validation au cours des époques.
  
- **Évaluation :**
  - Détection des anomalies sur les données de test.
  - Calcul des métriques : matrice de confusion, précision, rappel, et exactitude.

### Chargement des données

Placer dans le répertoire `./datasets/KDD/`.
