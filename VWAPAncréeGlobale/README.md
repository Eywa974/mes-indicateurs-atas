# 📊 VWAP ancrée globale (Indicateur pour ATAS)

> **VWAP ancrée globale** pose une ancre sur un graphique et la retrouve sur tous les graphiques du même instrument. Chaque graphique recalcule la VWAP à partir de ses propres barres, depuis la barre qui contient cette ancre.

Version actuelle : **1.1.2**. Dans **About**, la ligne Version affiche `1.1.2_Classic` ou `1.1.2_AtasX`.

---

## ✨ Fonctionnalités principales

* **Ancre partagée :** une VWAP posée, déplacée ou retirée sur un graphique l'est sur tous les graphiques du même instrument qui portent l'indicateur. Jusqu'à 12 ancres.
* **Calcul par graphique :** `somme(prix × volume) / somme(volume)`, depuis la barre qui contient l'ancre. Une barre sans volume ne fait pas bouger la ligne. Un 30 minutes et un 2 000 volumes partent du même instant, mais le prix n'est pas identique : chaque unité de temps découpe le volume à sa façon.
* **Prix et volume au choix :** Open, High, Low, Close, HL2, HLC3, OHLC4 ou HLCC4. Volume total, bid ou ask. Le défaut est le **haut** de la barre et le **volume total**, comme l'objet VWAP ancré d'ATAS tel qu'il est réglé sur ces graphiques.
* **Écarts-types :** bandes VWAP ± k × écart-type pondéré par le volume. Trois coefficients, coupés par défaut.
* **Trait :** couleur, épaisseur et style de la VWAP, et un second stylo pour les écarts.
* **Panneau déplaçable :** **Ancre** en bas à gauche, sous la liste des indicateurs. La poignée à gauche se glisse. Le chevron **▾** replie la liste, **▸** la rouvre. L'emplacement et l'état replié sont mémorisés sur chaque graphique.
* **Déplacement de la ligne :** glisser la VWAP, ou le carré à son départ, sur n'importe quel graphique. Le curseur devient une double flèche horizontale. Les autres graphiques suivent. Au-dessus d'une croix de suppression, le curseur reste la flèche normale.
* **Historique :** si le graphique n'a pas chargé de barres jusqu'à l'ancre, la liste affiche **hors historique** et aucune ligne n'est inventée.
* **Multi-compatibilité :** `AnchoredVwapGlobal_Classic.dll` pour ATAS Classic, `AnchoredVwapGlobal_AtasX.dll` pour ATAS X (Windows et macOS).

Pour poser une ancre : cliquer **Ancre**, puis la barre de départ. La croix retire cette ancre partout. **Effacer toutes les ancres** vide la liste.

---

## 📸 Aperçu


<img width="964" height="528" alt="VWAP40k" src="https://github.com/user-attachments/assets/72527bef-b8fe-497c-883f-df16a538586e" />
<img width="728" height="517" alt="VWAP10k" src="https://github.com/user-attachments/assets/1a52662e-1320-4632-8e00-1e44cce73a79" />

---

## 📥 Téléchargement

Cliquez sur le bouton ci-dessous pour accéder à la **dernière version disponible** (sélectionnez toujours la release située tout en haut de la page, puis téléchargez le fichier `.dll` dans la section **Assets**) :

👉 **[Télécharger la dernière version de VWAP ancrée globale]((https://github.com/Eywa974/mes-indicateurs-atas/releases?q=VWAPG))**

Deux fichiers, un par plateforme :

| Plateforme | Fichier |
| :--- | :--- |
| ATAS Classic | `AnchoredVwapGlobal_Classic.dll` |
| ATAS X (Windows et macOS) | `AnchoredVwapGlobal_AtasX.dll` |

---

## 🛠️ Installation & Mise à jour

### 1. Première installation
1. Téléchargez le fichier qui correspond à votre version d'ATAS.
2. Fermez complètement la plateforme **ATAS**.
3. Copiez le fichier `.dll` dans le dossier des indicateurs personnalisés :
   * **ATAS Classic :** `Documents\ATAS\Indicators` (ou `%AppData%\ATAS\Indicators`)
   * **ATAS X :** `Documents\ATAS X\Indicators` (ou `%AppData%\ATAS X\Indicators`)
4. S'il reste un ancien `AnchoredVwapGlobal.dll` sans suffixe dans ce dossier, retirez-le. ATAS charge chaque DLL du dossier, et les deux copies s'afficheraient ensemble.
5. Relancez **ATAS**, ouvrez un graphique, faites un clic droit ➡️ **Indicators** et recherchez **VWAP ancrée globale**. **About** doit afficher `Version 1.1.2_Classic` ou `Version 1.1.2_AtasX`.
6. Ajoutez l'indicateur sur chaque graphique qui doit afficher les ancres. Un graphique sans l'indicateur ne les dessine pas.

### 2. Mettre à jour l'indicateur
1. Fermez **ATAS**.
2. Téléchargez la nouvelle `AnchoredVwapGlobal_Classic.dll` ou `AnchoredVwapGlobal_AtasX.dll`.
3. Collez-la dans le même dossier `Indicators` et acceptez de **remplacer le fichier existant**.
4. Relancez **ATAS**. Les ancres déjà posées et les réglages du graphique sont conservés.

Les ancres sont rangées par instrument et survivent à un redémarrage d'ATAS. **Canal** vide relie tous les graphiques de l'instrument. Un même nom de canal isole un sous-ensemble.

---

## ⚙️ Paramètres principaux

| Paramètre | Description |
| :--- | :--- |
| **Canal** | Vide : tous les graphiques de l'instrument. Une même valeur relie seulement les graphiques qui la partagent. |
| **Ancres** | Liste en lecture seule des heures d'ancre, en UTC. `aucune` s'il n'y en a pas. |
| **Effacer toutes les ancres** | Retire toutes les ancres du canal, sur tous les graphiques liés. |
| **Prix** | Prix de chaque barre. Défaut **High**. Autres valeurs : Open, Low, Close, HL2, HLC3, OHLC4, HLCC4. Gardez le même choix sur tous les graphiques si vous voulez comparer la même construction. |
| **Volume** | `Total` (défaut), `Bid` ou `Ask`. |
| **Écarts-types** | Off par défaut. On : trois bandes autour de la VWAP. |
| **Écart 1, 2, 3** | Coefficients de l'écart-type pondéré par le volume. Défaut 1, 2 et 3. |
| **Trait** | Couleur, épaisseur et style de la VWAP. Défaut magenta, plein, épaisseur 2. |
| **Écarts** | Couleur, épaisseur et style des bandes. Défaut magenta atténué, tirets, épaisseur 1. |

---

## ⚠️ Avertissement (Disclaimer)

*Cet outil est fourni à titre purement informatif et éducatif. Le trading sur les marchés financiers comporte des risques élevés de perte en capital. L'auteur ne saurait être tenu responsable des décisions d'investissement ou des pertes financières liées à l'utilisation de cet indicateur.*
