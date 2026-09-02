# Gustave — site statique

## Mise en ligne sur GitHub Pages

1. Créer un dépôt public, y déposer ce dossier (`index.html` à la racine).
2. Settings → Pages → Source : `Deploy from a branch`, branche `main`, dossier `/ (root)`.
3. Créer à la racine un fichier `CNAME` contenant une seule ligne :
   ```
   gustaveprojet.fr
   ```
4. Chez le registrar du domaine, remplacer les enregistrements par :

   | Type  | Nom | Valeur                 |
   |-------|-----|------------------------|
   | A     | @   | 185.199.108.153        |
   | A     | @   | 185.199.109.153        |
   | A     | @   | 185.199.110.153        |
   | A     | @   | 185.199.111.153        |
   | CNAME | www | VOTRECOMPTE.github.io. |

5. Settings → Pages → cocher `Enforce HTTPS` une fois le certificat émis.

Ne pas supprimer le site Canva avant que la nouvelle version soit en ligne et vérifiée.

## Reste à faire

| Quoi | Où |
|---|---|
| Clé Web3Forms (gratuite, 2 min sur web3forms.com) | `REMPLACER_PAR_VOTRE_CLE_WEB3FORMS` dans `index.html` |
| Jauge minimale et maximale | `<dd>À compléter</dd>` |
| Dossier de présentation | déposer `dossier-gustave.pdf` à la racine |
| Fiche technique | déposer `fiche-technique-gustave.pdf` à la racine |

## Contenu des assets

| Fichier | Provenance |
|---|---|
| `tableau-desespere.mp4` + `.jpg` | VIDEO2, ré-encodée sans son — ouverture de la page |
| `tableau-coquelicots.mp4` + `.jpg` | VIDEO1 — bande après la présentation |
| `tableau-falaise.mp4` + `.jpg` | VIDEO3 — bande avant les dates |
| `hugo/benoit/lisa/erwan.jpg` | recadrages 3:4 dans la photo de groupe |
| `groupe-gustave.jpg` | photo de groupe réduite à 2000 px |
| `toile-gustave.jpg` | visuel peint — image de partage et image de fin |
| `logo-gustave.png` | logo redressé et détouré, non utilisé dans la page |

Les vignettes des trois extraits live sont chargées depuis les serveurs de YouTube
(`i.ytimg.com`). Pour supprimer cette requête vers Google, exporter une image fixe
verticale de chaque Short (720×1280) et remplacer les URL par des chemins locaux.

## Comportement des vidéos

Les trois tableaux animés sont hébergés dans le dépôt (4,4 Mo au total). Ils sont muets,
en boucle, et ne se chargent qu'à l'approche du regard grâce à un `IntersectionObserver` :
une vidéo hors écran est mise en pause. Si le visiteur a activé « réduire les animations »
dans son système, aucune vidéo ne démarre seule et les contrôles de lecture apparaissent.

## Note sur le logo

`LOGO_TRANSPARENT.png` était pivoté de 90° et son rouge (#D24100, orangé) ne correspond
pas à celui du visuel peint (#601D18). La version redressée est dans `assets/logo-gustave.png`.
À vectoriser en SVG pour un rendu net à toutes les tailles.

## Vérifications avant publication

- Lighthouse (outils développeur de Chrome) : viser 100 en performance et accessibilité.
- Coller l'URL dans WhatsApp ou Slack : la vignette de partage doit s'afficher.
- Google Search Console : ajouter la propriété et demander l'indexation.
