# Plan de l'application

Version du 22 novembre 2026. Ce document décrit à quoi ressemble Karly, écran par écran, et dans quel ordre on la développe. Il s'appuie sur [benchmark.md](benchmark.md) (partie « Parcours détaillés ») et sur la structure de GoMore, retenue comme modèle de simplicité.

L'objectif est une application complète : locataires et propriétaires, sur mobile et sur le web. Le choix entre professionnels et particuliers au lancement sera fait plus tard ; ce plan fonctionne pour les deux.

## 1. Navigation

### Mobile : quatre onglets en bas

| Onglet | Ce qu'on y fait |
|---|---|
| **Rechercher** | L'accueil. Les voitures les plus proches tout de suite, et la recherche. |
| **Locations** | Les locations en cours, à venir et passées, avec tout ce qu'il faut savoir. |
| **Messages** | Échanger entre locataire et propriétaire, à propos d'une location. |
| **Ajouter** | Mettre sa voiture en location pour gagner de l'argent, puis la gérer. |

**Le profil n'est pas un onglet.** On l'ouvre par la pastille (photo ou initiales) en haut à droite de l'écran Rechercher.

### Web : les mêmes pages, en haut de l'écran

- **À gauche** : le menu ☰ (comme sur Amazon), puis le nom « karly » écrit, puis les onglets en toutes lettres : Rechercher, Locations, Messages.
- **À droite** : le bouton « Louer ma voiture », qui correspond à l'onglet Ajouter, puis la pastille du profil.
- **Le menu ☰** ouvre un panneau latéral avec tout :
  - Rechercher, Locations, Messages ;
  - Louer ma voiture, Mes voitures ;
  - Profil ;
  - Comment ça marche, Aide.
- **Sur un téléphone, le site** reprend la barre d'onglets du bas. Une seule logique, deux tailles d'écran.

Les pages sont les mêmes sur mobile et sur le web, avec les mêmes prix et les mêmes fonctions (règle produit 9).

## 2. Les écrans, onglet par onglet

Tous les écrans ont leurs quatre états : chargement, vide, erreur, hors ligne. Seuls les cas particuliers sont décrits.

### 2.1 Rechercher

**R1. Accueil**
- **En haut, la barre de recherche**, compacte : « Où et quand ? ». Le lieu (« Autour de moi » par défaut) et les dates, avec des dates par défaut : aujourd'hui dans 2 heures, retour le lendemain à la même heure.
- **Juste en dessous, les voitures les plus proches**, sans rien avoir à saisir. On a tout de suite des propositions sous les yeux.
- Chaque carte de voiture montre :
  - la photo, le modèle et l'année ;
  - la distance et la note ;
  - le **prix total** pour les dates affichées ;
  - un badge « Réservation immédiate » ou « Sur demande ».
- Si l'utilisateur refuse la localisation : on lui demande sa ville, et on ne le bloque pas.
- Une location en cours ou à venir apparaît en tête, sous forme de bandeau qui mène à l'onglet Locations.
- Pastille du profil en haut à droite.

**R2. Recherche.** Lieu avec suggestions, dates et heures par pas de 30 minutes, durée affichée.

**R3. Résultats**
- Liste par défaut, avec un bouton « Voir sur la carte » (comme GoMore).
- Filtres rapides en pastilles :
  - réservation immédiate ;
  - type de voiture ;
  - boîte automatique ;
  - tri par prix ou par distance.
- Le bouton « Filtres » ouvre les autres critères : places, énergie, pneus neige et chaînes, vignette, attelage, siège enfant, animaux, sortie à l'étranger.
- Les filtres survivent au retour en arrière et à la mise en veille.
- **Aucun résultat** : on propose d'élargir la zone ou de décaler les dates.

**R4. Fiche voiture**, dans cet ordre :
1. Les photos.
2. Le modèle, la note, le **prix total** pour ces dates. Les dates se modifient sur place.
3. Immédiat ou sur demande. Sur demande : « Réponse sous X h. Rien n'est débité avant. »
4. **Ce qui est compris** :
   - l'assurance, l'assureur et la franchise en CHF, avec une ligne qui explique ce qu'est une franchise ;
   - les kilomètres inclus et le prix du kilomètre en plus ;
   - la caution : son montant et quand elle est rendue ;
   - l'assistance 24 h/24.
