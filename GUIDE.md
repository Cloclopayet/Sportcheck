# 📱 SportCheck — Guide de mise en ligne et installation

## Ce que contient ce dossier

```
sportcheck-app/
├── index.html        → L'application complète
├── manifest.json     → Définition PWA (icône, nom, couleurs)
├── sw.js             → Service Worker (mode offline)
├── icons/            → Icônes pour Android et iPhone
│   ├── icon-72.png
│   ├── icon-96.png
│   ├── icon-128.png
│   ├── icon-144.png
│   ├── icon-152.png  ← iPhone
│   ├── icon-192.png  ← Android
│   ├── icon-384.png
│   └── icon-512.png  ← Android splash
└── GUIDE.md          → Ce fichier
```

---

## 🚀 Étape 1 — Héberger sur GitHub Pages (GRATUIT, HTTPS automatique)

### Créer un compte GitHub (si pas encore fait)
1. Allez sur **github.com**
2. Cliquez "Sign up" → créez un compte gratuit

### Mettre l'app en ligne
1. Connectez-vous sur **github.com**
2. Cliquez le bouton vert **"New"** (nouveau dépôt)
3. Nom du dépôt : `sportcheck` (tout en minuscules)
4. Cochez **"Public"**
5. Cliquez **"Create repository"**

### Uploader les fichiers
1. Sur la page du dépôt, cliquez **"uploading an existing file"**
2. Glissez-déposez **tout le contenu** du dossier `sportcheck-app/` :
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - Le dossier `icons/` avec les 8 fichiers PNG
3. En bas, cliquez **"Commit changes"**

### Activer GitHub Pages
1. Dans votre dépôt, allez dans **Settings** (onglet en haut)
2. Dans le menu gauche, cliquez **"Pages"**
3. Sous "Source", choisissez **"Deploy from a branch"**
4. Branch : **"main"** → dossier : **"/ (root)"**
5. Cliquez **"Save"**
6. Attendez 2-3 minutes → votre URL sera :
   **`https://VOTRE-NOM.github.io/sportcheck/`**

---

## 📱 Étape 2 — Installer sur Android

1. Ouvrez l'URL dans **Chrome**
2. Une bannière verte apparaît en bas : **"Installer SportCheck"**
3. Tapez **"Installer"**
4. L'icône apparaît sur votre écran d'accueil
5. L'app s'ouvre en plein écran (sans barre navigateur)

> Si la bannière n'apparaît pas : tapez les 3 points en haut à droite → **"Ajouter à l'écran d'accueil"**

---

## 🍎 Étape 3 — Installer sur iPhone / iPad

1. Ouvrez l'URL dans **Safari** (⚠️ pas Chrome sur iPhone)
2. Tapez le bouton **Partager** (carré avec une flèche vers le haut)
3. Faites défiler → tapez **"Sur l'écran d'accueil"**
4. Tapez **"Ajouter"**
5. L'icône SportCheck apparaît sur votre écran d'accueil

---

## ⚙️ Étape 4 — Configurer Google Cloud (Gmail + Drive)

Un seul Client ID OAuth suffit pour Gmail ET Google Drive.

### Créer le projet Google Cloud
1. Allez sur **console.cloud.google.com**
2. Cliquez sur le menu déroulant en haut → **"Nouveau projet"**
3. Nom : `SportCheck` → **"Créer"**

### Activer les APIs nécessaires
1. Menu gauche → **"APIs et services"** → **"Bibliothèque"**
2. Recherchez **"Gmail API"** → **"Activer"**
3. Recherchez **"Google Drive API"** → **"Activer"**

### Créer les identifiants OAuth
1. Menu gauche → **"APIs et services"** → **"Identifiants"**
2. Cliquez **"+ Créer des identifiants"** → **"ID client OAuth"**
3. Type d'application : **"Application Web"**
4. Nom : `SportCheck`
5. Dans **"Origines JavaScript autorisées"**, ajoutez :
   - `https://VOTRE-NOM.github.io`
   - (Pour tests locaux : `http://localhost`)
6. Cliquez **"Créer"**
7. Copiez le **Client ID** (format: `xxxxxxxxxxxx.apps.googleusercontent.com`)

### Configurer l'écran de consentement
1. Menu gauche → **"Écran de consentement OAuth"**
2. Type : **"Externe"** → **"Créer"**
3. Nom de l'application : `SportCheck`
4. Email : votre adresse Gmail
5. Sauvegardez (pas besoin de tout remplir)
6. Ajoutez votre email comme **"Utilisateur test"**

### Entrer le Client ID dans l'app
1. Ouvrez SportCheck
2. Tapez **⚙️** → Section **"Gmail — Envoi direct"**
3. Collez le Client ID
4. Section **"Google Drive"** → même Client ID
5. Tapez **"💾 Enregistrer"**

---

## 🔄 Fonctionnement hors ligne

L'app fonctionne **sans connexion internet** une fois installée :
- Tous les formulaires fonctionnent offline
- La génération PDF fonctionne offline
- L'envoi Gmail nécessite une connexion (normal)
- La sauvegarde Drive nécessite une connexion (normal)

---

## 🔗 Partager l'accès

Pour que vos techniciens accèdent à l'app :
- Envoyez-leur simplement l'URL : `https://VOTRE-NOM.github.io/sportcheck/`
- Chaque technicien installe l'app sur son smartphone
- Chaque appareil garde ses propres paramètres (config locale)

---

## 🔧 Mettre à jour l'app

Pour mettre à jour l'application :
1. Allez sur votre dépôt GitHub
2. Cliquez sur `index.html` → icône crayon (modifier)
3. Ou bien uploadez le nouveau `index.html` par glisser-déposer
4. GitHub Pages se met à jour automatiquement en 2-3 minutes

---

## ❓ Résolution de problèmes

**La bannière d'installation n'apparaît pas sur Android :**
→ L'app doit être en HTTPS (GitHub Pages = OK). Vérifiez que vous utilisez Chrome.

**Sur iPhone, "Sur l'écran d'accueil" n'est pas visible :**
→ Faites défiler vers le bas dans la liste de partage Safari.

**L'email Gmail ne part pas :**
→ Vérifiez que votre email est ajouté comme "Utilisateur test" dans Google Cloud Console (section Écran de consentement OAuth).

**Le PDF est vide ou mal formaté :**
→ Attendez que la page soit complètement chargée avant de générer. Sur iPhone, utilisez "Imprimer" → PDF comme alternative.

**Erreur "Not allowed" sur Drive :**
→ Ajoutez bien `https://VOTRE-NOM.github.io` dans les origines autorisées du Client ID OAuth.
