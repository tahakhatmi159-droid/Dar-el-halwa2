# Réponses aux questions — TP1 à TP5

## TP1
**Q1 (charset).** Sans `<meta charset="UTF-8">`, le navigateur doit deviner l'encodage : les accents peuvent s'afficher « Ã© » au lieu de « é ». Même si l'affichage semble correct (le serveur envoie parfois l'encodage en en-tête HTTP), la déclaration reste indispensable car le fichier peut être ouvert hors serveur, copié, ou servi autrement.
**Q2 (git add).** `git add` choisit ce qui entrera dans le prochain instantané (zone d'index). `git commit` n'enregistre que ce qui a été ajouté : on peut ainsi regrouper des modifications cohérentes dans un commit.
**Q3 (nav).** 1) Sens : lecteurs d'écran et moteurs de recherche identifient une zone de navigation, 2) accessibilité/maintenance : navigation par repères au clavier, code plus lisible qu'une `div` anonyme.

## TP2
**Q1 (alt).** Meilleur : « Vitrine garnie de mignardises, cornes de gazelle et makrouds » (décrit le contenu). Ensuite `alt="image"` (inutile mais court), le pire : `alt="patisserie.jpg"` (nom de fichier lu lettre à lettre).
**Q2.** Sans `https://`, `www.facebook.com/...` est un chemin relatif : il est résolu par rapport à votre site (`http://127.0.0.1:5500/www.facebook.com/darelhalwa`) → 404. Correction : `https://www.facebook.com/darelhalwa`.
**Q3.** `rel="noopener"` empêche la page ouverte d'accéder à `window.opener` (risque de redirection malveillante de l'onglet d'origine, « tabnabbing »).
**Q4.** Non, ce n'est pas une erreur : les bordures sont de la présentation, donc du CSS. À faire au TP4 (étape 6), `border-collapse` et `border` sur `th, td`.
**Q5.** Chrome ne lit pas `.wmv` (format propriétaire Microsoft). Formats sûrs : MP4 (H.264 + AAC) et WebM ; audio : MP3, OGG, AAC.

## TP3
**Q1.** Le navigateur envoie la requête POST vers `traitement.php`. Fichier inexistant → erreur 404 (ou « Cannot POST /traitement.php » avec Live Server).
**Q2.** GET place les données dans l'URL (visibles, limitées, mises en favori) ; POST les place dans le corps de la requête. Avec GET, elles apparaissent dans l'URL.
**Q3.** `maxlength` ne s'applique pas à `type="number"`. Pour un code postal : `type="text"` avec `inputmode="numeric"`, `pattern="[0-9]{4}"`, `minlength="4"` et `maxlength="4"`.
**Q4.** Avec quatre `name` différents, les boutons ne sont plus exclusifs : on peut tous les cocher. Le groupe est constitué par le `name` commun.
**Q5.** Oui : `required` sur un seul bouton rend le groupe obligatoire (un choix doit exister parmi les boutons de même `name`).
**Q6.** La valeur de l'attribut `value` de l'option (ex. `sfax`), pas le texte affiché ; sans `value`, c'est le texte qui est envoyé.
**Q7.** `formnovalidate` envoie le formulaire sans validation. Utile pour un bouton « Enregistrer le brouillon ».
**Q8.** 1) Le placeholder disparaît dès la saisie (on oublie ce qu'il fallait écrire), 2) lecteurs d'écran/zone cliquable : pas d'étiquette associée ; aussi contraste faible.
**Q9.** La validation native est côté client, donc contournable : le serveur doit toujours revalider.

## TP4
**Q1.** Le style en ligne l'emporte (spécificité la plus haute). Sans lui, interne et externe ont la même spécificité : le dernier déclaré gagne. Oui, inverser `<link>` et `<style>` change le résultat.
**Q2.** En ligne : modifier chaque titre dans les 3 pages (de nombreux endroits) ; interne : 3 fichiers ; externe : 1 fichier. Autres conséquences : code dupliqué et lourd, pas de cache de la feuille, mélange structure/présentation.
**Q3.** Une ligne modifiée, tous les endroits utilisant `var(--miel)` changent.
**Q4.** `p` = (0,0,1) ; `main p` = (0,0,2) ; `.mise-en-avant` = (0,1,0). Le rouge gagne : on compare colonne par colonne de gauche à droite, pas par addition (onze éléments ne valent pas une classe).
**Q5.** `!important` casse la cascade (guerre d'escalade), rend le code impossible à maintenir ; il écrase aussi les réglages d'accessibilité de l'utilisateur.
**Q6.** 400 + 2×20 (padding) + 2×2 (bordure) = **444 px** (+ 60 px de marges extérieures).
**Q7.** 400 px au total. C'est le **contenu** qui est rogné (356 px). Cette règle est en tête car elle rend les calculs prévisibles pour toute la feuille.
**Blancs :** `thead { background-color: #f3e2bf; color: var(--chocolat); }` · `th, td { border: 1px solid #bbb; padding: 8px; }` · `tbody tr td:last-child { text-align: right; }` · `tbody tr:nth-child(even) { ... }` · `a:visited { color: var(--pistache); } a:hover { color: var(--chocolat); text-decoration: underline; } a:active { color: var(--chocolat); }`

## TP5
**Q1.**
| Zone | 1D/2D | Technique | Pourquoi |
|---|---|---|---|
| Barre de navigation | 1D | Flexbox | liens alignés sur une ligne |
| Galerie de 4 cartes | 2D | Grid | lignes et colonnes |
| Pied de page 3 colonnes | 1D | Flexbox | blocs répartis sur un axe |
| Gabarit général | 2D | Grid | zones nommées en plan |

**Q2.** `space-between` : aucun espace aux extrémités. `space-around` : demi-espace aux extrémités (moitié de l'espace entre éléments). `space-evenly` : espaces strictement égaux, extrémités comprises.
**Q3.** `flex-wrap` fait passer les liens à la ligne suivante. En positionnement absolu avec largeurs en px : chevauchements, débordement, barre de défilement horizontale.
**Q4.** `flex: 1` = `flex: 1 1 0%` (grow 1, shrink 1, basis 0%). C'est `flex-basis: 0` qui garantit l'égalité stricte (sinon la taille du contenu s'ajoute avant le partage).
**Q5.** `align-items` vaut par défaut `normal`, qui se comporte comme `stretch` : chaque carte s'étire sur toute la hauteur de la ligne.
**Q6.** Grid place les cartes dans le plan ; Flexbox organise l'intérieur de chaque carte (colonne, prix poussé en bas).
**Q7.** En mobile-first, la base = mobile et chaque `min-width` ajoute des règles. Mélanger `max-width` crée des intervalles qui se chevauchent, des règles à annuler, des conflits de cascade : la feuille devient illisible.
**Q8.** Sans viewport, le mobile affiche la page dans une fenêtre virtuelle (~980 px) réduite : texte minuscule, media queries 360 px inefficaces. La balise `width=device-width, initial-scale=1` aligne la largeur de mise en page sur celle de l'écran.

**Panne `.carte { width: 400px }`** : la carte déborde de sa piste, car c'est la piste qui dicte la largeur ; propriété fautive : `width` (à retirer).

**Bonus.** `repeat(auto-fit, minmax(220px, 1fr))` : le nombre de colonnes s'adapte tout seul à la largeur, sans media query. Version Flexbox : il faut en plus `flex-wrap: wrap` et `flex: 1 1 220px` ; la dernière ligne s'étire de façon irrégulière car Flexbox gère chaque ligne indépendamment.
