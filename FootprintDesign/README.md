# 📊 Footprint Design (Indicateur pour ATAS)

> **Footprint Design** est un indicateur personnalisé pour la plateforme de trading ATAS. Il dessine le footprint en delta ou en volume, avec les bougies, la value area, les gros prints, un HUD et les VWAP RTH / ETH.

---

## ✨ Fonctionnalités principales

* **Footprint Delta ou Volume :** la largeur des cellules suit le delta ou le volume. La couleur suit toujours le delta, achat ou vente.
* **Cellules :** texte centré, opacité, bordure, padding, coins arrondis, et un petit texte optionnel sous un seuil de delta.
* **Value area :** POC, plus fort delta acheteur, plus fort delta vendeur, et lignes VAH / VAL.
* **Bougies :** contour et mèche à gauche du footprint, ou bougie classique. Le remplissage peut reprendre la teinte **Delta Effort** de Cluster Statistic + sur le même graphique, sans changer le contour ni la mèche.
* **Zoom :** largeur et hauteur de cellule. En dessous d'un seuil, les cellules peuvent disparaître et laisser la bougie occuper toute la barre.
* **Quatre plages de couleur** selon la valeur absolue du delta. Une cellule sous tous les seuils, ou de delta nul, reste vide.
* **Big trades :** quatre plages de volume, formes creuses (carré, cercle, triangle, diamant), couleur bid / ask, bordure et texte proportionnels. Mode cumulatif ou print par print. Les marques restent sur leur bougie d'origine.
* **HUD déplaçable :** Delta / Volume, regroupement 1, 2, 4 ou 8 ticks, zoom des cellules, et fermeture. La poignée à gauche se glisse au clic gauche.
* **Fusion au clic**, coupée par défaut : clic gauche sur une bougie pour la sélectionner, clic gauche sur la voisine pour additionner volumes et deltas, clic droit pour séparer. Une seule bougie résume le groupe, à gauche.
* **VWAP RTH** (09:30–16:00, heure de New York) et **VWAP ETH** (18:00 la veille jusqu'à 17:00). Chaque séance repart de zéro.
* **Multi-compatibilité :** `FootprintDesign_Classic.dll` pour ATAS Classic, `FootprintDesign_AtasX.dll` pour ATAS X (Windows et macOS).

---

## 📸 Aperçu

*(Conseil : Glissez-déposez une capture d'écran de votre indicateur directement dans l'éditeur GitHub pour générer le lien de l'image ici)*

![Aperçu de l'indicateur Footprint Design](<img width="1329" height="711" alt="VP" src="https://github.com/user-attachments/assets/636b35c0-e7e9-4f6d-adab-edd93f4ccc91" />)
<img width="1329" height="711" alt="VP" src="https://github.com/user-attachments/assets/cae4be51-e585-4297-9db4-c4f988e6574c" />


---

## 📥 Téléchargement

Cliquez sur le bouton ci-dessous pour accéder à la **dernière version disponible** (sélectionnez toujours la release située tout en haut de la page, puis téléchargez le fichier `.dll` dans la section **Assets**) :

👉 **[Télécharger la dernière version de Footprint Design](https://github.com)**

Deux fichiers, un par plateforme :

| Plateforme | Fichier |
| :--- | :--- |
| ATAS Classic | `FootprintDesign_Classic.dll` |
| ATAS X | `FootprintDesign_AtasX.dll` |

---

## 🛠️ Installation & Mise à jour

### 1. Première installation
1. Téléchargez le fichier qui correspond à votre version d'ATAS.
2. Fermez complètement la plateforme **ATAS**.
3. Copiez le fichier `.dll` dans le dossier des indicateurs personnalisés :
   * **ATAS Classic :** `Documents\ATAS\Indicators` (ou `%AppData%\ATAS\Indicators`)
   * **ATAS X :** `Documents\ATAS X\Indicators` (ou `%AppData%\ATAS X\Indicators`)
4. S'il reste un ancien `FootprintDesign.dll` sans suffixe dans ce dossier, retirez-le. ATAS charge chaque DLL du dossier, et les deux copies s'afficheraient ensemble.
5. Relancez **ATAS**, ouvrez un graphique, faites un clic droit ➡️ **Indicators** et recherchez **Footprint Design**. Le champ **Version** doit afficher `1.3.21`.

### 2. Mettre à jour l'indicateur
1. Fermez **ATAS**.
2. Téléchargez la nouvelle `FootprintDesign_Classic.dll` ou `FootprintDesign_AtasX.dll`.
3. Collez-la dans le même dossier `Indicators` et acceptez de **remplacer le fichier existant**.
4. Relancez **ATAS**. Les paramètres déjà enregistrés sur le graphique sont conservés. Les nouveaux réglages apparaissent avec leur valeur par défaut.

Les modèles d'indicateur sont rangés dans un dossier au nom affiché **Footprint Design**.

---

## ⚙️ Paramètres principaux

Les bougies natives du graphique sont masquées tant que l'indicateur est attaché.

| Paramètre | Description |
| :--- | :--- |
| **Mode** | `Delta` : la largeur d'une cellule suit le \|delta\| du niveau. `Volume` : la largeur suit le volume. La couleur reste celle du delta. |
| **Échelle par bougie** | On : le plus gros niveau de la bougie remplit la largeur. Off : une échelle commune. |
| **Proportion des bougies visibles** | On : le maximum est celui à l'écran. Off : le maximum de tout le graphique chargé. Ignoré si l'échelle par bougie est active. |
| **Regrouper (ticks)** | `1`, `2`, `4` ou `8`. Au-dessus de 1, delta et volume sont additionnés. Le bouton du HUD enchaîne ces quatre valeurs. POC et value area sont recalculés sur la grille regroupée. |
| **Fusion au clic** | Off par défaut. On : clic gauche sur la bougie pour sélectionner (cadre jaune autour de la bougie), clic gauche sur la colonne voisine pour fusionner, clic droit pour séparer. Un clic dans le vide ne sélectionne rien et laisse déplacer le graphique. Le champ **Fusions** mémorise les groupes ; il est ignoré tant que la fusion est coupée. |
| **Texte delta** | Delta de chaque niveau, centré sur la colonne. Masqué si la colonne fait moins de 8 px ou si la ligne est plus basse que la police. Si le nombre ne tient pas, l'affichage passe en forme compacte (`1.2k`, `10k`). |
| **Delta ÷ 10** | Off : entier. On : arrondi de delta / 10. |
| **Petit texte sous le seuil** | Off par défaut. Sous le seuil (15 par défaut, en \|delta\| brut), police et, si demandé, couleur alternative. |
| **Value area %** | Part du volume autour du POC, de 50 à 90. Défaut 70. |
| **POC / Max achat / vente / Lignes VA** | Bordure du plus fort volume, marques du plus fort delta acheteur et vendeur, et traits VAH / VAL. |
| **Bougies classiques** | On : corps et mèche à gauche du footprint, sur **Largeur classique %** de la barre (saisie au clavier, 5 à 80, défaut 20). Off : un contour étroit par-dessus le footprint. |
| **Remplissage** | `Vide` : contour seul. `Hausse / baisse` : couleur du stylo. `Delta Effort` : teinte du corps lue sur **Cluster Statistic +** du même graphique (maximum, couleurs achat / vente et fond du tableau). Le contour et la mèche restent les stylos Hausse et Baisse. |
| **Bougies seules si dézoomé** | Sous **Seuil (px de barre)** (défaut 8), les cellules disparaissent et la bougie prend toute la barre. |
| **Largeur / Hauteur de cellule** | Cibles en pixels (défaut 33 × 19). Le bouton **Zoom** du HUD les applique à la largeur des barres et à l'échelle de prix. |
| **Niveaux 1 à 4** | Couleur achat et vente à partir d'un \|delta\|. Le seuil le plus haut atteint l'emporte. Une couleur transparente ne remplit pas et ne trace pas le contour. |
| **Big trades** | Quatre plages (`Depuis`, forme, couleurs ask / bid, bordure, épaisseur, texte, tailles min / max). **Cumulatif** utilise les agrégats ATAS. Sous **Dézoom sous (px)**, les marques rétrécissent selon **Ratio dézoom** sans passer sous la taille min. |
| **HUD** | Barre de boutons, visible par défaut. **Décalage X / Y** mémorise l'emplacement après un glisser de la poignée. |
| **VWAP RTH / ETH** | Les deux sont affichés par défaut. RTH bleu, ETH jaune. Prix typique (plus haut + plus bas + clôture) / 3. |

---

## ⚠️ Avertissement (Disclaimer)

*Cet outil est fourni à titre purement informatif et éducatif. Le trading sur les marchés financiers comporte des risques élevés de perte en capital. L'auteur ne saurait être tenu responsable des décisions d'investissement ou des pertes financières liées à l'utilisation de cet indicateur.*

