# Des possibilités infinies

[Le Cherry-Mx-Bitboard](https://github.com/ogatatsu/Cherry-Mx-Bitboard) a été modifié pour que le SK6812mini en soit accro en référence à l'hélice.

Une carte imprimée pour un clavier fait maison, une carte correspond à un interrupteur.![pcb](./images/pcbs.jpg)

Avec cette carte, vous pouvez créer un clavier rétroéclairé en couleur avec une disposition originale sans concevoir la carte.

Par exemple ...!

![exemple exemple](https://cdn-ak.f.st-hatena.com/images/fotolife/s/swan_match/20180915/20180915184339.jpg)

Cliquez ici pour plus de détails.

Nous avons publié [comment faire une plaque supérieure](https://swanmatch.github.io/topplate_tips) .

# Langues

- [Japonais](./readme.md)
- [Anglais](./readme_en.md)
- [français](./readme_fr.md)
- [russe](./readme_ru.md)
- [chinois](./readme_zh.md)

## Série de possibilités infinies

### Maison ProMicro

La broche de ProMicro peut être retirée, avec OLED, interrupteur de réinitialisation, TRRS pour clavier divisé et trou de vis M2 pour le montage.
 Les attributions de broches TRRS sont compatibles Helix.

### Série de possibilités infinies

Il existe plusieurs séries de possibilités infinies, chacune avec différentes LED et diodes de commutation correspondantes.
 Les spécifications sont résumées ci-dessous.

projet | commutateur | Disponibilité de la prise Kailh | LED | Diode traversante | SOD-123
--- | --- | --- | --- | --- | ---
Lien | MX | Non | SK6812MINI | Oui | Non
Altana | MX | Oui | SK6812MINI | Oui | Non
Suxen | MX | Non | YS-SK6812MINI | Oui | Oui (*)
Récipient | MX | Oui | YS-SK6812MINI | Oui | Oui (*)
Choc | KailhLowProfile | Non | YS-SK6812MINI | Non | Oui

(*) Lors de l'utilisation de SOD-123 avec Swen et conteneur, un pad sera partagé avec le trou du trou traversant en raison des limitations d'espace, donc ce sera une implémentation un peu délicate.

## Exemple de matériau (fournisseur)

- Assiette coupée arbitrairement
    - Panneau acrylique 2 mm (Yusha Kobo)
         Ce serait bien d'avoir un adhésif tel qu'un carré acrylique de 3 mm et un sundae acrylique. (Centre d'accueil)
    - Boîtier 3D (DMM.make)
    - Carton de 5 mm (ramasser dans cette zone, etc.)
- Diode de commutation 1N4148, SOD-123 (clavier TALP)
- SK6812mini, YS-SK6812MINI-E (Yusha Kobo)
- Prise Kailh (Yusha Kobo, Talpkeyboard, Kbdfans)
- Fil en émail uréthane (recommandé environ 0,35 à 0,45 mm. Il est également disponible dans les centres de la maison, etc.
- Prise TRRS, bouton RESET (Akizuki Denshi)
- OLED (en option, Yusha Kobo)
- Promicro (Yusha Kobo, clavier TALP)
- Divers entretoises, vis (M. Hirosugi Keiki, M. Wilco, etc.)
- Interrupteur à clé, capuchon de touche (Yusha Kobo, clavier Talp, etc. si vous le souhaitez)
- Câble USB, câble TRS (3,5 mm 3 pôles)

D'autres outils tels qu'un fer à souder à contrôle de température, un testeur et une pince à épiler sont nécessaires.

## Affectation des broches

![pcb](./images/PCB.png)

Les brochages aux possibilités infinies sont:

- C: ligne horizontale (Col)
- R: ligne verticale (ligne)
- DI: entrée de signal de commande LED (DataIn)
- DO: sortie du signal de contrôle LED (DataOut)
- -: Terre (pour LED)
- +: VCC (5V pour LED)

L'exemple de l'image est Suxen, mais les autres sont similaires.

## Procédure d'assemblage

1. Souder le SK6812mini.
     Utilisez un fer à souder à contrôle de température pour souder à environ 220 ° C.
     Il se brisera si vous vous appuyez dessus.
     Utilisez une soudure à basse température avec un point de fusion de 200 ° C ou moins.
2. Souder la diode.
3. Placez l'interrupteur sur la plaque supérieure et soudez les pieds de l'interrupteur à l'arrière avec des possibilités infinies. (Altana, Container est une socket)
     Si vous utilisez une plaque acrylique de 2 mm à ce moment, il est recommandé de fixer un carré acrylique de 3 mm sur le côté de l'interrupteur à l'arrière de la plaque avec un adhésif acrylique pour empêcher l'interrupteur de se détacher.
4. Reliez les lignes horizontales (Col) et verticales (Row) en fonction de la matrice de touches du clavier que vous souhaitez construire.
5. Connectez tous les "-" et "+".
6. Câblez de DI à DO dans l'ordre dans lequel vous voulez que les LED brillent. 1ère DO → 2ème DI → 2ème DO → 3ème DI…
7. Souder le TRRS JACK et le commutateur RESET.
8. Souder la prise OLED.
9. Câblez Col and Row, LED (DO), GND et VCC depuis les trous à côté de n'importe quelle broche pour des possibilités infinies.
10. Souder le Promicro à la prise.
     (Vous pouvez utiliser un con-through, mais il est moins cher de remplacer la prise entière si elle se brise.)
11. Créez et écrivez un micrologiciel à votre goût et complétez
     Le micrologiciel est très simple avec [QMK_Firmware](https://github.com/qmk/qmk_firmware) .
     Référence: [3 types de moyens pour préparer le firmware de votre propre clavier](https://skyhigh-works.hatenablog.com/entry/2018/10/09/120909)

## Exemple de câblage

Par exemple, dans le cas de l'agencement suivant à Suxen, le câblage sera le suivant.
 Comme il est assez difficile d'enlever le revêtement sur le fil d'émail uréthane (UEW), il est recommandé de couper les pieds de diode pour le câblage entre les cartes adjacentes, qui sont moins susceptibles de provoquer un court-circuit.

![pcb](./images/Wired2.png)

### Remarques

- Altana et Container sont des versions qui vous permettent de remplacer le commutateur à l'aide d'un socket Kailh.
- Suxen et Container sont compatibles avec YS-SK6812MINI, et montent les pattes dépourvues de LED selon la soie triangulaire du PCB.
- Si, dans le cas peu probable où vous n'avez pas besoin d'allumer la LED, vous ne pouvez câbler que Col et Row pour fonctionner comme un clavier. [Exemple de câblage](./images/Wired.png)
- Dans le cas des claviers à montage sandwich, qui sont souvent utilisés au Japon, la plaque supérieure et la plaque inférieure sont placées avec des entretoises, mais dans le cas de possibilités illimitées, il n'y a pas d'espace pour les entretoises pour entrer entre les touches. Faites un trou de vis à l'extérieur de la clé.
- Si Promicro est d'abord soudé à la «maison», la soudure peut fuir du trou lors du câblage vers le côté des possibilités infinies, provoquant un court-circuit dans les parties de l'unité principale Promicro.
     Assurez-vous de souder le Promicro en dernier.

## À la fin

Si vous avez assemblé un clavier à l'aide de cette carte, veuillez nous en informer à @swan_match .

Nous soutenons votre End Game! !!

## Licence

https://creativecommons.org/licenses/by/4.0/
