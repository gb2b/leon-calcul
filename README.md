# Caisse — Léon en Rue Libre

Petite caisse web pour le stand du festival : on touche les articles du menu, on ajuste
les quantités, le total s'affiche en grand, puis un écran d'encaissement calcule la
monnaie à rendre — en billets et en pièces.

## Ce que ça fait

- Deux postes de caisse : au premier lancement on choisit « resto », « bar » ou
  « les deux », et le menu n'affiche que ce qui se vend à ce poste. La pastille de
  l'en-tête indique le poste courant et permet d'en changer en deux appuis.
  Resto : plancha, frites, dessert. Bar : tapas, boissons, consignes.
- Gestion du stock : un article marqué épuisé reste affiché, barré, et ne peut plus
  être ajouté ; s'il était dans la commande en cours, il en est retiré.
- Catégorie « Consigne » : verre 1 € et pichet 5 €. Au poste bar elle passe en tête du
  menu. Trois façons de la gérer, réglables en cours de soirée :
  **Automatique** (par défaut) — chaque boisson ajoutée pose son verre consigné, et
  chaque pichet sa consigne ; retirer la boisson retire le verre.
  **Proposée** — une fenêtre s'ouvre au moment de voir la commande, avec un verre par
  boisson déjà compté, ajustable.
  **À la demande** — la même fenêtre s'ouvre à zéro : il faut ajouter volontairement.
- Menu complet (plancha, tapas & dessert, consigne, bières, vins & sangria, sans
  alcool), une icône et une couleur par catégorie, en clair comme en sombre.
- Les boissons à 1 € (Coca, Oasis, ice tea, eau pétillante, sirop) sont regroupées
  sous un seul bouton « Soft » ; café, ginger beer et eau 1,5 L restent séparés.
- Affichage de tout le menu d'un coup (par défaut) ou filtré par catégorie.
- Ajout par simple appui ; un bouton « − » apparaît sur la carte pour retirer un article
  sans passer par le récapitulatif.
- Récapitulatif : total figé en haut, articles au milieu, actions figées en bas.
- Écran d'encaissement séparé, en espèces ou par carte bleue. En espèces, on appuie sur
  les billets et les pièces que le client donne (1 € à 100 €, aux couleurs réelles des
  coupures), le montant s'additionne et « à rendre » s'affiche avec le détail des
  coupures ; un champ libre accepte n'importe quel montant. En carte, le clavier
  disparaît : montant exact, rien à rendre.
- Le moyen de paiement par défaut se règle dans les réglages : espèces, carte, ou
  « carte seulement » pour un poste sans monnaie — la bascule disparaît alors.
- Le bilan et le texte partagé séparent la recette en espèces et la recette par carte,
  et l'historique marque « CB » les commandes payées par carte.
- Confirmation après validation, avec la monnaie à rendre en gros et un bouton pour
  annuler tout de suite l'encaissement en cas d'erreur.
- Bilan de la journée : nombre de commandes, recette, détail par article, partage du
  bilan (partage natif, presse-papiers ou texte à copier).
- Historique des commandes encaissées : chacune peut être annulée ou reprise pour
  modification.
- Rappel « commande oubliée » après un délai réglable au curseur : jamais, 30 s, 1 min,
  1 min 30, 2 min, 5 min ou 10 min.
- Éditeur de menu dans les réglages : changer un prix, un nom, une description ou une
  icône, déplacer un article de catégorie, en ajouter, en supprimer, et rétablir le menu
  d'origine. Le menu modifié est enregistré sur l'appareil ; les commandes déjà
  encaissées gardent leurs montants même si l'article disparaît.
- Réglages à part : taille du texte (5 paliers), thème auto/clair/sombre, poste de caisse,
  affichage du menu, retour tactile, paiement par défaut, consigne, rappel de commande
  oubliée. Le menu, le stock et le bilan ont chacun leur page, pour garder les réglages
  lisibles.
- Tout est calculé sur l'appareil ; la commande en cours, l'historique et les réglages
  survivent à un rechargement.

## Utiliser hors ligne

**Option 1 — le fichier seul.** Envoyez `index.html` sur le téléphone et ouvrez-le.
Il est autonome ; sans réseau, les polices Google sont remplacées par celles du système.

**Option 2 — application installée.** Publiez le dossier sur un hébergement HTTPS
(GitHub Pages : *Settings → Pages → Deploy from a branch*). Le service worker met
l'application en cache dès la première visite.

- Android / Chrome : menu ⋮ → « Installer l'application ».
- iPhone : **aucun navigateur ne propose de bouton d'installation** — cela passe
  toujours par le menu Partager. Dans Safari : Partager → « Sur l'écran d'accueil »
  (mode plein écran). Dans Chrome iOS : ⋯ → « Ajouter à l'écran d'accueil », qui crée
  un raccourci ouvert par Safari.

Réglages → « Installer sur l'écran d'accueil » détecte l'appareil, donne les étapes et
affiche un diagnostic : version de l'application, navigateur, adresse, https, manifeste,
service worker, vibration.

**Mises à jour.** L'application installée cherche une nouvelle version à l'ouverture et
quand elle revient au premier plan (au plus une fois toutes les cinq minutes). Quand une
version est prête, une fenêtre la propose : « Plus tard » ne change rien, « Mettre à jour »
l'active et recharge. Rien ne se recharge sans accord, et la commande en cours comme le
bilan de la journée sont conservés. Un bouton « Rechercher une mise à jour » permet de
forcer la vérification.


**Vibration :** `navigator.vibrate` n'existe sur aucun navigateur iPhone. Le réglage se
désactive tout seul et l'indique quand l'appareil ne la prend pas en charge.

## Fichiers

| Fichier | Rôle |
| --- | --- |
| `index.html` | L'application complète (HTML, CSS, JS, icônes SVG) |
| `sw.js` | Service worker : mise en cache pour le hors-ligne |
| `manifest.webmanifest` | Nom, couleurs et icônes de l'application installée |
| `icon-192.png`, `icon-512.png` | Icônes de l'écran d'accueil |

## Prix

Repris du menu du festival : chipolatas-frites 8 €, poulet mariné-frites 9 €, frites 4 €,
assiette tapas 8 €, pâtisserie 3 €, bière pression 3 €, pichet 12 €, bière bio 5 €,
punch 4 €, sangria 4 € / 10 €, vin 3 € / 12 €, champagne 6 € / 35 €, ginger beer 2 €,
eau 1,5 L 2 €, sodas et café 1 €.

Les sauces (mayonnaise, ketchup) sont offertes « à la demande » sur le menu : elles ne
figurent donc pas dans la caisse. Tous les prix étant des euros entiers, le clavier
d'encaissement ne propose pas de centimes ; le champ libre accepte n'importe quel montant.

Pour changer un prix ou un libellé, passez par Réglages → « Modifier le menu ». Le
tableau `DEFAULT_MENU` en haut du `<script>` reste la base rétablie par le bouton
« Rétablir le menu d'origine ».
