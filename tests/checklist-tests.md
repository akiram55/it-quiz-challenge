# Checklist de recette — IT Quiz Challenge

**Légende :** ☑ vérifié dans le navigateur local le 20/10/2026 · ☐ reste à faire · ◐ vérification partielle. Les détails d'exécution et les limites des essais sont dans [`../docs/tests-execution.md`](../docs/tests-execution.md).

| Vérification | Résultat attendu | État |
|---|---|---|
| Afficher l'accueil sans session | Écran de connexion initial | ☑ |
| Soumettre une connexion vide | Message d'erreur clair | ☐ |
| Créer un compte avec champs manquants | Refus, aucune création | ☐ |
| E-mail mal formé | Refus avec message explicite | ☐ |
| Mot de passe de moins de 12 caractères | Refus | ☐ |
| Confirmation différente | Refus | ☐ |
| Créer compte valide | Session ouverte, tableau de bord affiché | ☑ |
| Réutiliser le même identifiant (casse ignorée) | Doublon refusé | ☐ |
| Réutiliser la même adresse e-mail | Doublon refusé | ☐ |
| Connexion avec identifiant valide | Connexion acceptée | ☑ |
| Connexion avec e-mail valide | Connexion acceptée | ☐ |
| Connexion avec mauvais mot de passe | Refus sans préciser quel champ est faux | ☑ |
| Actualiser après connexion | Session locale toujours active | ☑ |
| Effacer la session et ouvrir l'application | Retour à la connexion | ☑ |
| Se déconnecter | Retour à la connexion, session effacée | ☑ |
| Vérifier les 3 images et textes alternatifs | Images locales distinctes, alternatives présentes | ☑ |
| Vérifier banque et niveaux | 30 questions distinctes par niveau | ☑ contrôle statique |
| Entraînement | Correction et explication après validation | ☑ |
| Examen | Aucune réponse révélée avant la fin | ☑ |
| Défi chronométré | Compte à rebours; fin gérée une seule fois | ◐ chrono visible, session terminée avant zéro; expiration non testée |
| Révision | Questions précédemment manquées proposées | ☑ |
| Questions à réponses multiples | Sélection multiple et correction exacte | ☑ |
| Résultats | Score, pourcentage, réponses et durée cohérents | ☑ |
| Progression après actualisation | Données récupérées pour le profil | ☑ |
| Deux profils locaux distincts | Statistiques séparées logiquement | ☐ |
| Suppression des statistiques, annulation | Données conservées | ☐ |
| Suppression confirmée | Statistiques du profil effacées, compte conservé | ☐ |
| Mise en page mobile 390 × 844 | Pas de débordement horizontal observé | ☑ |
| Publication sur GitHub Pages | Ressources relatives disponibles | ☐ publication réelle non effectuée |
