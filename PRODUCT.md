# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Web app responsive, utilisable comme site et installable sur Android, iPhone, Mac et Windows (application web progressive). Framework pas encore choisi.

## Users

Une personne qui a besoin d'une voiture pour quelques heures ou quelques jours : un week-end, un déménagement, un rendez-vous hors des transports publics. Elle n'a pas de voiture ou pas la bonne. Elle cherche depuis son téléphone, souvent peu de temps avant, et veut savoir tout de suite combien ça coûte au total et comment récupérer la voiture.

Deuxième public : les personnes qui mettent des voitures à disposition, particuliers comme professionnels (garages, loueurs).

## Product Purpose

Trouver, réserver et récupérer une voiture en quelques minutes, sans paperasse. Réserver une voiture doit être aussi simple que commander un trajet : on choisit, on paie, on part.

Succès : une première location menée de bout en bout sans aide, sans frais inattendus et sans bug.

## Positioning

Une location claire et fiable là où le marché déçoit : le prix affiché avant de confirmer est le prix payé, la caution revient seule, l'identité se vérifie avant le jour J, l'aide part de la location concernée. Les acteurs en place sont critiqués précisément sur ces points (voir `docs/benchmark.md`).

## Operating Context

- Réservation surtout sur téléphone, souvent en mobilité ; consultation aussi sur ordinateur.
- Prise et retour de la voiture dans la rue ou en parking souterrain, parfois sans réseau, d'une main, en plein soleil ou de nuit.
- État des lieux photo au départ et au retour.
- Marché supposé : la Suisse (francs suisses, TWINT). À confirmer.

## Capabilities and Constraints

Première version : recherche par lieu, dates et type de véhicule ; réservation en quelques étapes avec prix total d'avance ; paiement intégré ; permis et pièces vérifiés une fois dans le profil ; état des lieux guidé avec photos ; suivi des locations en cours et passées ; rappels avant la prise en charge et le retour.

Modèle : voitures proposées par des particuliers et par des professionnels. Certaines réservations peuvent donc être instantanées, d'autres passer par une demande au propriétaire.

Pas encore décidé : le mode de remise des clés (ouverture par téléphone, en main propre, boîte à clés). L'interface doit pouvoir accueillir les trois.

Hors périmètre de la première version : livraison à domicile, tarif à la minute, abonnements, fidélité, comptes entreprise, aller simple, détection automatique des dégâts.

## Brand Commitments

- Nom : Karly. Promesse : « La location de voiture, simplement. »
- Mascotte : une petite voiture jaune à visage, sur fond bleu nuit. Version de profil « qui roule » probablement retenue comme logo ; version de face gardée en réserve (`assets/logo/tour-2/`).
- Mot-logo « karly » en minuscules, lettres monolignes arrondies dessinées sur mesure (`assets/logo/`).
- Textes en français, phrases courtes, tutoiement non décidé.

## Evidence on Hand

- Benchmark du marché : `docs/benchmark.md`.
- Pistes de logo : `assets/logo/`.
- Aucun client, avis, chiffre ou partenaire réel à ce jour : ne pas en inventer.

## Product Principles

1. Sans bug d'abord : une fonction qui marche à moitié n'est pas livrée.
2. Rien de caché : chaque franc est annoncé avant de payer.
3. Une étape, une décision : une action principale par écran.
4. Toujours dire où on en est et ce qui vient ensuite.
5. Prévoir le mauvais moment : sans réseau, au parking, pressé.

## Accessibility & Inclusion

Niveau visé : WCAG 2.2 AA. Utilisable d'une main sur téléphone, lisible en plein soleil, respecte la taille de texte choisie par l'utilisateur et la réduction des animations.
