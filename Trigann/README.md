# TriGann

Triangle de Gann, modèle Sacred, pour ATAS Classic et ATAS X. On place trois points sur le graphique. L'indicateur trace le triangle, l'objectif PT et les zones Z1 et Z2, puis signale la reprise du mouvement.

Version actuelle : **1.0.5**. Dans les paramètres, la ligne Version affiche `1.0.5_Classic` ou `1.0.5_AtasX`.

## ⚙️ Fonctionnalités majeures

- Trois clics posent les points 1, 2 et 3. Le sens du mouvement est celui du segment 1 vers 2 : hausse pour un achat, baisse pour une vente.
- Le triangle, les étiquettes 1, 2 et 3, le niveau PT et les bandes Z1 et Z2 sont dessinés à partir du point 3. Si le segment 2-3 est plus long que 1-2, le tracé passe en correction et le contour devient gris.
- **Signal de clôture.** Un triangle vert (achat) ou rouge (vente) apparaît sur la première bougie close après le point 3 qui reprend le mouvement, sans avoir enfoncé le point 3, et seulement s'il reste plus de chemin jusqu'au PT que jusqu'au stop placé juste au-delà du point 3.
- **Anticipation.** Une flèche orange se pose sur la bougie en cours quand le point 3 tient encore, que l'extrême de la bougie précédente est cassé, et que la même condition de distance au PT est déjà remplie. Elle disparaît à la clôture si le signal n'est pas confirmé.
- **Alerte.** Un son peut être joué une seule fois, au moment où le triangle de signal vient de se fermer. Les signaux déjà passés ne sonnent pas.
- Les figures, leur position et l'emplacement du bandeau sont mémorisés avec le graphique.

## Utilisation

Le bandeau est en bas à gauche du graphique. La poignée à gauche se glisse pour le déplacer. Un clic agit sur le bouton, un déplacement le pose ailleurs.

1. Cliquer **Tracer**. Le bouton indique le point attendu : Point 1, puis 2, puis 3.
2. Cliquer trois fois sur le graphique. Avec **Accrocher au high/low**, chaque clic se colle au plus haut ou au plus bas de la bougie, selon le plus proche.
3. Le triangle se dessine. Glisser un sommet pour le déplacer. Cliquer un côté le sélectionne.
4. La croix au centre du triangle supprime cette figure. **Effacer** retire toutes les figures du graphique.

Si Footprint Design est sur le même graphique, les points se calent sur la largeur de bougie de cet indicateur.

## Installation

Deux fichiers, un par plateforme.

| Plateforme | Fichier | Dossier |
| --- | --- | --- |
| ATAS Classic | `TriGann_Classic.dll` | `%AppData%\ATAS\Indicators` ou `Documents\ATAS\Indicators` |
| ATAS X (Windows et macOS) | `TriGann_AtasX.dll` | `%AppData%\ATAS X\Indicators` ou `Documents\ATAS X\Indicators` |

Redémarrer la plateforme après la copie. L'indicateur est dans la catégorie **Gann**, sous le nom **TriGann**.

## 🛠️ Configuration & Paramètres

### TriGann

| Paramètre | Défaut | Rôle |
| --- | --- | --- |
| Version | `1.0.5_Classic` ou `1.0.5_AtasX` | Lecture seule. Identifie l'assemblage chargé. |
| Accrocher au high/low | coché | Colle chaque point au plus haut ou au plus bas de la bougie. |

### Signaux

| Paramètre | Défaut | Rôle |
| --- | --- | --- |
| Signal de clôture | coché | Affiche le triangle d'achat ou de vente à la clôture. |
| Anticipation | coché | Affiche la flèche orange sur la bougie en cours. |
| Alerte au signal | décoché | Joue un son une fois, à la fermeture du triangle de signal. |
| Fichier d'alerte | `alert1` | Nom du son ATAS, sans extension. |
| Couleur achat | vert | Couleur du triangle de signal à l'achat. |
| Couleur vente | rouge | Couleur du triangle de signal à la vente. |

### Apparence

| Paramètre | Défaut | Rôle |
| --- | --- | --- |
| Etiquettes des niveaux | coché | Affiche Z1, Z2 et PT avec leur prix, à droite du graphique. |
| Prix des sommets | coché | Affiche le prix sous ou au-dessus des points 1, 2 et 3. |
