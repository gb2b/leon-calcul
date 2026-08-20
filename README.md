# Caisse — Léon en Rue Libre

Petite caisse web pour le stand du festival : on touche les articles du menu, on ajuste
les quantités, le total s'affiche en grand, puis un écran d'encaissement calcule la
monnaie à rendre — en billets et en pièces.

## Ce que ça fait

- Deux postes de caisse : au premier lancement on choisit « plancha », « bar » ou
  « les deux », et le menu n'affiche que ce qui se vend à ce poste (modifiable dans
  les réglages).
- Gestion du stock : un article marqué épuisé reste affiché, barré, et ne peut plus
  être ajouté ; s'il était dans la commande en cours, il en est retiré.
- Catégorie « Consigne » : verre 1 € et pichet 1 €. Au poste bar elle passe en tête du
  menu, et un rappel s'affiche au moment de voir la commande ou d'encaisser si elle
  contient des boissons sans consigne — avec le nombre de verres pré-rempli, ajustable,
  et un bouton « Sans consigne » pour un client qui a déjà le sien. Une seule fois par
  commande.
- Menu complet (plancha, tapas & dessert, consigne, bières, vins & sangria, sans
  alcool), une icône et une couleur par catégorie, en clair comme en sombre.
- Les boissons à 1 € (Coca, Oasis, ice tea, eau pétillante, sirop) sont regroupées
  sous un seul bouton « Soft » ; café, ginger beer et eau 1,5 L restent séparés.
- Affichage de tout le menu d'un coup (par défaut) ou filtré par catégorie.
- Ajout par simple appui ; un bouton « − » apparaît sur la carte pour retirer un article
  sans passer par le récapitulatif.
- Récapitulatif : total figé en haut, articles au milieu, actions figées en bas.
- Écran d'encaissement séparé : on appuie sur les billets et les pièces que le client
  donne (1 € à 100 €, aux couleurs réelles des coupures), le montant s'additionne, et
  « à rendre » s'affiche avec le détail des coupures à rendre. Un champ libre reste
  disponible pour n'importe quel montant.
- Confirmation après validation, avec la monnaie à rendre en gros et un bouton pour
  annuler tout de suite l'encaissement en cas d'erreur.
- Bilan de la journée : nombre de commandes, recette, détail par article, partage du
  bilan (partage natif, presse-papiers ou texte à copier).
- Historique des commandes encaissées : chacune peut être annulée ou reprise pour
  modification.
- Rappel « commande oubliée » après un délai sans appui (réglable, désactivable).
- Éditeur de menu dans les réglages : changer un prix, un nom, une description ou une
  icône, déplacer un article de catégorie, en ajouter, en supprimer, et rétablir le menu
  d'origine. Le menu modifié est enregistré sur l'appareil ; les commandes déjà
  encaissées gardent leurs montants même si l'article disparaît.
- Réglages à part : taille du texte (5 paliers), thème auto/clair/sombre, affichage du
  menu, retour tactile, ouverture des réglages par appui long.
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
affiche un diagnostic : adresse, https, manifeste, service worker, vibration.

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
