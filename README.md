C'est une excellente initiative. Pour que le projet reste cohérent, tout le monde doit utiliser la même base.

Voici le **Kit de Démarrage** complet à envoyer à tes amis. Il contient :

1. **Le Prompt** (la consigne pour l'IA).
2. **Le Template** (le code de base à copier-coller).
3. **Le Guide Workflow** (comment gérer le suivi des tâches avec le fichier JSON et Git).

---

### 📋 1. Le Prompt (À donner à l'IA)

Dis à tes amis de copier ce texte s'ils utilisent ChatGPT ou Claude pour générer une page :

> **Rôle :** Tu es un expert Front-End. Tu dois créer une nouvelle page pour "Vinci Arena" (plateforme de tournois e-sport).
> **Contraintes Techniques :**
> 1. Un seul fichier HTML (CSS dans `<style>`, JS dans `<script>`).
> 2. Pas de framework (CSS natif uniquement).
> 3. Responsive (Mobile-first).
> 
> 
> **Charte Graphique (Design System) :**
> * **Fond de page :** `#f0f2f5`
> * **Navbar :** Bleu `#112b4f`, Hauteur 70px, Texte blanc.
> * **Boutons principaux :** Bleu `#112b4f` (Hover `#1e40af`).
> * **Boutons accent (Inscription) :** Orange/Marron `#b45309`.
> * **Cartes :** Fond blanc `#ffffff`, Bordure `#e2e8f0`, Radius `8px`, Ombre légère `0 2px 10px rgba(0,0,0,0.03)`.
> * **Police :** 'Roboto', sans-serif.
> 
> 
> **Structure Obligatoire :**
> Utilise le code HTML de base fourni (Header standard + `<main class="main-container">`).
> **Ta mission :**
> [DÉCRIRE ICI LA PAGE À CRÉER. Ex: Fais la page de gestion des admins avec un tableau...]

---

### 🎨 2. Le Template de Base (Boilerplate)

C'est le code que tes amis doivent **copier dans leur nouveau fichier HTML** avant de commencer. Il contient déjà le bon design, la navbar complète (avec notifications) et le footer.

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Vinci Arena</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;600;700&display=swap" rel="stylesheet">

    <style>
        /* --- 1. VARIABLES & RESET --- */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { font-family: 'Roboto', sans-serif; background-color: #f0f2f5; color: #334155; line-height: 1.5; }

        /* --- 2. NAVBAR (Standard) --- */
        .navbar {
            background-color: #112b4f; height: 70px; padding: 0 40px;
            display: flex; justify-content: space-between; align-items: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1); position: sticky; top: 0; z-index: 1000;
        }
        .logo-img-nav { height: 45px; width: auto; border-radius: 4px; display: block; }
        .nav-links { display: flex; align-items: center; gap: 25px; }
        .nav-links a { color: white; text-decoration: none; font-weight: 500; font-size: 14px; transition: 0.2s; }
        .nav-links a:hover { text-decoration: underline; text-underline-offset: 4px; }
        
        .nav-user { display: flex; align-items: center; gap: 15px; border-left: 1px solid rgba(255,255,255,0.2); padding-left: 20px; margin-left: 10px; }
        .nav-notification { position: relative; color: white; display: flex; align-items: center; margin-right: 10px; }
        .notification-badge { position: absolute; top: -6px; right: -8px; background-color: #ef4444; color: white; font-size: 10px; font-weight: bold; padding: 2px 5px; border-radius: 10px; border: 2px solid #112b4f; }
        .nav-avatar { width: 35px; height: 35px; border-radius: 4px; background-color: white; padding: 2px; }

        /* --- 3. CONTENEUR PRINCIPAL --- */
        .main-container { max-width: 1000px; margin: 40px auto; padding: 0 20px; }
        .page-title { font-size: 28px; font-weight: 700; color: #0f172a; margin-bottom: 25px; }

        /* --- 4. COMPOSANTS (Cartes & Boutons) --- */
        .card {
            background-color: white; border-radius: 8px; padding: 25px;
            border: 1px solid #e2e8f0; box-shadow: 0 2px 10px rgba(0,0,0,0.03);
        }
        .btn-primary {
            background-color: #112b4f; color: white; padding: 10px 20px;
            border: none; border-radius: 6px; font-weight: 600; cursor: pointer; transition: 0.2s;
        }
        .btn-primary:hover { background-color: #1e40af; }

        /* Mobile */
        @media (max-width: 768px) {
            .navbar { padding: 15px; flex-direction: column; height: auto; gap: 15px; }
            .nav-user { border-left: none; padding-left: 0; margin-left: 0; width: 100%; justify-content: center; border-top: 1px solid rgba(255,255,255,0.2); padding-top: 15px; }
        }
    </style>
</head>
<body>

    <header class="navbar">
        <a href="accueil.html"><img src="image/imageLogo.png" alt="Logo" class="logo-img-nav"></a>
        <nav class="nav-links">
            <a href="accueil.html">Accueil</a>
            <a href="dashboard_membre.html">Tableau de bord</a>
            <a href="liste_tournois.html">Tournoi</a>
            <a href="equipes_publique.html">Equipe</a>
            <div class="nav-user">
                <a href="#" class="nav-notification">
                    <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2"><path d="M6 8a6 6 0 0 1 12 0c0 7 3 9 3 9H3s3-2 3-9"/><path d="M10.3 21a1.94 1.94 0 0 0 3.4 0"/></svg>
                    <span class="notification-badge">3</span>
                </a>
                <a href="connexion.html" style="font-size:13px;">Se déconnecter</a>
                <a href="profil.html"><img src="https://api.dicebear.com/7.x/avataaars/svg?seed=Felix" class="nav-avatar"></a>
            </div>
        </nav>
    </header>

    <main class="main-container">
        <h1 class="page-title">Nouvelle Page</h1>
        <div class="card">
            <p>Commencez à coder ici...</p>
        </div>
    </main>

</body>
</html>

```

---

### 📖 3. README : Workflow de Travail (Gestion des Tâches)

Ajoute cette section dans ton fichier `README.md` (ou envoie-le sur votre conversation de groupe Discord/WhatsApp). C'est crucial pour ne pas écraser le travail des autres.

```markdown
# 🛠️ Workflow de travail & Suivi des tâches

Pour travailler ensemble efficacement et garder le tableau de bord à jour, suivez scrupuleusement ces étapes.

### 📂 Structure des fichiers
- `index.html` : La page sommaire avec l'état des tâches (À faire / Fait).
- `data/ihm_status.json` : Le fichier qui stocke la mémoire du projet.

### 🚀 AVANT de commencer à travailler (Start)
1. **Récupérez les dernières modifs :**
   ```bash
   git pull origin main

```

2. Ouvrez `index.html` dans votre navigateur.
3. Cliquez sur le bouton **"📥 Recharger les statuts (JSON)"** en haut de la page.
*Cela va mettre à jour les badges (Rouge/Vert) avec l'état réel du projet.*

### 👨‍💻 PENDANT le travail

1. Créez votre fichier HTML (ex: `ma_page.html`) en utilisant le **Template de base**.
2. Codez votre page.
3. Une fois terminé, retournez sur `index.html`.
4. Cliquez sur le badge rouge **"À FAIRE"** correspondant à votre tâche pour le passer en vert **"FAIT"**.

### 💾 APRÈS le travail (End)

1. Un bouton flottant **"💾 Sauvegarder les changements"** est apparu en bas à droite. Cliquez dessus.
2. Un fichier `ihm_status.json` va se télécharger.
3. **IMPORTANT :** Prenez ce fichier téléchargé et remplacez l'ancien fichier qui se trouve dans le dossier `data/` de votre projet.
4. Envoyez tout sur Git :
```bash
git add .
git commit -m "Fini IHM XX + Mise à jour status JSON"
git push origin main

```



```

```