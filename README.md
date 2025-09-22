# 🛠️ QA Postman / Newman
Collection de tests API pour ReqRes
Les tests couvrent : 
- GET (Single user & all users)
- POST (Single user)
- PUT (User 2)
- PATCH (User 2)
- DELETE (User 3)


## 📁 Installation
```bash
git clone https://github.com/Arwouin/postman-playground.git
cd postman-playground
npm install
```

Installation de Newman (Optionnel)
```bash
npm install -g newman
```

## 📋 Lancement des tests
1. Ouvrir Postman ou installation via "https://www.postman.com/downloads/"
2. Importer la collection `collection.json`
3. Importer l'environnement `environment.json`
4. Lancer la collection manuellement

### Avec Newman
```bash
newman run collections/collection.json -e environment.json -r cli,html
```
Le rapport HTML est généré automatiquement avec le workflow GitHub Actions (N'est pas stocké dans le repo)


## 🪛 Structure du projet
- collections/ --> Fichier JSON Postman
- environments/ --> Fichier JSON environnements
- workflows/ --> Fichier GitHub Actions (CI) pour exécution automatique


## 😺 Exécution en intégration continue (CI) - Github Actions
Exemple : 
```yaml
name: Newman CI
on: [push]

jobs:
 test:
  runs-on: ubuntu-latest
  steps:
    - uses: actions/checkout@v4
    - run: npm install newman
    - run: newman run collections/collection.json -e environments/environment.json -r cli,html
```
