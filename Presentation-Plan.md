Deep learning embarqué:
	0-Bonjour, qui je suis (1min)
	1- Deep learning: petite intro (Ce que c'est, les phases entreprisent pour l'utiliser, le GPU) (3min)
	    1.x GPU: Optimiser le calcul tensoriel qui est à la base de l'apprentisssage des réseaux de neurones.
	    1.x: Il existe plusieurs framework pour l'entraînement (Keras, Tensorflow, PyTorch, ... ).
	    1.x: Un réseau de neurones a une architecture: Une cascade de couches de convolution (paramètre d'une matrice de convolution)
	    1.x: Diviser les données en train test .
	    1.x: Precision et recall: https://fr.wikipedia.org/wiki/Pr%C3%A9cision_et_rappel
	2- Différence avec le deep learning embarqué (la machine de train <> machine de test (car machine d'inférence différente)) (1min)
		2.1-Entraînement du modèle (3min)
		        2.1.1 L'entraînement d'un modèle de deep learning et consommateur en ressources, le calcul d'une prédiction non.
		            --> Intéressant de faire de la prédiction en embarqué.
		            --> Et pourquoi ne pas faire l'entraînement sur le cloud
                2.1.2 L'entraînement d'un modèle supervisé suit ces étapes:
                    ** Initialiser aléatoirement les paramètre du modèle.
                    ** Séparer les données labelisée en 2 ensembles train et test
                    ** Lancer une prédiction sur les données du train (généralement divisé en batch).
                    ** On mesure l'erreur entre ces prédictions avec les vrais résultats. On s'aide d'une focntion de coût (Ex: Binary crossentropy, ...)
                    ** Ajuster les paramètres du modèle à l'aide d'une descente de gradient pour diminuer au maximum l'erreur.
                    ** Lancer une prédiciton sur les données test on mesure l'erreur avec les vrai labels (pas frocément à l'aide de la même fonctionde coût)
                    ** Si l'erreur est acceptable le modèle est entraîné sinon on retourne à l'étape 3 (à chaque retour à l'étape 3 une "epoch" s'est déroulé).
                2.1.3 Sauvegarde du modèle :
                    **Pour faire passer le modèle entre plusieurs machine (ex:de la machine d'entrainement vers celle de la prediction)
                      Sauvegarde au format binaire: h5, protobuf 
                2.1.4 Une slide de résumé
		2.2-Déploiement du modèle (7min) la machine de train <> machine de test, nerf de la guerre
		        2.2.1 Différence d'architecture:  arm, raspberry
		        2.2.2 Les packages utilisés pour le ML (Tensorflow, ...) ne peuvent marcher de la même façon avec un jeu d'insruction ARM.
		               Il faudra utiliser des versions semblables à celle de la machine d'entrainement et de plus executables avec une archi ARM.
		               Attention au type de bibliothèques à installer et dans la mesure où la version ARM est disponible
		        2.2.3 Automatiser le déploiement: (pour gérer dans le temps l'industrialisation des déploiements)
		                *Ansible par exemple : Outil d'automatisation d'execution de tâches sur une machine distante via SSH.
		                                      On utilisera des playbooks (fichiers au format.yaml) pour décrire ces instructions.
		                                      Les playbooks contiendront l'installation de toute les librairies python avec une archi ARM utilisées lors de l'entraînement		             		          
		                *TensorRT: solution développé par nvidia qui s'utilise avant le déploiement du modèle:
		                        **Fait des optimisations de l'architecture du réseau de neurones
		                        **Déploie sur le device souhaité un moteur d'inférence light-weight qui contient le modèle optimisé ainsi que toutes ses dépendances
                2.2.4 Une slide de résumé 
	3-Live démo:
		3.1-La jetson nano (4min)
		            **Archi
        		    **OS
        		    **Prix
        		    **A des GPU on peut même faire du transfert learning dessus avec PyTorch
        		    **Réception et préparation de la carte (2min)
		3.3-Utilisation du modèle de reconnaissance d'images en temps réél (3min)
	4-Conclusion (3min)