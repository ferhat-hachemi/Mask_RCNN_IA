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

**Entrainement 1:**
- Activation: ****
- LEARNING_RATE : **0.001**
- OPTIMIZER: ****
- EPOCHS: **10**
- STEPS_PER_EPOCH: **15**
- The log file of the training with the last line showing the different losses:

Epoch 1/10
15/15 [==============================] - 344s 23s/step - loss: 18.6162 - rpn_class_loss: 7.6389 - rpn_bbox_loss: 9.6619 - mrcnn_class_loss: 0.4545 - mrcnn_bbox_loss: 0.6485 - mrcnn_mask_loss: 0.2124 - val_loss: 5.3477 - val_rpn_class_loss: 0.2056 - val_rpn_bbox_loss: 5.1420 - val_mrcnn_class_loss: 4.2077e-05 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 2/10
15/15 [==============================] - 320s 21s/step - loss: 14.1338 - rpn_class_loss: 4.0130 - rpn_bbox_loss: 8.5430 - mrcnn_class_loss: 0.0128 - mrcnn_bbox_loss: 1.3022 - mrcnn_mask_loss: 0.2628 - val_loss: 6.4300 - val_rpn_class_loss: 0.0824 - val_rpn_bbox_loss: 5.3243 - val_mrcnn_class_loss: 0.0208 - val_mrcnn_bbox_loss: 0.8118 - val_mrcnn_mask_loss: 0.1908

Epoch 3/10
15/15 [==============================] - 348s 23s/step - loss: 7.4600 - rpn_class_loss: 0.3646 - rpn_bbox_loss: 6.6169 - mrcnn_class_loss: 0.0026 - mrcnn_bbox_loss: 0.3635 - mrcnn_mask_loss: 0.1125 - val_loss: 6.3026 - val_rpn_class_loss: 0.0703 - val_rpn_bbox_loss: 6.2320 - val_mrcnn_class_loss: 3.7242e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 4/10
15/15 [==============================] - 336s 22s/step - loss: 9.2055 - rpn_class_loss: 0.3307 - rpn_bbox_loss: 8.8748 - mrcnn_class_loss: 5.4041e-07 - mrcnn_bbox_loss: 0.0000e+00 - mrcnn_mask_loss: 0.0000e+00 - val_loss: 7.8739 - val_rpn_class_loss: 0.1211 - val_rpn_bbox_loss: 5.5934 - val_mrcnn_class_loss: 0.0128 - val_mrcnn_bbox_loss: 1.9808 - val_mrcnn_mask_loss: 0.1658

Epoch 5/10
15/15 [==============================] - 324s 22s/step - loss: 6.7169 - rpn_class_loss: 0.1487 - rpn_bbox_loss: 6.5681 - mrcnn_class_loss: 3.7434e-05 - mrcnn_bbox_loss: 0.0000e+00 - mrcnn_mask_loss: 0.0000e+00 - val_loss: 3.1938 - val_rpn_class_loss: 0.1004 - val_rpn_bbox_loss: 3.0932 - val_mrcnn_class_loss: 1.0678e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 6/10
15/15 [==============================] - 328s 22s/step - loss: 8.3123 - rpn_class_loss: 0.3982 - rpn_bbox_loss: 7.4394 - mrcnn_class_loss: 2.4278e-04 - mrcnn_bbox_loss: 0.4237 - mrcnn_mask_loss: 0.0508 - val_loss: 5.5967 - val_rpn_class_loss: 0.0639 - val_rpn_bbox_loss: 5.5322 - val_mrcnn_class_loss: 6.0522e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 7/10
15/15 [==============================] - 338s 23s/step - loss: 8.6955 - rpn_class_loss: 0.2674 - rpn_bbox_loss: 8.0418 - mrcnn_class_loss: 3.2460e-04 - mrcnn_bbox_loss: 0.3337 - mrcnn_mask_loss: 0.0522 - val_loss: 5.3912 - val_rpn_class_loss: 0.0458 - val_rpn_bbox_loss: 5.3447 - val_mrcnn_class_loss: 6.8065e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 8/10
15/15 [==============================] - 320s 21s/step - loss: 9.6878 - rpn_class_loss: 0.1897 - rpn_bbox_loss: 9.4981 - mrcnn_class_loss: 3.8996e-05 - mrcnn_bbox_loss: 0.0000e+00 - mrcnn_mask_loss: 0.0000e+00 - val_loss: 7.7396 - val_rpn_class_loss: 0.1473 - val_rpn_bbox_loss: 7.5922 - val_mrcnn_class_loss: 1.8316e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 9/10
15/15 [==============================] - 315s 21s/step - loss: 6.9605 - rpn_class_loss: 0.1397 - rpn_bbox_loss: 6.8194 - mrcnn_class_loss: 0.0014 - mrcnn_bbox_loss: 0.0000e+00 - mrcnn_mask_loss: 0.0000e+00 - val_loss: 4.9935 - val_rpn_class_loss: 0.0653 - val_rpn_bbox_loss: 4.9271 - val_mrcnn_class_loss: 0.0011 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00

Epoch 10/10
15/15 [==============================] - 319s 21s/step - loss: 6.9689 - rpn_class_loss: 0.1457 - rpn_bbox_loss: 6.8231 - mrcnn_class_loss: 3.5683e-06 - mrcnn_bbox_loss: 0.0000e+00 - mrcnn_mask_loss: 0.0000e+00 - val_loss: 3.3112 - val_rpn_class_loss: 0.1322 - val_rpn_bbox_loss: 3.1784 - val_mrcnn_class_loss: 5.4498e-04 - val_mrcnn_bbox_loss: 0.0000e+00 - val_mrcnn_mask_loss: 0.0000e+00


![MODEL_10_EPOCHS_15_STEPS](https://github.com/user-attachments/assets/491b5b6b-5340-4e26-bc32-34e7519ce8c5)




























