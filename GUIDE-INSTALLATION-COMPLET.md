# 📱 SportCheck — Guide d'installation et configuration complet
### Pour le responsable et les techniciens

---

## 🗺️ VUE D'ENSEMBLE — Ce qu'on va faire

```
ÉTAPE 1 → Créer le projet Google Cloud (fait 1 seule fois par le responsable)
ÉTAPE 2 → Récupérer le Client ID Google
ÉTAPE 3 → Installer l'app sur chaque téléphone
ÉTAPE 4 → Configurer l'app sur chaque téléphone (5 minutes par appareil)
ÉTAPE 5 → Faire le premier test
```

**Qui fait quoi ?**
- **Étapes 1 et 2** → Le responsable (une seule fois, sur ordinateur)
- **Étapes 3 et 4** → Chaque technicien sur son propre téléphone

---

## 📋 CE QUI EST SAUVEGARDÉ SUR CHAQUE TÉLÉPHONE

| Information | Sauvegardée sur le tel ? | À re-saisir ? |
|---|---|---|
| Nom de société, adresse, agrément | ✅ Oui | Jamais (1 fois) |
| Client ID Google | ✅ Oui | Jamais (1 fois) |
| Email de réception des rapports | ✅ Oui | Jamais (1 fois) |
| Logo société | ✅ Oui | Jamais (1 fois) |
| Technicien par défaut | ✅ Oui | Jamais (1 fois) |
| Autorisation Google (Gmail/Drive) | ❌ Non | À chaque session (2 clics) |

> ⚠️ **Important** : L'autorisation Google expire toutes les heures pour des raisons de sécurité. Ce n'est pas une saisie de mot de passe — c'est juste un clic "Autoriser" sur une fenêtre Google qui s'ouvre automatiquement.

---

## 🔧 ÉTAPE 1 — Créer le projet Google Cloud
*(Fait une seule fois par le responsable, sur ordinateur)*

### 1.1 Aller sur Google Cloud Console
1. Ouvre **console.cloud.google.com** dans ton navigateur
2. Connecte-toi avec le compte Gmail de la société
3. En haut, clique sur le menu déroulant → **"Nouveau projet"**
4. Nom : `SportCheck`
5. Clique **"Créer"** — attends 30 secondes

### 1.2 Activer Gmail API
1. Menu gauche → **"APIs et services"** → **"Bibliothèque"**
2. Tape `Gmail API` dans la recherche → clique dessus → **"Activer"**

### 1.3 Activer Google Drive API
1. Retourne dans la bibliothèque
2. Tape `Google Drive API` → clique dessus → **"Activer"**

### 1.4 Configurer l'écran de consentement OAuth
1. Menu gauche → **"APIs et services"** → **"Écran de consentement OAuth"**
2. Type : **"Externe"** → **"Créer"**
3. Remplis :
   - Nom de l'application : `SportCheck`
   - Email assistance : ton adresse Gmail
   - Email développeur : ton adresse Gmail
