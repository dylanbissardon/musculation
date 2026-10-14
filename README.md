# Muscu — Résistance adaptative (V3)

Application web mobile-first pour suivre la résistance par exercice et équipement.

## Fonctions
- Recommandations à partir de l’inventaire disponible.
- Progression selon le ressenti : facile (+ un niveau réalisable), difficile (stable), impossible (− un niveau réalisable).
- Historique séparé par exercice et équipement.
- Connexion par lien e-mail Supabase pour synchroniser l’historique entre appareils.
- Application installable sur iPhone et utilisable sur Mac.
- Historique local conservé en secours si la synchronisation est indisponible.

## Configuration Supabase
Dans **Authentication → URL Configuration** :
- Site URL : `https://dylanbissardon.github.io/musculation/`
- Ajouter cette même URL dans **Redirect URLs**.

La table `public.workout_history` doit exister avec les politiques RLS de lecture, insertion et suppression limitées à `auth.uid() = user_id`. Le navigateur utilise uniquement la clé publishable publique ; ne jamais mettre une clé `service_role` dans le site.

## Connexion iPhone depuis l’écran d’accueil

Pour éviter que le lien magique ouvre Safari dans un contexte séparé de l’application installée, la V3 utilise un code e-mail à saisir directement dans Muscu.

Dans **Authentication → Email Templates → Magic Link**, configure le contenu du courriel pour afficher le code, par exemple :

`Ton code de connexion Muscu : {{ .Token }}`

Enregistre le modèle. Dans Muscu, demande ensuite un code et saisis-le dans le champ prévu, sans cliquer sur le lien magique de l’e-mail.

## Installer sur iPhone
1. Ouvrir `https://dylanbissardon.github.io/musculation/` dans Safari.
2. Appuyer sur **Partager** puis **Sur l’écran d’accueil**.
3. Ouvrir Muscu depuis l’icône ajoutée. Pour synchroniser, se connecter avec la même adresse e-mail sur les deux appareils.

Les modifications poussées sur la branche `main` sont publiées par GitHub Pages après quelques instants.
