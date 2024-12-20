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
Vous trouverz ici notre dataset utilisé pour l'entrainement: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/tree/master/dataset/lighter-dataset">**Dataset**</a>

**Constitution du Dataset :**
Le dataset utilisé pour ce projet a été conçu pour entraîner un modèle de détection d’objets sur des images de briquets ("lighters"). Un ensemble de 151 images a été collecté, couvrant divers angles et conditions d’éclairage. Roboflow a été utilisé pour annoter chaque image, en marquant les coordonnées précises des briquets, et pour générer les fichiers de labélisation compatibles avec le format Mask R-CNN. Cet outil a facilité un processus d'annotation précis et rapide, essentiel pour entraîner le modèle à détecter les briquets avec précision.

**Prétraitement des données :**
Pour s'assurer que le modèle puisse traiter les images de manière optimale, un prétraitement a été appliqué aux données. Toutes les images ont été redimensionnées à une résolution standard de 640x640 pixels, conformément aux exigences du modèle Mask R-CNN, qui s'attend à des entrées de dimensions fixes

**Division du Dataset :**
Le dataset a été divisé en deux sous-ensembles pour l'entraînement et la validation, selon une répartition d'environ 87 % pour l'entraînement et 13 % pour la validation. Cette proportion permet au modèle de s'entraîner sur une quantité suffisante de données tout en laissant un échantillon représentatif pour évaluer sa performance sur des images inédites.

 ## Environnement de Travail
Pour pouvoir lancer l'environnement, nous avons créé un environnement Python avec Conda en installant la version 3.3.6 de Python, afin de pouvoir installer les bibliothèques nécessaires pour utiliser MRCNN.

## Les Expériences d'Entraînement et Hyperparamètres

Dans notre cas, plusieurs entraînements du modèle ont été réalisés en ajustant différents paramètres pour observer leur impact sur les performances. Des hyperparamètres tels que le nombre d'époques (EPOCHS), le nombre d'étapes par époque (STEPS_PER_EPOCH) et les étapes de validation (VALIDATION_STEPS) ont été modifiés, permettant de suivre les variations dans les comportements du modèle et les changements des pertes (losses) au cours de l'entraînement.

