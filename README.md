# IT Quiz Challenge

Application web éducative autonome pour s'entraîner à l'informatique et à la cybersécurité, du niveau débutant au niveau avancé. Projet réalisé en HTML5, CSS3 et JavaScript natif, sans backend, dépendance ni API externe. Compatible avec GitHub Pages.

> **Important — prototype pédagogique uniquement.** L'authentification est locale et ne protège pas de vrais comptes. N'utilisez pas un mot de passe réutilisé ni des informations sensibles.

## Fonctionnalités

- Création de compte et connexion par identifiant ou e-mail; vérification des champs et prévention des doublons (casse ignorée).
- Dérivation du mot de passe par **PBKDF2-HMAC-SHA-256, 210 000 itérations, sel aléatoire de 16 octets par compte**, via Web Crypto. Le mot de passe en clair n'est jamais conservé.
- Session locale persistante après actualisation, contrôle de session avant affichage des vues internes et déconnexion.
- Tableau de bord individuel : nombre de quiz, meilleur score, moyenne, progression par niveau et dernières tentatives.
- Banque de **90 questions originales** (30 par niveau), réparties en domaines, avec QCM, vrai/faux et choix multiples, points et explications.
- Modes entraînement (correction après validation), examen (réponses révélées en fin de session), défi de 90 secondes et révision des réponses manquées.
- Résultats détaillés, durée, réponses correctes/incorrectes, explications et sauvegarde locale par profil.
- Suppression confirmée des statistiques de progression, sans effacer le compte.
- Interface responsive, navigation clavier, textes alternatifs sur les images et prise en compte de `prefers-reduced-motion`.

## Technologies

- HTML5 sémantique
- CSS3 responsive (styles locaux)
- JavaScript natif (ES6+)
- Web Crypto API pour PBKDF2
- `localStorage` pour les profils, la session et les statistiques
- Images locales générées pour ce projet

Aucun service distant n'est requis. Un navigateur récent avec Web Crypto est recommandé. Le calcul PBKDF2 peut ne pas être accessible sous certaines ouvertures directes `file://`; dans ce cas, lancer via l'extension Live Server de VS Code (ou utiliser GitHub Pages/localhost). L'application ne requiert pas de serveur applicatif ni d'installation de dépendances.

## Arborescence

```text
it-quiz-challenge/
├── index.html
├── README.md
├── LICENSE
├── .gitignore
├── assets/
│   ├── css/style.css
│   ├── js/app.js
│   ├── js/questions.js
│   └── images/
│       ├── beginner.jpg
│       ├── intermediate.jpg
│       └── advanced.jpg
├── docs/
│   ├── tests-execution.md
│   └── captures/
│       ├── tableau-de-bord.png
│       └── quiz.png
└── tests/
    └── checklist-tests.md
```

## Lancer localement

1. Téléchargez ou clonez le dépôt.
2. Ouvrez `index.html` dans un navigateur moderne. Si Web Crypto n'est pas disponible en ouverture `file://`, ouvrez le dossier dans VS Code et lancez `index.html` avec **Live Server** (ou utilisez un serveur statique local équivalent).
3. Créez un compte de démonstration. L'identifiant doit faire 3 à 24 caractères et le mot de passe au moins 12 caractères.
4. Choisissez un niveau, un domaine et un mode puis démarrez le quiz.

Les fonctionnalités ne nécessitent ni `npm install`, ni backend.

## Publication sur GitHub Pages

1. Créez un dépôt GitHub et ajoutez les fichiers du dossier du projet à sa racine.
2. Dans **Settings → Pages**, choisissez **Deploy from a branch**, puis la branche `main` et le dossier `/ (root)`.
3. Enregistrez. Lorsque GitHub Pages a terminé le déploiement, ouvrez l'URL fournie par GitHub. Les chemins de ressources sont relatifs.
4. Les données LocalStorage sont isolées par origine de navigateur : le profil créé sur localhost ne migre pas vers l'URL GitHub Pages.

## Données locales et sécurité — à lire

Les clés de stockage sont `itqc_users_v1`, `itqc_session_v1` et `itqc_stats_v1`. Les comptes conservent l'identifiant, l'e-mail, un sel aléatoire et le résultat de PBKDF2; ils ne conservent pas le mot de passe en clair. Les statistiques sont indexées par identifiant de profil pour séparer logiquement les parcours dans l'interface.

Cette séparation n'est **pas une isolation de sécurité**. Toute personne ayant accès au même navigateur/profil peut consulter, copier, supprimer ou modifier le LocalStorage. Le code s'exécute côté client et peut être modifié; une XSS ou une extension malveillante peut lire les données accessibles. Le hachage ralentit certains essais hors ligne mais ne transforme pas le navigateur en service d'authentification sécurisé. Il n'y a ni vérification d'adresse e-mail, ni récupération de compte, ni synchronisation entre appareils. N'utilisez pas la fonction de mot de passe pour un compte réel. Des comptes réellement protégés exigent un backend sécurisé, des contrôles d'accès serveur, une gestion de session et un stockage de mots de passe appropriés.

Le bouton de suppression de progression demande confirmation et ne supprime que les statistiques du profil actuellement connecté. La suppression du navigateur efface toutes les données locales.

## Tester manuellement

Consultez [`tests/checklist-tests.md`](tests/checklist-tests.md) pour la checklist de recette. Des contrôles automatisés statiques et des essais navigateur effectués sont décrits dans [`docs/tests-execution.md`](docs/tests-execution.md). Pour vérifier le flux : créer un compte neuf, essayer une connexion incorrecte puis correcte, recharger, lancer chacun des modes, examiner les corrections et vérifier le tableau de bord. La banque de questions se trouve dans `assets/js/questions.js`.

## Licence et images

Le code est distribué sous licence MIT (voir `LICENSE`). Les trois visuels locaux ont été générés spécifiquement pour ce projet avec un outil de génération d'images; ils ne sont pas des photographies documentaires et ne comportent pas d'attribution externe connue.