5. Où récupérer la voiture : le quartier et le mode de remise des clés. L'adresse exacte est donnée après la confirmation.
6. Le propriétaire : identité vérifiée, délai de réponse, nombre de locations, mention « Professionnel » le cas échéant.
7. Les avis.
8. Les règles : âge minimum, animaux, carburant au retour, sortie à l'étranger.
9. Les conditions d'annulation, en clair.

Le bouton reste fixé en bas avec le total : « Réserver cette voiture » ou « Demander cette voiture ». Un lien plus discret, « Poser une question », ouvre une conversation.

### 2.2 Réserver (depuis la fiche voiture)

Quatre étapes au plus, avec la progression affichée. Les étapes déjà faites sont sautées. Ce qui a été saisi est conservé en cas d'erreur.

**B1. Options**
- Les niveaux de protection, chacun avec sa franchise en CHF et son prix. **Aucun n'est coché d'avance.**
- Le conducteur supplémentaire et les kilomètres en plus.
- Le total se met à jour à chaque choix.

**B2. Compte et vérification** (seulement la première fois)
- Création du compte : Apple, Google ou e-mail.
- Photo du permis et selfie.
- Le statut et le délai de vérification sont affichés.
- Si la vérification échoue : la raison en une phrase et un contact humain.

**B3. Paiement.** TWINT, carte, Apple Pay ou Google Pay. Le moyen choisi est enregistré.

**B4. Récapitulatif**
- Chaque ligne du prix, puis le **total payé**.
- La caution à part : son montant, quand elle est bloquée, quand elle est rendue.
- Les kilomètres inclus, les règles d'annulation, le lieu et l'heure.
- Le bouton : « Payer CHF 184.50 » pour une réservation immédiate, ou « Envoyer la demande » sur demande (« Rien n'est débité avant l'accord du propriétaire »).

**B5. Confirmation**
- Où on en est et ce qui vient ensuite.
- Pour une demande : un compte à rebours. Si le propriétaire ne répond pas à temps, la demande est annulée automatiquement, sans frais, et des voitures proches sont proposées.

### 2.3 Locations

**L1. Liste**
- En haut à droite : le bouton **« + Nouvelle location »**, qui ouvre la recherche.
- Trois sections : En cours, À venir, Passées. Les demandes en attente sont dans À venir, avec leur compte à rebours.
- Un propriétaire voit un sélecteur « Je loue / Ma voiture » pour retrouver aussi les locations de ses voitures.
- Liste vide : « Aucune location pour l'instant », avec le bouton « Trouver une voiture ».

