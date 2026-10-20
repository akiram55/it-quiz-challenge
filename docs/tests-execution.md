# Journal des vérifications réellement exécutées

**Environnement :** Chromium via `playwright-cli`, application servie en local sur `http://127.0.0.1:8000`, le 20 octobre 2026. Profil de démonstration temporaire `alice`; aucun vrai compte ni secret réutilisé. Les chiffres ci-dessous sont le résultat d'une session de test, non des performances de référence.

## Contrôles exécutés

- Ouverture de l'application sans session : l'écran de connexion est affiché en premier.
- Création d'un compte valide (`alice`, adresse de démonstration) et accès au tableau de bord. La page a démontré l'utilisation de PBKDF2 côté navigateur.
- Affichage des trois cartes d'apprentissage, chacune avec image et texte alternatif; les trois images ont été chargées dans le navigateur (`naturalWidth` non nul).
- Mode entraînement : question à réponses multiples, sélection clavier + souris, correction expliquée affichée. Une session de 10 questions a été terminée; résultat observé : 8 réponses exactes, 9/11 points, 82 %.
- Mode examen : session de 10 questions terminée. Avant la dernière question, aucune explication n'était visible; les réponses et explications apparaissaient sur l'écran de résultat.
- Mode défi : le compte à rebours était visible; session de 10 questions terminée avant la fin du délai. Le test de déclenchement réel à zéro n'a pas été exécuté.
- Mode révision : une question précédemment ratée a été sélectionnée et son explication affichée. Le premier essai a révélé un défaut d'affichage de correction en révision; le rendu a été corrigé puis retesté avec succès.
- Actualisation de la page après enregistrement de tentatives : la session restait active et le tableau de bord affichait 3 tentatives ainsi que les scores par niveau.
- Déconnexion depuis l'en-tête : retour à la page de connexion. Une connexion avec mot de passe erroné a affiché le message générique de refus; une connexion correcte a ensuite rouvert le tableau de bord.
- Contrôle responsive à 390 × 844 CSS pixels : la largeur de document observée était de 390 pixels (pas de débordement horizontal dans cet affichage).
- Contrôle statique JavaScript : 90 questions, exactement 30 par niveau; propriétés requises présentes sur les entrées.

Les deux captures d'interface fournies sont `captures/tableau-de-bord.png` et `captures/quiz.png` et ont été produites depuis la session navigateur décrite. Le profil peut contenir des données d'essai si quelqu'un réutilise le même stockage local; le ZIP ne contient aucun profil ou stockage navigateur.

## Contrôles restant à effectuer

- Parcours complet de création avec chaque champ invalide, e-mail mal formé, confirmation divergente, doublons identifiant/e-mail et longueur de mot de passe insuffisante.
- Connexion par e-mail valide (la connexion par identifiant a été exécutée).
- Test de l'expiration du chronomètre à zéro et de l'absence de double comptabilisation à cette frontière.
- Vérification séparée avec plusieurs profils, confirmation/annulation de suppression des statistiques, et maintien du compte après suppression.
- Recette exhaustive des domaines/niveaux, tests d'accessibilité clavier/lecteur d'écran et autres navigateurs.
- Publication réelle sur GitHub Pages et contrôle depuis son URL.

Aucun test n'est présenté comme réussi lorsqu'il n'a pas été exécuté. La checklist vierge reste disponible dans `../tests/checklist-tests.md` pour une recette manuelle ultérieure.
