C'est une excellente idée ! Pour que tes amis (ou une IA qu'ils utiliseraient) puissent créer de nouvelles pages qui s'intègrent parfaitement avec celles qu'on vient de faire, il leur faut un **"Design System"** (les couleurs, la police, les ombres) et une consigne stricte.

Voici ce que tu peux leur envoyer. Il y a **un prompt à copier-coller** (si tes amis utilisent une IA comme moi) et **le code CSS de base** (le "Template") à utiliser à chaque fois.

---

### 📋 1. Le Prompt (À donner à l'IA ou au développeur)

Copie-colle ce texte pour générer une nouvelle page :

> **Contexte :**
> Agis comme un développeur front-end expert. Tu dois créer une nouvelle page web pour le projet "Vinci Arena", une plateforme de gestion de tournois e-sport.
> **Règles techniques :**
> 1. Génère un seul fichier contenant HTML, CSS (dans la balise `<style>`) et JS (dans `<script>`).
> 2. N'utilise AUCUN framework CSS (pas de Bootstrap, pas de Tailwind). Tout doit être fait en CSS natif.
> 3. La page doit être 100% responsive (mobile-first pour les grilles).
> 
> 
> **Charte Graphique stricte (Vinci Arena) :**
> * **Police :** 'Roboto', sans-serif (depuis Google Fonts).
> * **Couleur de fond de la page :** `#f0f2f5` (Gris très clair).
> * **Barre de navigation (Header) :** Fond `#112b4f` (Bleu marine), Hauteur 70px, ombrée.
> * **Texte principal :** `#334155` (Gris foncé).
> * **Texte secondaire :** `#64748b` (Gris moyen).
> * **Couleurs d'accentuation :** Bleu primaire (`#2563eb`), Orange/Doré (`#f59e0b`), Marron/Bouton d'inscription (`#b45309`).
> * **Cartes (Cards) :** Fond blanc (`#ffffff`), bordure très légère (`1px solid #e2e8f0`), coins arrondis (`border-radius: 8px`), et une ombre douce au survol (`box-shadow: 0 8px 20px rgba(0,0,0,0.06)`).
> 
> 
> **Structure requise :**
> Utilise le template de base de Vinci Arena (Barre de navigation standard en haut, puis une balise `<main class="main-container">` au centre d'une largeur max de 1000px ou 1200px).
> **Mission :**
> [INSÈRE ICI LA DESCRIPTION DE LA PAGE SOUHAITÉE. Ex: "Crée la page de création d'un tournoi avec un formulaire complet..."]

---

### 🎨 2. Le Template HTML/CSS de base (Le "Boilerplate")

Dis à tes amis de **toujours commencer avec ce code**. C'est le squelette officiel du site. Ils n'auront plus qu'à coder l'intérieur de la balise `<main>`.

```html
<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nouvelle Page - Vinci Arena</title>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;500;600;700;900&display=swap" rel="stylesheet">

    <style>
        /* =========================================
           1. RESET & VARIABLES DE BASE
           ========================================= */
        * { box-sizing: border-box; margin: 0; padding: 0; }
        body { 
            font-family: 'Roboto', sans-serif; 
            background-color: #f0f2f5; /* Fond officiel */
            color: #334155; 
            line-height: 1.5;
        }

        /* =========================================
           2. BARRE DE NAVIGATION (Ne pas modifier)
           ========================================= */
        .navbar {
            background-color: #112b4f;
            height: 70px;
            padding: 0 40px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.1);
            position: sticky;
            top: 0;
            z-index: 1000;
        }
        .logo-img-nav { height: 45px; width: auto; border-radius: 4px; display: block; }
        .nav-links { display: flex; align-items: center; gap: 30px; }
        .nav-links a { color: white; text-decoration: none; font-weight: 500; font-size: 15px; transition: color 0.2s; }
        .nav-links a:hover { text-decoration: underline; text-underline-offset: 4px; }
        .nav-links a.active { color: #f59e0b; font-weight: 700; }
        
        .btn-register {
            background-color: #b45309; 
            color: white !important;
            padding: 10px 24px;
            border-radius: 4px;
            font-weight: 700;
            text-decoration: none !important;
            transition: 0.2s;
        }
        .btn-register:hover { background-color: #92400e; }

        /* Utilisateur connecté (Avatar) */
        .nav-user {
            display: flex; align-items: center; gap: 15px;
            border-left: 1px solid rgba(255,255,255,0.2);
            padding-left: 20px; margin-left: 10px;
        }
        .nav-avatar {
            width: 35px; height: 35px; border-radius: 4px;
            background-color: white; padding: 2px;
        }

        /* =========================================
           3. LAYOUT PRINCIPAL ET COMPOSANTS
           ========================================= */
        .main-container {
            max-width: 1000px; /* Ou 1200px selon le besoin */
            margin: 40px auto;
            padding: 0 20px;
        }

        .page-title {
            font-size: 28px;
            font-weight: 700;
            color: #0f172a;
            margin-bottom: 25px;
        }

        /* Style des cartes standard */
        .card {
            background-color: #ffffff;
            border-radius: 8px;
            padding: 25px;
            border: 1px solid #e2e8f0;
            box-shadow: 0 2px 10px rgba(0,0,0,0.03);
            transition: transform 0.2s, box-shadow 0.2s;
        }
        .card:hover {
            transform: translateY(-3px);
            box-shadow: 0 8px 20px rgba(0,0,0,0.06);
            border-color: #cbd5e1;
        }

        /* Style des boutons standard */
        .btn-primary {
            background-color: #112b4f;
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 6px;
            font-weight: 600;
            cursor: pointer;
            transition: 0.2s;
        }
        .btn-primary:hover { background-color: #1e40af; }

        /* =========================================
           4. RESPONSIVE MOBILE
           ========================================= */
        @media (max-width: 768px) {
            .navbar { padding: 15px 20px; flex-direction: column; height: auto; gap: 15px; }
            .nav-links { flex-wrap: wrap; justify-content: center; gap: 15px; }
            .nav-user { border-left: none; padding-left: 0; margin-left: 0; border-top: 1px solid rgba(255,255,255,0.2); padding-top: 15px; width: 100%; justify-content: center;}
        }
    </style>
</head>
<body>

    <header class="navbar">
        <a href="accueil.html">
            <img src="image/imageLogo.png" alt="Logo Vinci Arena" class="logo-img-nav">
        </a>
        
        <nav class="nav-links">
            <a href="accueil.html">Accueil</a>
            <a href="dashboard_membre.html">Tableau de bord</a>
            <a href="liste_tournois.html">Tournoi</a>
            <a href="equipes_publique.html">Equipe</a>
            
            <div class="nav-user">
                <a href="connexion.html">Se déconnecter</a>
                <a href="profil.html">
                    <img src="https://api.dicebear.com/7.x/avataaars/svg?seed=Felix" alt="Avatar Navbar" class="nav-avatar">
                </a>
            </div>
        </nav>
    </header>

    <main class="main-container">
        
        <h1 class="page-title">Titre de la page</h1>
        
        <div class="card">
            <p>Le contenu de la nouvelle IHM va ici...</p>
            <br>
            <button class="btn-primary">Exemple de bouton</button>
        </div>

    </main>

</body>
</html>

```

### 💡 Comment l'utiliser avec tes amis :

S'ils doivent faire la page **"Centre de notifications" (IHM 36)** par exemple, ils ont juste à donner le **Prompt** à l'IA, ajouter à la fin : *"Crée la page Centre de notifications avec une liste des messages lus et non lus"*, et l'IA va générer une page qui aura exactement la même tête que toutes celles qu'on a faites ensemble !