**L2. Carte d'une location en cours** (visible directement dans la liste, et en détail au toucher)
- Voiture, propriétaire, **heure de retour** avec un compte à rebours.
- **Tarif payé** et son statut : réglé, en attente, remboursé.
- **Kilomètres** : autorisés, effectués (relevés à l'état des lieux de départ, puis au retour), prix du kilomètre en plus.
- **Carburant ou batterie** : le niveau au départ et le niveau attendu au retour.
- **Lieu de prise en charge** et **lieu de retour**, avec un lien vers le GPS.
- **Caution** : le montant bloqué et la date de libération.
- Un bouton principal qui change selon le moment : « Commencer l'état des lieux », « Ouvrir la voiture », « Rendre la voiture ».
- Des actions secondaires : Envoyer un message, Obtenir de l'aide, Prolonger, Annuler (le montant remboursé est affiché avant de confirmer).
- Les photos d'état des lieux, avec leur date et leur heure.
- **Consultable sans réseau** : la location en cours et la suivante sont enregistrées sur le téléphone.

**L3. Le jour J** (depuis la carte de la location)
1. **Prise en charge** : le lieu exact sur une carte, les instructions et une photo de l'emplacement si le propriétaire en a mis une.
2. **État des lieux de départ** :
   - 8 photos guidées, avec un cadre à l'écran ;
   - puis le compteur et le carburant ;
   - une note libre pour signaler un dégât déjà présent.
   - **Il fonctionne sans réseau** : les photos sont datées sur le téléphone et envoyées dès que le réseau revient.
3. **Les clés** : en main propre, code d'une boîte à clés ou ouverture par le téléphone, selon le mode choisi. Un lien « Ça ne marche pas » mène toujours à l'aide.
4. **Pendant la location** : un bouton « Accident ou panne » bien visible, avec le numéro d'assistance.
5. **État des lieux de retour** : les mêmes 8 angles, le compteur et le carburant.
6. **Fin** :
   - les kilomètres parcourus et le montant final ;
   - un supplément seulement selon le barème annoncé sur la fiche ;
   - la date de libération de la caution.
7. **Avis** :
   - une note et trois critères ;
   - un texte obligatoire en dessous de 5 étoiles ;
   - les avis restent cachés jusqu'à ce que les deux personnes aient noté, ou 14 jours après.

**L4. Aide** (depuis une location)
- Choix en gros boutons :
  - la voiture ne s'ouvre pas ;
  - je ne la trouve pas ;
  - accident ou panne ;
  - dégât constaté ;
  - je serai en retard ;
  - autre chose.
- Pour chaque choix : une marche à suivre courte, puis un humain (chat, ou téléphone en cas d'urgence).

### 2.4 Messages

**M1. Liste des conversations.** Chacune montre la voiture, les dates et le dernier message. Elles sont triées par location active d'abord.

**M2. Conversation**
- En haut, un lien vers la location.
- Le téléphone du propriétaire n'est visible qu'après la confirmation.
- Un message qui propose de payer hors de Karly déclenche un avertissement : ce paiement n'est pas protégé.

Une conversation s'ouvre aussi depuis la fiche voiture (« Poser une question ») et depuis la carte de la location.

### 2.5 Ajouter (propriétaire)

**A1. Avant la première voiture : présentation, en une page**
- « Gagne de l'argent avec ta voiture », avec une estimation selon le modèle et la ville.
- Les quatre engagements de Karly :
  - assurance incluse ;
  - locataires vérifiés ;
  - photos au départ et au retour comme preuve ;
  - versement à une date connue.
- Le bouton : « Mettre ma voiture en ligne ».

**A2. Mise en ligne.** Des étapes courtes, enregistrées au fur et à mesure pour pouvoir reprendre plus tard :
1. La plaque et le modèle (remplis automatiquement si possible), l'année et le kilométrage.
2. Les photos guidées : extérieur, intérieur, coffre.
3. Le lieu de stationnement et les instructions. L'adresse reste cachée jusqu'à la confirmation.
4. Le mode de remise des clés.
5. Le prix : un prix suggéré, modifiable, avec à côté le gain net.
6. Le mode de réservation (immédiate ou sur demande), le délai de prévenance, la durée minimum et maximum.
7. Les règles : âge minimum, kilomètres inclus, animaux, étranger.
8. La vérification du propriétaire : identité, carte grise, IBAN. Pour une entreprise : raison sociale, numéro IDE, TVA.
9. L'aperçu de l'annonce telle que les locataires la verront, puis « Publier ma voiture ».

**A3. Après la première voiture : l'onglet devient un tableau de bord**, avec quatre sections :
- **Demandes et aujourd'hui** :
  - les demandes à accepter ou refuser, avec un compte à rebours et le profil vérifié du locataire ;
  - les remises et retours du jour.
- **Calendrier** :
  - toutes les voitures sur une même vue ;
  - on y bloque des dates et on change le prix d'un jour.
- **Mes voitures** :
  - le statut de chaque annonce (en ligne, en pause, à compléter) et ses réglages ;
  - un bouton « Ajouter une voiture ».
- **Revenus** :
  - le prochain versement et sa date ;
  - l'historique ;
  - les factures avec TVA pour les professionnels.

Côté propriétaire, une location terminée propose **« Déclarer un frais ou un dégât »** :
- une demande avec photos et montant, selon le barème publié ;
- le locataire a 72 heures pour accepter ou contester ;
- s'il conteste, Karly arbitre.

### 2.6 Profil (pastille en haut à droite)

- Le profil public : photo, prénom, avis.
- Le statut de vérification du permis et de l'identité.
- Les moyens de paiement et les notifications.
- Comment ça marche, l'aide, les conditions.
- Se déconnecter, supprimer mon compte.

### 2.7 Notifications

Chacune ouvre l'écran concerné.

| Moment | Locataire | Propriétaire |
|---|---|---|
| Demande | Acceptée, refusée, expirée | Nouvelle demande, rappel avant expiration |
| Vérification | Validée ou à compléter | Validée ou à compléter |
| Avant | Rappel la veille ; adresse et instructions 30 min avant | Rappel la veille |
| Pendant | Retour dans 1 h | Voiture prise en charge |
| Après | Caution libérée ; avis à donner | Voiture rendue ; versement envoyé ; avis à donner |
| Messages | Nouveau message | Nouveau message |

### 2.8 Outil interne (pour l'équipe Karly, hors app)

C'est la condition pour tenir les promesses de confiance. Il sert à :
- traiter les vérifications d'identité restées en suspens ;
- répondre à l'aide, en ayant la location concernée sous les yeux ;
- arbitrer les frais contestés, avec les photos des deux côtés ;
- rembourser ;
- suspendre une annonce ou un compte.

## 3. Ce qui inspire confiance, et où ça se voit

| Engagement | Écrans |
|---|---|
| Le prix affiché est le prix payé | R1, R3, R4, B4, fin de location |
| Rien n'est débité avant la confirmation | R4, B4, B5 |
| La caution est claire et rendue toute seule | R4, B4, L2, notification |
| L'identité est vérifiée par Karly, avant le jour J | B2, Profil, demandes côté propriétaire |
| L'assurance est nommée, avec la franchise en CHF | R4, B1, A1 |
| Les photos datées sont visibles des deux côtés | L2, L3, déclaration de frais |
| Les avis sont à l'aveugle, dans les deux sens | L3, R4, demandes |
| Un humain répond, depuis la location | L2, L3, L4 |
| Le versement arrive à une date connue | A1, Revenus |

## 4. Plan d'action pour le développement

### 4.1 Technique proposée (à valider)

But : un seul code pour iPhone, Android et le web, afin que les pages soient les mêmes partout et qu'on avance vite.

| Besoin | Proposition | Pourquoi |
|---|---|---|
| App iPhone, Android et site | **Expo (React Native) avec Expo Router** | Un seul code pour les trois. La navigation par onglets en bas sur mobile devient un en-tête en haut sur grand écran. Accès natif à la caméra, au GPS, au Bluetooth et au stockage hors ligne. |
| Comptes, base de données, fichiers, messages en direct | **Supabase** (Postgres) | Connexion Apple, Google et e-mail, stockage des photos, messagerie en temps réel, règles d'accès dans la base. Hébergement possible en Europe. |
| Paiements, caution, versements aux propriétaires | **Stripe** (avec Stripe Connect) | Cartes, Apple Pay, Google Pay et TWINT en Suisse ; caution bloquée sans débit sur carte ; versements vers un IBAN suisse. |
| Vérification d'identité | **Stripe Identity**, ou un spécialiste (Onfido, Veriff) | Permis et selfie, résultat en quelques minutes. |
| Cartes et adresses | Mapbox ou Google Maps | Carte des voitures, suggestions d'adresses. |
| Notifications | Expo Notifications, e-mails par Resend ou Postmark | |
| Tests | Jest pour la logique, Maestro pour les parcours sur mobile, Playwright pour le web | Chaque parcours est testé de bout en bout (règle de qualité). |

**À vérifier avant de démarrer :**
- Stripe peut-il bloquer une caution sans la débiter avec TWINT ? Si ce n'est pas possible, la caution passera par une carte.
- Stripe Identity est-il disponible en Suisse ?

### 4.2 Données principales

- **Utilisateur** : profil, statut de vérification, rôles (locataire, propriétaire, entreprise).
- **Voiture** : fiche, photos, lieu, mode de remise des clés, règles, prix, réglages de réservation.
- **Disponibilité** : jours bloqués, prix d'un jour particulier.
- **Réservation**, qui passe par ces statuts :
  - `demandée` (puis `refusée` ou `expirée`) ;
  - `confirmée` ;
  - `en cours` ;
  - `rendue` ;
  - `clôturée` ;
  - `annulée` à tout moment avant le départ.

  On n'a qu'un seul endroit qui calcule le prix, utilisé par la liste, la fiche, le récapitulatif et la facture. C'est ce qui garantit que le prix affiché est le prix payé.
- **Paiement**, **caution**, **versement**, **frais déclarés**.
- **État des lieux** : départ ou retour, photos avec date, heure et position, kilomètres, carburant.
- **Conversation** et **message**, rattachés à une voiture ou à une réservation.
- **Avis**, dans les deux sens.

### 4.3 Étapes

Chaque étape se termine par quelque chose qui marche de bout en bout, testé, avec ses quatre états. On ne commence pas la suivante avant.

| Étape | Contenu | Terminée quand |
|---|---|---|
| 0. Socle | Projet Expo, navigation à quatre onglets et en-tête web avec menu ☰, jetons de design provisoires (remplacés après le choix du logo), Supabase, comptes, données de test, tests automatiques à chaque modification | On se connecte et on navigue entre les onglets vides, sur iPhone, Android et web |
| 1. Ajouter | Présentation, mise en ligne d'une voiture, Mes voitures, calendrier | Une voiture est publiée avec photos, prix et disponibilités |
| 2. Rechercher | Voitures proches, recherche, filtres, carte, fiche voiture, calcul du prix total | On trouve une voiture et son prix total, sans compte |
| 3. Réserver | Options, compte, vérification d'identité, paiement en mode test, réservation immédiate et sur demande, expiration automatique, demandes côté propriétaire | Une réservation est payée, ou demandée puis acceptée, refusée ou expirée sans débit |
| 4. Locations | Liste, carte de location en cours avec tarifs, kilomètres, carburant et lieux, annulation, prolongation, consultation sans réseau | Le locataire et le propriétaire voient la même location, à jour |
| 5. Jour J | État des lieux hors ligne, remise des clés (en main propre et boîte à clés d'abord), retour, kilomètres et carburant finaux | Une location se fait de bout en bout, y compris dans un parking sans réseau |
| 6. Messages et notifications | Conversations en direct, notifications du tableau 2.7, e-mails | Chaque événement prévient la bonne personne |
| 7. Après la location | Caution libérée automatiquement, versements, avis à l'aveugle, déclaration de frais et contestation, aide depuis la location, outil interne | L'argent arrive où il doit, à la date annoncée, et un litige se règle |
| 8. Finition | Les quatre états partout, accessibilité (WCAG 2.2 AA), textes relus, tests de bout en bout de tous les parcours, paiement réel, bêta fermée | Une première location réelle menée sans aide, sans frais inattendu, sans bug |

L'ouverture de la voiture par le téléphone, si elle est retenue, vient après l'étape 5 : elle dépend d'un boîtier dans les voitures et d'un partenaire.

### 4.4 Reporté après la première version

- Favoris.
- Prix dynamique : seul le prix suggéré est prévu.
- Badges de propriétaire.
- Livraison de la voiture.
- Co-propriétaires d'une annonce.
- Mise en avant payante.

## 5. Points ouverts

Ils ne bloquent pas le début du développement. Chacun bloque une étape précise.

| Point | Bloque | Pourquoi c'est ouvert |
|---|---|---|
| Technique (section 4.1) | Étape 0 | `CLAUDE.md` hésite entre une app iPhone seule et iPhone plus Android. Le plan propose un seul code pour iPhone, Android et web. |
| Assureur partenaire, franchise, niveaux de protection | Étape 3 | |
| Modes de remise des clés | Étape 5 | |
| Délai de réponse imposé aux propriétaires | Étape 3 | |
| Barèmes : annulation, retard, carburant, km en plus, frais de service, commission | Étapes 2 et 3 | |
| Langues : français seul ou aussi allemand | Étape 8 | |
| Tutoiement ou vouvoiement | Étape 8 | La maquette tutoie, pour l'exemple seulement |
| Logo et couleurs | Remplacement des jetons provisoires | |
