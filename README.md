# Mask_RCNN_IA


## Introduction

**Objectif du projet :**
L'objectif principal de ce projet est de réaliser la détection d'objets, en l'occurrence un "lighter" (briquet), à l'aide d'un modèle de détection d'objets basé sur Mask R-CNN. Le modèle Mask R-CNN, qui repose sur un backbone ResNet101, est largement utilisé pour des tâches de segmentation et de détection d'objets, grâce à sa capacité à identifier des régions d'intérêt dans une image tout en produisant des masques de segmentation pour chaque instance détectée. Cependant, pour maximiser l'efficacité et la précision du modèle, il est essentiel d'expérimenter et de régler divers hyperparamètres

**Structure du rapport :**
Ce rapport est structuré pour documenter de manière détaillée les différentes tentatives d'entraînement effectuées dans le cadre de ce projet. Chaque entraînement est présenté avec sa configuration d'hyperparamètres, ses résultats et les observations qui en découlent. Le rapport met en avant :

- Les configurations d'hyperparamètres utilisées pour chaque expérience.
- Les résultats obtenus sous forme de métriques d'évaluation, telles que les pertes d'entraînement et de validation.
- Les graphiques et matrices de confusion illustrant les performances du modèle.
- Une analyse de l'impact des principaux hyperparamètres sur les résultats.
- L'objectif de cette structure est de montrer la progression de l'optimisation du modèle et de fournir une analyse approfondie des ajustements effectués.

## Description du Dataset

**Constitution du Dataset :**
Le dataset utilisé pour ce projet a été conçu pour entraîner un modèle de détection d’objets sur des images de briquets ("lighters"). Un ensemble de 150 images a été collecté, couvrant divers angles et conditions d’éclairage. Roboflow a été utilisé pour annoter chaque image, en marquant les coordonnées précises des briquets, et pour générer les fichiers de labélisation compatibles avec le format Mask R-CNN. Cet outil a facilité un processus d'annotation précis et rapide, essentiel pour entraîner le modèle à détecter les briquets avec précision.

**Prétraitement des données :**
Pour s'assurer que le modèle puisse traiter les images de manière optimale, un prétraitement a été appliqué aux données. Toutes les images ont été redimensionnées à une résolution standard de 640x640 pixels, conformément aux exigences du modèle Mask R-CNN, qui s'attend à des entrées de dimensions fixes

**Division du Dataset :**
Le dataset a été divisé en deux sous-ensembles pour l'entraînement et la validation, selon une répartition standard de 85 % pour l'entraînement et 15 % pour la validation. Cette proportion permet au modèle de s'entraîner sur une quantité suffisante de données tout en laissant un échantillon représentatif pour évaluer sa performance sur des images inédites.

 ## Environnement de Travail
Pour pouvoir lancer l'environnement, nous avons créé un environnement Python avec Conda en installant la version 3.3.6 de Python, afin de pouvoir installer les bibliothèques nécessaires pour utiliser MRCNN.

## Les Expériences d'Entraînement et Hyperparamètres

Dans notre cas, plusieurs entraînements du modèle ont été réalisés en ajustant différents paramètres pour observer leur impact sur les performances. Des hyperparamètres tels que le nombre d'époques (EPOCHS), le nombre d'étapes par époque (STEPS_PER_EPOCH) et les étapes de validation (VALIDATION_STEPS) ont été modifiés, permettant de suivre les variations dans les comportements du modèle et les changements des pertes (losses) au cours de l'entraînement.

# *Entrainement 1*:
- Activation: ****
- LEARNING_RATE : **0.001**
- OPTIMIZER: ****
- EPOCHS: **10**
- STEPS_PER_EPOCH: **15**





