**Training 1:**
- Activation: **ReLU**
- LEARNING_RATE : **0.001**
- OPTIMIZER: **SGD**
- EPOCHS: **10** & STEPS_PER_EPOCH: **15**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_10_epochs_15_steps.txt">Logs losses</a>
- SCREENSHOTS
  
  ![image](https://github.com/user-attachments/assets/ec2fc919-27f2-4ccf-bb1c-c00c08078cb8)
  ![image](https://github.com/user-attachments/assets/047cb5cc-ed87-4755-ac32-78eaaae1d277)
  ![image](https://github.com/user-attachments/assets/2e74bf91-8565-4892-9385-6f39dd52815a)
  ![image](https://github.com/user-attachments/assets/26146756-6941-41c6-abdf-54a4b484b240)
  ![image](https://github.com/user-attachments/assets/1a88606d-2558-4559-9f6d-c1f11903901b)
  ![image](https://github.com/user-attachments/assets/66f944ce-6cc1-4447-8f2e-361a169910e2)
  ![image](https://github.com/user-attachments/assets/9e316a00-89c8-4031-8d94-db0b7e5486a7)
  ![image](https://github.com/user-attachments/assets/d0dc327c-ddc9-48e1-8a3f-7e8f251141d4)
  ![image](https://github.com/user-attachments/assets/a7b1500a-c16e-4ab3-97d7-7cc76f7b3379)
  ![image](https://github.com/user-attachments/assets/a7ec9b3a-a3e1-49a5-8df9-a97614f25664)

- Graph representing the train and validation losses:
  
![GRAPH_10_EPOCHS_15_STEPS](https://github.com/user-attachments/assets/91693cc8-2071-4cb3-97c8-3948375fa800)

- Test Detection: 

![MODEL_10_EPOCHS_15_STEPS](https://github.com/user-attachments/assets/491b5b6b-5340-4e26-bc32-34e7519ce8c5)

- Commentaire :
  - La courbe d'entraînement montre une forte baisse initiale, puis se stabilise avec de légères variations, indiquant que le modèle apprend bien au début mais rencontre des difficultés à progresser par la suite. Cela suggère qu'il pourrait bénéficier d'améliorations pour mieux généraliser, comme l'ajout de régularisation ou l'augmentation des données pour éviter le surapprentissage.

**Training 2:**
Pour cet entrainement nous avons augmenté le nombre de STEPS_PER_EPOCH=200 ainsi que VALIDATION_STEPS=20 afin d'améliorer la qualité de l'apprentissage du modèle.

- Activation: **ReLU**
- LEARNING_RATE : **0.001**
- OPTIMIZER: **SGD**
- EPOCHS: **10** & STEPS_PER_EPOCH: **200**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_10_epochs_200_steps.txt">Logs losses</a>
- SCREENSHOTS

 ![image](https://github.com/user-attachments/assets/67aef4d1-b695-4e09-9c72-4c894e89f169)
 ![image](https://github.com/user-attachments/assets/80bb0aba-a701-4a62-81db-6aaf62d3836f)
 ![image](https://github.com/user-attachments/assets/5b7d8511-56d9-4268-b669-367fbf0b8185)
 ![image](https://github.com/user-attachments/assets/c1a5dd2d-9972-477e-923b-dd72259fe052)
 ![image](https://github.com/user-attachments/assets/8b1026e4-2d8b-48ed-b1c2-8b4b6fcc227c)
 ![image](https://github.com/user-attachments/assets/490ba82b-f9bc-4c4d-8800-2c0d0f363181)
 ![image](https://github.com/user-attachments/assets/526de830-489e-4b0a-8a4e-c774af253377)
 ![image](https://github.com/user-attachments/assets/8aec24a3-9116-4534-aab7-34427825e72e)
 ![image](https://github.com/user-attachments/assets/2a2ad9d3-fa5f-48a4-9e3a-b7fa964142a9)
 ![image](https://github.com/user-attachments/assets/d1b90b63-ef2b-4e7d-833f-1f5888425c6b)

- Graph representing the train and validation losses: 

![GRAPH_10_EPOCHS_200_STEPS](https://github.com/user-attachments/assets/f133ad0a-2ea5-458b-8f8a-669416f9a947)

- Test Detection:
  
![image](https://github.com/user-attachments/assets/3c7496a6-64f8-4c2e-8f71-7413ebf84206)

- Commentaire: 
  - On remarque que les courbes suivent le même schéma que lors de l'entraînement précédent, mais sont beaucoup plus proches, voire identiques vers les dernières époques, indiquant une réduction de l'overfitting par rapport au précédent entraînement.

**Training 3:**
Pour cet entrainement nous avons réduits le nombre de STEPS_PER_EPOCH=50 et augmenté VALIDATION_STEPS=30.

- Activation: **ReLU**
- LEARNING_RATE : **0.001**
- OPTIMIZER: **SGD**
- EPOCHS: **10** & STEPS_PER_EPOCH: **50**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_10_epochs_50_steps.txt">Logs losses</a>
- SCREENSHOTS

 ![image](https://github.com/user-attachments/assets/f8f3b66b-6f37-4cb3-ac3e-f58c02aebcc0)
 ![image](https://github.com/user-attachments/assets/474f1af7-ea94-4d6a-a6b1-8b0a0154db92)
 ![image](https://github.com/user-attachments/assets/1dec8dcb-f420-461a-b8ad-e3a286a05f6d)
 ![image](https://github.com/user-attachments/assets/7f25bf7f-79dd-4eb7-95de-d7a4698f6d82)
 ![image](https://github.com/user-attachments/assets/51841e97-eb67-4dfe-a3cf-3c4a60ae3028)
 ![image](https://github.com/user-attachments/assets/cc1267e9-2b9a-407b-82ed-0d1007cbcdec)
 ![image](https://github.com/user-attachments/assets/d8f1b613-6989-42c6-baa0-f862dab9e2b1)
 ![image](https://github.com/user-attachments/assets/d69334dd-2575-4d1e-851a-61ce06ba6e8b)
 ![image](https://github.com/user-attachments/assets/6c87956b-5c49-4a03-83c8-b26e16b88d45)
 ![image](https://github.com/user-attachments/assets/7e217f0d-0383-4cea-bccb-38b68fa9c43d)

- Graph representing the train and validation losses:

![GRAPH_10_EPOCHS_50_STEPS](https://github.com/user-attachments/assets/0c62c752-cdf4-4c40-bb45-3b2b5bbbf439)

- Test Detection:
  
![image](https://github.com/user-attachments/assets/b7fe5836-638c-4687-89f4-22a56585a5f8)

- Commentaire:
  - Le graphique montre que la perte d'entraînement est moins stable, avec certaines époques où la perte d'entraînement dépasse la perte de validation. Cela peut indiquer que le modèle rencontre des difficultés d’optimisation ou qu’il apprend de manière irrégulière. Ce comportement peut être dû à un taux d'apprentissage trop élevé.
  
**Training 4:**
Pour cet entrainement nous avons réduits le nombre d'EPOCHS=5, VALIDATION_STEPS=5 & STEPS_PER_EPOCH=30

- Activation: **ReLU**
- LEARNING_RATE : **0.0001**
- OPTIMIZER: **SGD**
- EPOCHS: **5** & STEPS_PER_EPOCH: **30**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_5_epochs_30_steps.txt">Logs losses</a>
- SCREENSHOTS

![image](https://github.com/user-attachments/assets/e6bc6e55-c1d8-4974-a2c6-6705a3f7c958)
![image](https://github.com/user-attachments/assets/306f8e94-cfbb-45d4-a0dd-1a9089522e7b)
![image](https://github.com/user-attachments/assets/411d0010-9923-460e-aeb7-076c6a9da6f6)
![image](https://github.com/user-attachments/assets/5c44314f-619a-400d-a028-afdc5d4064e9)
![image](https://github.com/user-attachments/assets/44207fad-75e9-42e5-bbd6-62977313c2b2)

- Graph representing the train and validation losses:

![GRAPH_5_EPOCHS_30_STEPS](https://github.com/user-attachments/assets/a086b4ff-8efe-4571-8536-c47254572534)

- Test Detection:
  
![image](https://github.com/user-attachments/assets/bdbd26e4-d016-4c68-945c-8a11b16b6774)

- Commentaire:
  - Avec la réduction du taux d’apprentissage et du nombre d’époques, le graphique montre une stabilisation autour d’une perte de 2.5, indiquant une convergence plus régulière. Cependant, comme les résultats de détection restent incorrects, cela pourrait signaler que le modèle ne capte pas les bonnes caractéristiques pour identifier les briquets.

**Training 5:**
À partir de cet entrainement nous avons augmenté la taille de dataset avec 277 images (68% training et 32% vlidation) pour essayer d'améliorer le model.

- Activation: **ReLU**
- LEARNING_RATE : **0.001**
- OPTIMIZER: **SGD**
- EPOCHS: **10** & STEPS_PER_EPOCH: **40**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_10_epochs_40_steps_detection.txt">Logs losses</a>
- SCREENSHOTS:

 ![image](https://github.com/user-attachments/assets/c7446f47-379a-4170-92fa-d5f67ad4624b)
 ![image](https://github.com/user-attachments/assets/89b38474-26ba-4fab-9489-9d7e13e31d74)
 ![image](https://github.com/user-attachments/assets/68778492-6c81-42fe-afeb-e1b902df1502)
 ![image](https://github.com/user-attachments/assets/7f6deb8a-28ba-4732-907e-e7d7f42aa46a)
 ![image](https://github.com/user-attachments/assets/66409ca1-0a0f-4869-ad5a-bd9740a8ec7d)
 ![image](https://github.com/user-attachments/assets/feb0d84a-72a4-40c6-aff5-d6efc3ca3848)
 ![image](https://github.com/user-attachments/assets/cf4176d1-8dec-4c8e-9e2d-d1a8d9b709e5)
 ![image](https://github.com/user-attachments/assets/a2eb4876-8108-4f86-b9a0-47dd92540c78)
 ![image](https://github.com/user-attachments/assets/0bb41a61-3066-4a55-8112-4f24f00633df)
 ![image](https://github.com/user-attachments/assets/493ac8af-1f6b-4e33-b423-128b3ef3f045)

-  <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_10_epochs_40_steps_detection_full_logs.txt">Full Logs losses</a>
- Graph representing the train and validation losses:
  
![Screenshot from 2024-11-14 21-20-44](https://github.com/user-attachments/assets/d612c97b-89e5-46cc-8ae1-77d000776e5e)

- Test Detection:

![image](https://github.com/user-attachments/assets/a3868dd2-6219-4df9-9bd9-d28dd97d6ada)

![image1](https://github.com/user-attachments/assets/15d45b6b-d53f-47e2-921b-87dd3af9b760)

- Commentaire:
Le graphique montre une bonne convergence des pertes d’entraînement et de validation, stabilisées autour de 0.5, indiquant que le modèle apprend de manière régulière sans surapprentissage. Cependant, la présence de cadres de détection supplémentaires suggère qu'il capte des caractéristiques non spécifiques aux briquets, entraînant des faux positif.

**Training 6:** (Fine tuning de résultat précedent avec 10 EPOCHS en plus)
- Activation: **ReLU**
- LEARNING_RATE : **0.0001**
- OPTIMIZER: **SGD**
- EPOCHS: **10** & STEPS_PER_EPOCH: **80**
- The log file of the training with the last line showing the different losses: <a href="https://github.com/ferhat-hachemi/Mask_RCNN_IA/blob/master/training_logs/log_20_epochs_80_steps_fine_tuning.txt">Logs losses</a>

- SCREENSHOTS:

 ![image](https://github.com/user-attachments/assets/6dc2d452-0971-4d95-9a25-3501f2466994)
 ![image](https://github.com/user-attachments/assets/0fa6fde7-155a-4705-ae49-b14e742c7e94)
 ![image](https://github.com/user-attachments/assets/1d4459cc-d86a-4bcb-afa3-4267ba987962)
 ![image](https://github.com/user-attachments/assets/55f81ba6-a28a-45af-9c7c-f3702c5a6267)
 ![image](https://github.com/user-attachments/assets/eb4b64b4-0c3f-42a3-8cbc-3a959dc8b99c)
 ![image](https://github.com/user-attachments/assets/b7bb54d8-41aa-454a-a8c9-0e57998a2420)
 ![image](https://github.com/user-attachments/assets/c50c651f-6a84-4301-9804-5c3a553636c5)
 ![image](https://github.com/user-attachments/assets/3dcc877e-8c59-43c2-be13-f3c45605adec)
 ![image](https://github.com/user-attachments/assets/82f1d41f-b46b-414a-8bb5-322eefa0ed11)
 ![image](https://github.com/user-attachments/assets/238063d1-8e4b-4fd9-b7b6-93f95e6bfa34)

- Graph representing the train and validation losses:

![Screenshot from 2024-11-15 10-18-24](https://github.com/user-attachments/assets/2e1afec9-c199-42da-b024-50554b4c5e6f)

  
- Test detection :
 
![fine_tuning1](https://github.com/user-attachments/assets/bf0d0aa1-f80b-4e9c-acbd-fde8e3804bbf)

![fine_tuning2](https://github.com/user-attachments/assets/a28ee694-89e1-4fa3-b3d4-7904538637cf)

- Commentaire:
Grâce au fine-tuning, le nombre de faux positifs a diminué, mais le modèle continue à générer des cadres de détection inutiles.

## Conclusion

En conclusion, le modèle Mask R-CNN parvient bien à détecter les briquets, mais génère encore des cadres inutiles. Cela indique qu'il reste des problèmes de généralisation. Un fine-tuning supplémentaire, ou un ajustement des hyperparamètres pourraient aider à réduire ces faux positifs et affiner la précision globale.
