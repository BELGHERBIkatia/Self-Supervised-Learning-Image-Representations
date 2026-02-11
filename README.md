# Apprentissage de représentations d'images : Approches auto-supervisées

[cite_start]Ce projet explore différentes méthodes de **Self-Supervised Learning (SSL)** pour l'apprentissage de représentations visuelles sans étiquettes explicites[cite: 3, 4, 21]. [cite_start]L'objectif est d'évaluer l'efficacité de diverses tâches prétextes en mesurant leur capacité de généralisation sur des tâches de classification supervisée[cite: 22].

##  Présentation des Démonstrations

Le projet implémente cinq démonstrations principales pour comprendre les mécanismes du SSL :

* [cite_start]**Demo 1 : Context Encoder (Inpainting)** – Le modèle apprend à reconstruire les zones manquantes d'une image pour capturer des caractéristiques globales[cite: 11, 12, 81].
* [cite_start]**Demo 2 : Rotation Prediction** – Prédit l'angle de rotation (0°, 90°, 180°, 270°) appliqué à l'image pour comprendre la forme et l'orientation[cite: 12, 13, 81].
* [cite_start]**Demo 3 : SimCLR (Contrastive Learning)** – Utilise l'apprentissage contrastif pour maximiser la similarité entre vues augmentées d'une même image[cite: 14, 15, 81].
* [cite_start]**Demo 4 : Downstream Tasks** – Réutilisation des représentations de SimCLR pour la segmentation sémantique[cite: 16, 17].
* [cite_start]**Demo 5 : Avoiding Trivial Representations** – Analyse de l'impact des informations bas-niveau (biais) sur l'apprentissage[cite: 18, 19].

---

##  Résultats et Comparaisons

Les modèles ont été évalués sur les jeux de données **CIFAR-10** et **CIFAR-100**.

### Performances sur CIFAR-10 (Accuracy)
[cite_start]L'apprentissage contrastif (SimCLR) surpasse nettement les méthodes basées sur la reconstruction ou les transformations géométriques simples[cite: 25, 30].



| Modèle | Tâche prétexte | Top-1 Accuracy | Top-5 Accuracy |
| :--- | :--- | :--- | :--- |
| **SimCLR** | Similitude entre vues | **92.84%** | 99.86% |
| **Rotation Prediction** | Angle de rotation | **79.91%** | 99.12% |
| **Context Encoder** | Reconstruction spatiale | **45.77%** | 90.29% |
| **Relative Patch Position** | Position spatiale locale | **38.0%** | - |

> [cite_start]**Note :** Les résultats sur CIFAR-100 confirment cette tendance avec SimCLR atteignant ~72.3% d'accuracy contre ~38.5% pour le Context Encoder[cite: 68].

---

##  Focus : Relative Patch Position Prediction

[cite_start]Cette tâche prétexte consiste à prédire la position relative d'un patch par rapport à un patch central[cite: 70, 72]. 

* [cite_start]**Architecture :** Utilise un réseau **Relative PositionNet** avec un encodeur convolutionnel partagé[cite: 73, 74].
* [cite_start]**Objectif :** Apprendre une représentation spatiale non triviale des images[cite: 77].
* [cite_start]**Performance :** Bien que l'accuracy soit plus faible (~38%), le modèle démontre une compréhension réelle de la structure spatiale locale[cite: 76, 81].

