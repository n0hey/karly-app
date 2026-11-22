# Karly

Web app de location de voitures. Promesse : réserver une voiture doit être aussi simple que commander un trajet. On choisit, on paie, on part.

Statut : phase de conception. Il n'y a pas encore de code d'application dans ce dépôt.

## Ce que Karly doit être

Trois exigences, dans cet ordre quand elles s'opposent :

1. **Sans bug.** Une fonction qui marche à moitié n'est pas livrée.
2. **Facile à comprendre.** Quelqu'un qui ouvre l'app pour la première fois sait quoi faire sans explication.
3. **Utile.** Peu de fonctions, mais chacune sert à louer une voiture.

Références : Uber et Bolt pour la simplicité du parcours, GoMore pour la location. 2EM sert de contre-exemple (voir [docs/benchmark.md](docs/benchmark.md)).

## Décisions prises

- **Plateforme** : une web app responsive, utilisable comme site et installable sur Android, iPhone, Mac et Windows. Framework pas encore choisi.
- **Modèle** : voitures proposées par des particuliers et par des professionnels. Certaines réservations sont instantanées, d'autres passent par une demande au propriétaire : l'interface doit toujours dire laquelle.
- **Marque** : mascotte, une petite voiture jaune à visage sur fond bleu nuit (`#FFCB3D` sur `#1B2440`). Deux versions retenues, le choix final entre les deux reste à faire : de face (`assets/logo/karly-de-face.svg`) et de profil (`assets/logo/karly-qui-roule.svg`). Mot-logo « karly » en minuscules arrondies.
- **Style** : très clair, très premium.
- **Design system** : la base « Soleil » sur fond blanc. Boutons jaunes en pilule (le jaune est réservé à l'action), formes rondes, bleu ciel en fond des visuels de voitures. Trois versions nommées dans `docs/design-system/versions.html` : **Équilibre**, **Velours** (plus premium), **Pop** (plus ludique). Le choix entre les trois reste à faire. Les étapes précédentes restent dans `prototype.html` et `ebauches.html`.
- **Mascotte dans l'app** : posée telle quelle sur le blanc, jamais sur la tuile de couleur du logo. Elle sera animée et n'apparaît qu'à des moments prévus : au repos (accueil, profil), endormie (aucune location en cours), réveil (une réservation arrive), appel de phares (rappel), en route (chargement). Pas de mascotte animée pendant le paiement, une saisie ou une erreur. Les animations s'arrêtent si l'utilisateur a demandé moins de mouvement.

Le contexte produit détaillé est dans [PRODUCT.md](PRODUCT.md).

## Décisions ouvertes

Ne pas trancher ces points à la place de l'utilisateur. Poser la question si une tâche en dépend.

- **Version du design system** : Équilibre, Velours ou Pop.
- **Fond du logo** : sur le bleu nuit actuel, les roues ne se voient pas. Cinq pistes dans `docs/design-system/versions.html` (Nuit, Nuit pneus clairs, Indigo, Azur, Ciel).
- **Remise des clés** : en main propre, boîte à clés, ou ouverture par le téléphone (demande du matériel dans les voitures). L'interface doit pouvoir accueillir les trois.
- **Marché** : la Suisse est supposée (francs suisses, TWINT), à confirmer.
- **Tutoiement ou vouvoiement** dans les textes de l'app.

Quand un point est tranché, le déplacer dans « Décisions prises ».

## Périmètre de la première version

- Recherche de voitures par lieu, dates et type de véhicule
- Réservation en quelques étapes, prix total affiché d'avance
- Paiement intégré
- Permis et pièces vérifiés une fois dans le profil
- État des lieux guidé avec photos, au départ et au retour
- Suivi des locations en cours et passées
- Rappels avant la prise en charge et avant le retour

Hors périmètre tant que ce n'est pas demandé : livraison à domicile, tarif à la minute, abonnements, fidélité, comptes entreprise, aller simple, détection automatique des dégâts.

## Règles produit

Elles viennent des reproches les plus fréquents faits aux apps du marché. Elles ne se négocient pas écran par écran.

1. **Le prix affiché avant de confirmer est le prix payé.** Tout y figure : assurance, frais, kilomètres inclus, caution. Aucun frais n'apparaît à la dernière étape ni après la location sans avoir été annoncé avec son montant.
2. **La caution est claire** : montant, moment du blocage, date de libération. Elle est rendue automatiquement, jamais sur demande.
3. **Rien n'est débité avant que la réservation soit confirmée.**
4. **Aucune option pré-cochée.**
5. **On peut explorer sans compte.** Les documents ne sont demandés qu'au moment de réserver.
6. **L'identité se vérifie avant le jour J**, jamais devant la voiture. Le statut et le délai sont affichés.
7. **Les photos d'état des lieux sont horodatées et consultables par le client.**
8. **L'aide s'ouvre depuis la location concernée** et mène à un humain.
9. **Tout ce que fait le site, l'app le fait**, au même prix.

## Règles d'interface

1. Une action principale par écran.
2. L'écran dit toujours où on en est et quelle est la prochaine étape.
3. Chaque écran a ses quatre états : chargement, vide, erreur, hors ligne. Un écran sans ces états n'est pas terminé.
4. Une erreur conserve ce que l'utilisateur a saisi, dit ce qui s'est passé en une phrase et propose une issue. Jamais de message technique brut.
5. Les fonctions critiques marchent sans réseau : photos d'état des lieux, consultation de la réservation en cours.
6. Les filtres et la saisie survivent à un retour en arrière et à une mise en veille.
7. Aucune couleur, taille de texte ou espacement écrit en dur : tout passe par les jetons du design system (définis dans `docs/design-system/versions.html`, encore en cours d'affinage).

## Textes de l'app

- En français. Phrases courtes, mots courants, pas de jargon de loueur (« franchise » s'explique la première fois).
- Boutons : un verbe et son objet, par exemple « Réserver cette voiture ».
- Montants en francs suisses avec la devise, par exemple « CHF 84.50 ».
- Pas de point d'exclamation, pas de « avec succès ».

## Qualité

- Chaque parcours (recherche, réservation, paiement, état des lieux) a des tests automatisés avant d'être considéré comme fini.
- Avant de dire qu'un changement d'interface marche, le lancer et le vérifier à l'écran, y compris un cas d'erreur.
- Dire clairement ce qui n'a pas été vérifié.
- Préférer supprimer une fonction fragile plutôt que la livrer.

## Dépôt

| Chemin | Contenu |
|---|---|
| `README.md` | Présentation publique du projet |
| `docs/` | Cadrage, décisions, benchmark |
| `PRODUCT.md` | Contexte produit (utilisateurs, positionnement, engagements de marque) |
| `docs/design-system/` | Ébauches du design system |
| `assets/logo/` | Mascottes retenues et pistes de logo écartées, en SVG |

Documentation, messages de commit et textes de l'app sont en français.
