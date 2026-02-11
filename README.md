# Apprentissage de représentations d'images : Approches auto-supervisées

Ce projet porte sur l'**Apprentissage Auto-Supervisé (Self-Supervised Learning - SSL)** appliqué à la vision par ordinateur. L'objectif est d'apprendre des représentations visuelles riches à partir de données non étiquetées en utilisant des tâches prétextes, puis d'évaluer leur efficacité sur des tâches de classification.

## 🚀 Contenu du Projet

Le projet explore cinq démonstrations clés pour comprendre les mécanismes du SSL :

* **Demo 1 : Context Encoder (Inpainting)** – Le modèle apprend à reconstruire les zones manquantes au centre d'une image pour capturer des caractéristiques globales.
* **Demo 2 : Rotation Prediction** – Le modèle doit prédire l'angle de rotation (0°, 90°, 180°, 270°) appliqué à l'image pour comprendre la forme et l'orientation.
* **Demo 3 : SimCLR (Contrastive Learning)** – Utilisation d'un apprentissage contrastif pour maximiser la similarité entre différentes vues augmentées d'une même image.
* **Demo 4 : Downstream Tasks** – Réutilisation des représentations de SimCLR pour des tâches comme la segmentation sémantique.
* **Demo 5 : Avoiding Trivial Representations** – Analyse de l'impact des informations bas-niveau qui peuvent fausser l'apprentissage.

---

## 📊 Résultats et Performances

Les performances ont été mesurées sur les jeux de données **CIFAR-10** et **CIFAR-100**.

### Comparaison sur CIFAR-10 (Accuracy Top-1)

| Modèle | Tâche prétexte | Accuracy (Test) | Observations |
| :--- | :--- | :--- | :--- |
| **SimCLR** | Apprentissage contrastif | **92.8%** | Méthode la plus robuste ; capture les invariances les plus riches. |
| **Rotation Prediction** | Prédiction d'angle | **79.9%** | Très efficace pour comprendre la structure et l'orientation. |
| **Context Encoder** | Reconstruction (Inpainting) | **45.7%** | Apprend des représentations globales basées sur le contenu. |
| **Relative Position** | Position spatiale relative | **38.0%** | Encourage la modélisation de la structure spatiale locale. |

### Évaluation sur CIFAR-100
Les résultats confirment la supériorité des approches contrastives, même sur des jeux de données plus complexes :
* **SimCLR** : ~72.3%
* **Rotation Prediction** : ~55.8%
* **Context Encoder** : ~38.5%

---

## 🔬 Focus : Relative Patch Position Prediction

Dans cette expérience, nous avons implémenté le modèle **Relative PositionNet** pour prédire la position relative d'un patch d'image par rapport à un patch central.

* **Architecture** : Utilise un encodeur convolutionnel partagé et une couche finale entièrement connectée pour classer la position parmi 8 choix possibles.
* **Conclusion** : Bien que la performance brute soit plus faible (~38%), le modèle apprend une représentation spatiale non triviale, ce qui est l'objectif principal du SSL plutôt que la performance pure.

