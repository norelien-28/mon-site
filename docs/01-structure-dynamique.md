## 🗂️ Organisation recommandée (simple et claire)
```
/projet
├── index.html               ← page principale (layout)
├── header.html
├── footer.html
├── assets/
│   └── styles.css
├── categories/
│   ├── html/
│   │   ├── intro.html
│   │   └── balises.html
│   ├── css/
│   │   ├── flexbox.html
│   │   └── grid.html
│   └── js/
│       ├── dom.html
│       └── events.html
```

---

## 🔄 Amélioration du index.html (layout) pour charger dynamiquement n’importe quelle page d’astuce :
```html
<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8" />
  <title>Astuces Dev</title>
  <link rel="stylesheet" href="assets/styles.css" />
</head>
<body>
  <div id="header"></div>

  <main id="content">
    <p>Chargement...</p>
  </main>

  <div id="footer"></div>

  <script>
    // Charger le header et footer
    fetch('header.html').then(r => r.text()).then(html => header.innerHTML = html);
    fetch('footer.html').then(r => r.text()).then(html => footer.innerHTML = html);

    // Lire l’URL: ?cat=html&page=intro
    const params = new URLSearchParams(window.location.search);
    const cat = params.get("cat");
    const page = params.get("page");

    // Si pas de page, afficher un accueil par défaut
    if (!cat || !page) {
      document.getElementById("content").innerHTML = `
        <h1>Bienvenue !</h1>
        <p>Choisissez une catégorie d'astuces ci-dessus.</p>
      `;
    } else {
      const path = `categories/${cat}/${page}.html`;
      fetch(path)
        .then(r => {
          if (!r.ok) throw new Error("Page introuvable");
          return r.text();
        })
        .then(html => content.innerHTML = html)
        .catch(() => content.innerHTML = `<p>❌ Cette astuce n'existe pas.</p>`);
    }
  </script>
</body>
</html>
```

## 🧭 Exemple de navigation dans ton menu (header.html) :
```html
<header>
  <nav>
    <a href="index.html">Accueil</a>
    <a href="index.html?cat=html&page=intro">HTML - Introduction</a>
    <a href="index.html?cat=html&page=balises">HTML - Balises</a>
    <a href="index.html?cat=css&page=flexbox">CSS - Flexbox</a>
    <a href="index.html?cat=js&page=dom">JS - DOM</a>
  </nav>
</header>
```

## ✅ Avantages de cette approche
| Avantage                           | Détail                                                               |
| ---------------------------------- | -------------------------------------------------------------------- |
| 📦 **Structure claire**            | Chaque astuce est un fichier HTML simple                             |
| ♻️ **Layout réutilisé**            | Pas de duplication de code                                           |
| 🌍 **Fonctionne sur GitHub Pages** | Pas besoin de backend                                                |
| ⚙️ **Facile à maintenir/éditer**   | Tu ajoutes un fichier dans un dossier pour créer une nouvelle astuce |
| 🧱 **URL claires et lisibles**     | `?cat=css&page=grid` par exemple                                     |

## 🧰 Bonus (optionnel)
Tu pourrais aussi :
- Avoir une page index par catégorie (categories/css/index.html)
- Générer une liste dynamique des astuces (si tu veux automatiser)
- Ajouter un petit système de recherche ou de filtrage par JS

## 🔄 En résumé
Tu peux parfaitement faire ton projet "astuces par catégorie" avec GitHub Pages en :
1. Utilisant un layout unique (index.html)
2. Structurant les contenus par dossier (/categories/html/balises.html, etc.)
3. Naviguant avec des paramètres d’URL (?cat=html&page=balises)
4. Chargeant dynamiquement les contenus dans <main>