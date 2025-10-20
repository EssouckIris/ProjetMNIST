 TP1 – De la conception au déploiement de modèles de Deep Learning

Date : 19 octobre 2025

- Fondations du Deep Learning

Dans cette partie, un réseau de neurones fully-connected est construit pour classifier les chiffres manuscrits du dataset MNIST.

Étapes principales :

- Chargement et normalisation des données.
- Construction du modèle avec des couches Dense et Dropout.
- Compilation avec l’optimiseur Adam.
- Entraînement et évaluation du modèle.
- Sauvegarde du modèle sous mnist_model.h5.


Commande d’exécution :

python train_model.py



Ingénierie du Deep Learning

versionnement avec Git et GitHub

 Initialiser un dépôt :

git init
git add .
git commit -m "Initial commit"


 Connecter au dépôt distant :

git remote add origin <URL_DU_DEPOT>
git push -u origin master



 Suivi des expérimentations avec MLflow

MLflow permet de suivre les paramètres, métriques et modèles lors des entraînements.

Installation :

pip install mlflow

Lancement du tracking :

mlflow ui

(Accessible sur http://127.0.0.1:5000)

 Déploiement du modèle avec Flask

Le fichier app.py expose une API REST permettant de prédire la classe d’une image au format JSON.

Conteneurisation avec Docker

Fichier Dockerfile

FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 5000
CMD ["python", "app.py"]

Construction et exécution du conteneur :

docker build -t mnist-api .
docker run -p 5000:5000 mnist-api


Utilisation des ressources (CPU, RAM, GPU)


Technologies utilisées

TensorFlow / Keras	Construction et entraînement du modèle
NumPy	Manipulation des données
MLflow	Suivi des expérimentations
Flask	Déploiement via API web
Docker	Conteneurisation
Git / GitHub	Versionnement 


