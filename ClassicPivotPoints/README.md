# Classic Pivot Points + PDH / PDL

Indicateur ATAS X pour les points pivots **Classic** et les niveaux PDH / PDL. Le calcul n'utilise que la période précédente clôturée. Les méthodes Camarilla, Fibonacci, Woodie et DeMark ne sont pas présentes.

---

## 💾 Téléchargement

👉 [Cliquez ici pour télécharger les fichiers DLL de Classic Pivot Points (ATAS Classic & ATAS X)](https://github.com/Eywa974/mes-indicateurs-atas/releases/tag/v1.2.2-ClassicPivotPoints)

## Installation

Deux bibliothèques, une par plateforme :

| Plateforme | Fichier | Dossier |
| --- | --- | --- |
| ATAS X, Windows | `dist/ClassicPivotPoints_AtasX.dll` | `%APPDATA%\ATAS X\Indicators` |
| ATAS X, macOS | `dist/ClassicPivotPoints_AtasX.dll` | `~/Library/Application Support/ATAS/Indicators` |
| ATAS classique, Windows | `dist/ClassicPivotPoints_Classic.dll` | `%APPDATA%\ATAS\Indicators` |

La plateforme recharge le dossier tout seul, environ une seconde après la copie. L'indicateur apparaît dans le groupe **Custom** sous le nom **Classic Pivot Points**. 
La version 1.2.2 figure dans la description. Sur un graphique journalier, les niveaux sont calculés avec les bougies déjà chargées sur ce graphique. Il reste sur le panneau des prix.

## Calcul

Source unique : les bougies **journalières** de l'instrument, demandées à ATAS indépendamment du timeframe du graphique. Un graphique en 1 minute et un graphique en 15 minutes reçoivent donc les mêmes niveaux, tant que la série journalière couvre la période.

Pour chaque unité, le niveau affiché sur la période en cours vient exclusivement de la période précédente déjà terminée.

| Unité | Source |
| --- | --- |
| Daily | séance journalière précédente |
| Weekly | semaine précédente |
| Monthly | mois précédent |
| Quarterly | trimestre précédent |
| Yearly | année précédente |

Formules, sans arrondi au tick :

```text
P  = (High + Low + Close) / 3
R1 = (2 × P) − Low
S1 = (2 × P) − High
R2 = P + (High − Low)
S2 = P − (High − Low)
R3 = High + 2 × (P − Low)
S3 = Low − 2 × (High − P)
```

Seul le jeu de la période en cours est tracé. Un graphique qui contient cinq jours ne montre que les niveaux daily de la dernière séance.

High, Low et Close sont ceux de la période source. Pour la semaine, le mois, le trimestre et l'année, ils sont agrégés depuis les séances journalières : plus haut des plus hauts, plus bas des plus bas, clôture de la dernière séance de la période.

La date de séance vient de la bougie journalière ATAS.

- Séance contenue dans un jour calendaire : ce jour.
- Séance qui se termine à minuit : jour d'ouverture.
- Séance overnight (futures) : jour de clôture. La séance du lundi ouverte le dimanche soir appartient au lundi.

Semaine : semaine ISO, du lundi au dimanche. Mois : mois calendaire. Trimestre : janvier–mars, avril–juin, juillet–septembre, octobre–décembre. Année : année calendaire.

La période la plus ancienne est ignorée comme source si l'historique commence au milieu de cette période. Les périodes suivantes, bornées par un changement de période observé, restent fixes. La séance ou la période encore en cours n'entre jamais dans son propre calcul : ses plus hauts et plus bas peuvent changer sans déplacer les niveaux déjà affichés.

PDH est le plus haut de la séance journalière précédente. PDL en est le plus bas. Ils sont tracés sur la séance en cours seulement.

## Paramètres

La fenêtre de réglages contient trois catégories.

### Données

**Rôle** : Indépendant, Maître ou Esclave. Indépendant calcule sur le graphique. Le maître calcule et publie les niveaux de son instrument. L'esclave ne recalcule pas : il affiche les prix publiés par le maître du même instrument, placés sur ses propres bougies. Les couleurs, les étiquettes et les alertes de l'esclave restent locales.

**Canal** : texte commun au maître et à ses esclaves. Laisser vide pour un seul maître par instrument.

Pour Daily, Weekly, Monthly, Quarterly et Yearly, **Afficher** montre ou cache les niveaux de cette unité. Chaque unité ne trace que son jeu en cours.

Daily, Quarterly, Yearly, PDH et PDL sont affichés au départ. Weekly et Monthly sont prêts, il reste à les activer. Quarterly et Yearly demandent les bougies journalières de la période précédente : environ deux trimestres et deux années de séances. Si la plateforme ne fournit pas cette profondeur, le niveau correspondant n'est pas inventé. Une année ou un trimestre dont la première séance tombe dans les quatre premiers jours reste une source complète. Un historique qui commence au milieu de la période est ignoré.

### Visualisation

Chaque unité a ses propres réglages pour P, R1, R2, R3, S1, S2 et S3.

- Afficher ou masquer le niveau.
- **Ligne** : couleur, style et épaisseur de la palette native ATAS (`PenSettings`).
- Étiquette : nom du niveau, avec la date de la période où il s'applique.
- Prix : format de l'instrument, via le graphique ATAS.

Position du texte, commune aux niveaux d'une même unité :

- horizontale : gauche ou droite de la ligne ;
- verticale : au-dessus ou en dessous ;
- couleur du texte ;
- taille du texte, de 8 à 32.

La ligne part du début de la période en cours et va jusqu'au bord droit du graphique de prix. Les périodes déjà terminées ne sont pas dessinées.

PDH et PDL ont les mêmes choix de ligne, d'étiquette, de prix, de couleur et de taille, plus la position verticale du texte. Leurs styles initiaux sont différents des pivots : PDH orange en tirets, PDL cyan en pointillés. L'étiquette est placée à droite.

Forme des étiquettes :

| Niveau | Exemple | Date affichée |
| --- | --- | --- |
| Pivot daily ou weekly | `D P 02.11` | période où le niveau est valable |
| Pivot monthly | `M R1 11.2026` | mois d'application |
| Pivot quarterly | `Q S2 Q4.2026` | trimestre d'application |
| Pivot yearly | `Y P 2026` | année d'application |
| PDH / PDL | `PDH 31.10` | séance clôturée qui a produit le prix |

### Alertes

Pour P, R1, R2, R3, S1, S2, S3 de chaque unité, et séparément pour PDH et PDL :

- activer l'alerte ;
- toucher le niveau (la bougie englobe le prix) ;
- traverse à la hausse ;
- traverse à la baisse.

Les alertes ne concernent que les niveaux de la période en cours. Un contact maintenu ne se répète pas à chaque tick : le toucher se réarme quand le prix quitte le niveau, et la traversée se réarme au passage suivant. Au chargement, et quand un niveau apparaît, l'état est mémorisé sans alerte. L'alerte suivante correspond à un nouveau mouvement.

**Son** : nom du fichier ATAS sans extension. La valeur initiale est `alert1`. D'autres noms du dossier Sounds conviennent : `alert2`, `alert3`, `beep_1_1`.

ATAS joue le son et affiche l'alerte ensemble. Cette version de l'API n'offre pas un interrupteur séparé pour la fenêtre. L'interrupteur d'alertes de l'indicateur reste actif par défaut.

Une unité masquée dans Données peut quand même déclencher une alerte si son alerte est activée. Les niveaux ne sont pas dessinés tant que Afficher est désactivé.

ATAS peut limiter la profondeur de la série journalière demandée par un indicateur. L'indicateur demande le nombre de séances nécessaire au trimestre et à l'année précédents, puis se replie sur une profondeur plus courte si la plateforme refuse la première. Si l'historique reçu ne contient pas la période source, le niveau correspondant n'est pas inventé.

La série journalière suit la session par défaut de l'instrument. Les niveaux restent ceux de cette session, quel que soit le filtre de session du graphique.

Les prix calculés ne sont pas arrondis au tick. L'étiquette, elle, utilise la précision de l'instrument.
