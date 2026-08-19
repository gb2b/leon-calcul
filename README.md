# Caisse — Léon en Rue Libre

Petite caisse web pour le stand du festival : on touche les articles du menu, on ajuste
les quantités, le total s'affiche en grand et l'application calcule la monnaie à rendre.

- Menu complet (plancha, tapas & dessert, bières, vins & sangria, sans alcool) avec une
  icône et une couleur propres à chaque catégorie, reprises jusque dans le récapitulatif.
- Filtre par catégorie ou affichage de tout le menu d'un coup.
- Récapitulatif de commande et total en gros.
- Encaissement : on appuie sur les pièces (0,10 à 2 €) et les billets (5 à 100 €)
  reçus, autant de fois que nécessaire — les montants s'additionnent (comptés en
  centimes, sans erreur d'arrondi) — ou on saisit un montant libre ; « à rendre »
  s'affiche en jaune, « manque X € » si le compte n'y est pas.
- Total de la journée (nombre de commandes + recette).
- Rappel « commande oubliée » : sans aucun appui pendant 5 minutes (réglable, ou
  désactivable), la caisse demande s'il faut remettre la commande en cours à zéro.
- Thème clair / sombre / auto et 5 tailles de police, dans le menu Réglages.
- Tout est calculé sur l'appareil : aucune donnée n'est envoyée, la commande en cours
  et les réglages survivent à un rechargement.

## Utiliser hors ligne

**Option 1 — le fichier seul.** Envoyez `index.html` sur le téléphone (mail, AirDrop,
clé USB) et ouvrez-le. Il n'a besoin de rien d'autre ; sans réseau, les polices Google
sont simplement remplacées par celles du téléphone.

**Option 2 — application installée (recommandée).** Publiez le dossier sur un hébergement
HTTPS — par exemple GitHub Pages : *Settings → Pages → Deploy from a branch*, branche
`main`, dossier `/ (root)`. Ouvrez ensuite l'adresse sur le téléphone :

- Android / Chrome : menu ⋮ → « Installer l'application » (ou le bouton dans Réglages).
- iPhone / Safari : bouton Partager → « Sur l'écran d'accueil ».

Le service worker (`sw.js`) met l'application en cache : une fois installée, elle
démarre et fonctionne entièrement sans réseau.

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
figurent donc pas dans la caisse. Pour changer un prix ou un libellé, modifiez le tableau
`MENU` en haut du `<script>` dans `index.html`.
