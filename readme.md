# 🚀 Comment faire un site avec GitHub Pages

## 1. Crée un compte GitHub (si tu n’en as pas déjà un)
👉 https://github.com

## 2. Crée un nouveau dépôt

- Nom du dépôt : par exemple mon-site
- Public ou privé (public est requis pour GitHub Pages gratuits sur les comptes gratuits)
- Initialise avec un README.md (optionnel)

## 3. Ajoute tes fichiers HTML/CSS/JS

Tu peux :
- Utiliser l’interface web (bouton "Add file" > "Upload files")
- Ou cloner le dépôt localement avec Git, et y copier ton projet

Par exemple :
```css
/mon-site
├── index.html
├── header.html
├── footer.html
├── styles.css
└── script.js
```

## 4. Activer GitHub Page
1. Va dans l’onglet "Settings" de ton dépôt.
2. Dans le menu à gauche, clique sur "Pages" (ou "Pages" dans "Code and automation").
3. Sous "Build and deployment" > "Source", choisis :
    - Branch : main (ou master)
    - Folder : / (root)
4. Clique sur "Save"

## 5. Accède à ton site
Après quelques secondes, GitHub va générer ton site à l’URL :
```php-template
https://<ton-utilisateur>.github.io/<nom-du-depot>/
```

Exemple :
```arduino
https://juliendupont.github.io/mon-site/
```