# Site de l'association Sorbonne Défense — version 2

Site statique (HTML/CSS/JS, sans outil de compilation), prévu pour GitHub Pages.

## Contenu de l'archive

| Fichier | Rôle |
|---|---|
| `index.html` | Page d'accueil |
| `actualites.html` | Actualités de l'association (distinctes de la RESS) |
| `ress.html` | Revue d'Étude Stratégique de la Sorbonne |
| `a-propos.html` | L'association : objet, activités, historique, bureau, informations administratives |
| `contact.html` | Coordonnées |
| `mentions-legales.html` | Mentions légales (LCEN, RGPD) |
| `assets/style.css` | Feuille de style commune (couleurs, typographie, mise en page) |
| `assets/site.js` | En-tête qui se réduit, menu mobile, apparitions au défilement, filtre des actualités |
| `assets/logo.png` | Logo (sert aussi d'icône d'onglet) |
| `assets/fonts/` | Polices EB Garamond (titres) et Charis SIL (texte), hébergées avec le site |

Aucun cookie, aucun appel à un service tiers : les polices sont servies par le site lui-même.

## Mise en ligne sur GitHub Pages

1. Créer un compte sur github.com (ou utiliser celui de l'association).
2. Créer un dépôt public, par exemple `sorbonne-defense`.
3. Décompresser l'archive, puis déposer **le contenu** du dossier (pas le dossier lui-même) à la racine du dépôt : bouton *Add file* → *Upload files*. `index.html` doit se trouver à la racine.
4. Dans le dépôt : *Settings* → *Pages* → *Build and deployment* → *Source* : « Deploy from a branch », branche `main`, dossier `/ (root)` → *Save*.
5. Après une à deux minutes, le site est accessible à l'adresse `https://<compte>.github.io/sorbonne-defense/`.

### Nom de domaine propre (facultatif)

Pour utiliser par exemple `sorbonne-defense.fr` :

1. acheter le domaine auprès d'un registraire (OVH, Gandi…) ;
2. dans *Settings* → *Pages* → *Custom domain*, saisir le domaine ;
3. chez le registraire, créer les enregistrements DNS indiqués par GitHub (enregistrements A vers les adresses IP de GitHub Pages, ou CNAME vers `<compte>.github.io`) ;
4. cocher *Enforce HTTPS* une fois le certificat émis.

L'adresse `contact@sorbonne-defense.fr` utilisée sur le site est **provisoire** : elle ne fonctionnera qu'une fois le domaine acquis et une messagerie configurée.

## Avant la mise en ligne définitive

Les éléments manquants sont surlignés en jaune sous la forme `[À compléter : …]`. Rechercher `a-completer` dans les fichiers HTML pour tous les retrouver, compléter, puis supprimer la balise `<mark class="a-completer">`.

Points principaux :

- **Actualités** : les 6 actualités sont en lorem ipsum avec des dates d'exemple ; supprimer aussi le bandeau « Contenus provisoires » en haut de `actualites.html`.
- **Chiffres clés** (accueil) : membres, conférences, numéros de la RESS, année de création.
- **Photos** : cadres « Photo à venir ».
- **Agenda** (accueil), **bureau** (À propos), **comité de rédaction et numéros** (RESS).
- **Directeur de la publication** : « Président XXX » (mentions légales, RESS, À propos).
- **Date de création** : les annuaires publics divergent (11/04/2019 ou 31/01/2023) — à vérifier au JOAFE.

## Modifier le contenu

Les pages s'éditent directement dans un éditeur de texte ou dans l'interface de GitHub (icône crayon sur le fichier, puis *Commit changes*).

### Ajouter une actualité

Dans `actualites.html`, copier un bloc `<article class="actu revele" …> … </article>` et l'insérer **en tête** de la liste (sous `<div class="fil">`), puis adapter :

- `id="actu-…"` : identifiant unique, sans espace ni accent (sert de lien direct : `actualites.html#actu-…`) ;
- `data-categorie="…"` : une des valeurs `conference`, `visite`, `partenariat`, `vie` (utilisée par le filtre) ;
- le libellé de la catégorie (`<span class="categorie">`), la date (`<time datetime="AAAA-MM-JJ">`), le titre, le résumé et le texte complet (dans `<div class="texte-complet">`).

La première actualité est mise en avant avec la classe `actu--une` : la retirer de l'ancienne et l'ajouter à la nouvelle.

Mettre ensuite à jour les **trois cartes** de la section « Dernières actualités » de `index.html` (blocs `<a class="carte revele" …>`) : titre, date, catégorie, résumé et lien `href="actualites.html#actu-…"`.

### Remplacer un cadre « Photo à venir » par une photo

1. Déposer l'image dans `assets/` (JPEG, largeur 1600 px au plus, idéalement moins de 300 Ko), par exemple `assets/conference-rentree.jpg`.
2. Remplacer, dans le bloc concerné :

```html
<div class="cadre" role="img" aria-label="Emplacement photo"><span class="legende-cadre">Photo à venir</span></div>
```

par :

```html
<div class="cadre"><img src="assets/conference-rentree.jpg" alt="Description de la photo"></div>
```

La photo est recadrée automatiquement dans le cadre. Vérifier que l'association dispose des droits sur l'image et du consentement des personnes reconnaissables.

### Modifier les couleurs

Les couleurs sont définies une seule fois en tête de `assets/style.css` (bloc `:root`) : `--bleu` (bleu du logo), `--bleu-nuit` (pied de page), etc.

## Charte

- Bleu du logo `#1F2447`, fond blanc, texte noir.
- Titres : EB Garamond ; texte courant : Charis SIL.
- Animations désactivées automatiquement si le visiteur a demandé la réduction des animations dans son système.