4. Clique **"Enregistrer et continuer"** (3 fois jusqu'à la fin)
5. Dans la section **"Utilisateurs test"**, clique **"+ Add Users"**
6. Ajoute les adresses Gmail de **tous tes techniciens** (une par une)
7. Clique **"Enregistrer"**

> 💡 Tant que l'app n'est pas publiée officiellement sur Google, seuls les "utilisateurs test" peuvent l'utiliser. Ajoute l'adresse de chaque technicien ici.

### 1.5 Créer les identifiants OAuth
1. Menu gauche → **"APIs et services"** → **"Identifiants"**
2. Clique **"+ Créer des identifiants"** → **"ID client OAuth"**
3. Type d'application : **"Application Web"**
4. Nom : `SportCheck PWA`
5. Dans **"Origines JavaScript autorisées"**, ajoute :
   ```
   https://sportcheck-app.netlify.app
   ```
6. Clique **"Créer"**
7. Une fenêtre s'ouvre avec ton **Client ID** — il ressemble à :
   ```
   123456789012-abcdefghijklmnop.apps.googleusercontent.com
   ```
8. **COPIE CE CLIENT ID** — tu en as besoin pour l'étape 4

---

## 📱 ÉTAPE 2 — Installer l'app sur un téléphone

### Sur iPhone / iPad (obligatoire : Safari)
1. Ouvre **Safari** (⚠️ pas Chrome, pas Firefox)
2. Va sur : **https://sportcheck-app.netlify.app**
3. Attends que la page charge complètement
4. Appuie sur le bouton **Partager** (carré avec flèche ↑ en bas de l'écran)
5. Fais défiler la liste vers le bas → appuie **"Sur l'écran d'accueil"**
6. Nom : laisse `SportCheck` → appuie **"Ajouter"**
7. ✅ L'icône SportCheck apparaît sur ton écran d'accueil

### Sur Android (obligatoire : Chrome)
1. Ouvre **Chrome**
2. Va sur : **https://sportcheck-app.netlify.app**
3. Une bannière s'affiche en bas : **"Installer SportCheck"** → appuie dessus
4. Si la bannière n'apparaît pas : appuie sur les **3 points** (⋮) en haut à droite → **"Ajouter à l'écran d'accueil"**
5. ✅ L'icône SportCheck apparaît sur ton écran d'accueil

> ⚠️ **Toujours ouvrir l'app depuis l'icône** (pas depuis le navigateur) pour que tout fonctionne correctement.

---

## ⚙️ ÉTAPE 3 — Configurer l'app sur chaque téléphone
*(5 minutes par appareil — fait une seule fois)*

1. Ouvre **SportCheck** depuis l'icône sur l'écran d'accueil
2. Appuie sur l'icône **⚙️** en haut à droite
3. Remplis chaque champ :

### Section "Votre société"
| Champ | Quoi mettre |
|---|---|
| Nom société | Ex: `Green Sport Engineering SAS` |
| Adresse | Ex: `ZI La Mare — 97490 Sainte-Clotilde` |
| Tél / Email société | Ex: `+262 692 XX XX XX` |
| Agrément / N° SIRET | Ex: `CTNSI-2024-0342` |
| Technicien par défaut | Le prénom et nom du technicien de ce téléphone |

### Section "Logo"
- Appuie sur **"Choisir un logo"** → sélectionne le logo de la société depuis tes photos

### Section "Gmail — Envoi direct"
| Champ | Quoi mettre |
|---|---|
| Client ID OAuth | Colle le Client ID copié à l'étape 1.5 |
| Email destinataire | L'adresse qui reçoit les rapports (ex: `direction@votresociete.re`) |

### Section "Google Drive — Sauvegarde"
| Champ | Quoi mettre |
|---|---|
| Client ID OAuth | Le même Client ID qu'au-dessus |
| ID dossier Drive | (Optionnel) L'ID du dossier Drive où sauvegarder |

> 💡 **Comment trouver l'ID d'un dossier Drive ?** Ouvre le dossier sur drive.google.com — l'ID est la suite de lettres/chiffres dans l'URL après `/folders/`

4. Appuie **"💾 Enregistrer"**
5. ✅ Configuration terminée — ces paramètres sont mémorisés définitivement sur ce téléphone

---

## 🚀 ÉTAPE 4 — Faire le premier test

1. Lance **SportCheck** depuis l'icône
2. **Étape 1 — Info** : remplis Client, Technicien, Date
3. **Étape 2 — Matériel** : sélectionne un type (ex: 🛝 Sol Amortissant)
4. **Étape 3 — Contrôle** : coche quelques points
5. **Étape 6 — Conclusion** : sélectionne "Équipement conforme"
6. Appuie **"✅ Terminer le rapport"**
7. Une fenêtre s'ouvre → appuie **"☁️ Sauvegarder sur Drive"**

### 🔑 Première autorisation Google
Une fenêtre Google va s'ouvrir et demander :
> *"SportCheck veut accéder à votre compte Google"*

1. Sélectionne le compte Gmail du technicien
2. Appuie **"Autoriser"**
3. La fenêtre se ferme → le rapport est sauvegardé sur Drive

> ✅ **Cette fenêtre reviendra à chaque session** (environ toutes les heures) — c'est normal, c'est la sécurité Google. C'est juste 2 clics, pas une re-saisie de mot de passe.

---

## 📂 OÙ RETROUVER LES RAPPORTS

### Sur Google Drive
- Va sur **drive.google.com**
- Les rapports sont sauvegardés comme des **Google Docs modifiables**
- Tu peux corriger les fautes, ajouter des commentaires, imprimer en PDF

### Dans l'historique de l'app
- Dans SportCheck, appuie sur **"📚 Historique"** en bas
- Tous les rapports générés sur ce téléphone sont listés

---

## ❓ PROBLÈMES FRÉQUENTS

**"L'app ne s'installe pas sur iPhone"**
→ Utilise obligatoirement **Safari** (pas Chrome)

**"La fenêtre Google ne s'ouvre pas"**
→ Vérifie que le Client ID est bien saisi dans ⚙️ Paramètres
→ Vérifie que l'adresse Gmail du technicien est dans les "Utilisateurs test" (étape 1.4)

**"Erreur lors de la sauvegarde Drive"**
→ Vérifie que `https://sportcheck-app.netlify.app` est bien dans les origines autorisées (étape 1.5)

**"Le rapport s'est perdu"**
→ Retrouve-le dans l'historique de l'app (icône 📚)
→ Ou dans Google Drive si Drive était configuré

**"Je ne vois pas la carte GPS sur le rapport"**
→ Autorise la localisation quand l'app le demande
→ Sur iPhone : Réglages → Confidentialité → Localisation → Safari/SportCheck → "Lors de l'utilisation"

---

## 🔄 METTRE À JOUR L'APP

L'app se met à jour automatiquement dès que tu l'ouvres avec une connexion internet.
Un message discret apparaît : *"🔄 Nouvelle version dispo — rechargez pour l'activer"*
→ Ferme et rouvre l'app pour appliquer la mise à jour.

---

## 📞 RÉCAPITULATIF — Fiche rapide technicien

```
┌─────────────────────────────────────────────┐
│  SPORTCHECK — FICHE RAPIDE TECHNICIEN        │
├─────────────────────────────────────────────┤
│  URL : sportcheck-app.netlify.app            │
│                                              │
│  INSTALLATION (1 fois) :                     │
│  iPhone → Safari → Partager → Écran accueil  │
│  Android → Chrome → Installer                │
│                                              │
│  CONFIGURATION (1 fois) :                    │
│  ⚙️ → Remplis tout → Enregistrer             │
│                                              │
│  À CHAQUE RAPPORT :                          │
│  1. Ouvrir depuis l'ICÔNE (pas le nav.)      │
│  2. Remplir les 6 étapes                     │
│  3. Terminer → Autoriser Google (2 clics)    │
│  4. Le rapport part sur Drive                │
└─────────────────────────────────────────────┘
```

