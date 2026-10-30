# Dar El Halwa — Pâtisserie fine tunisienne

- **Projet** : site Dar El Halwa (Sfax)
- **Étudiant(e)** : NOM Prénom
- **Classe** : TI1 — Semestre 1 — ECUEF142

## Structure
```
dar-el-halwa/
├── index.html  carte.html  commande.html
├── css/style.css      (feuille unique, charte en variables, mobile-first)
├── images/  medias/  js/
└── REPONSES.md        (réponses aux questions des TP1 à TP5)
```
Ressources à copier à la main (fournies par l'enseignante dans `ressources-tp2.zip`) :
`images/patisserie.jpg`, `medias/temoignage.mp4`, `medias/avis-clients.mp3`.

## Fiche de correctifs
| # | TP | Symptôme | Cause identifiée | Correction |
|---|----|----------|------------------|------------|
| 1 | TP3 | Cliquer sur l'étiquette ne place pas le curseur dans le champ | `for` de `<label>` reprenait le `name` au lieu de l'`id` | `for` = `id` du champ |
| 2 | TP3 | `maxlength="4"` sans effet sur le code postal | Attribut ignoré sur `type="number"` | `type="text"` + `inputmode="numeric"` + `pattern="[0-9]{4}"` |
| 3 | TP4 | Liens du nav en miel au lieu de chocolat | `a:link` (0,1,1) plus spécifique que `nav a` (0,0,2) | Règle `nav a:link, nav a:visited` |
| 4 | TP5 | Cartes qui débordent de la grille | `width: 400px` posé sur `.carte` | Propriété retirée : c'est la piste de grille qui fixe la largeur |
| 5 | TP5 | Défilement horizontal à 360 px (tableau, `.carte-info`) | Largeur fixe de 400 px, tableau trop large | `max-width: 400px` et conteneur `.table-defilant { overflow-x: auto }` |

> À adapter avec ce que **vous** avez réellement observé pendant les séances.
