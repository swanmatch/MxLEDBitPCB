# Des possibilités infinies

[Cherry-Mx-Bitboard](https://github.com/ogatatsu/Cherry-Mx-Bitboard) est modifié de sorte que SK6812mini est accro à l'hélice.

Carte de circuit imprimé pour clavier auto-fabriqué, une carte correspond à un commutateur. ![pcb](pcbs.jpg)

En utilisant cette carte, vous pouvez créer un clavier rétroéclairé en couleur avec une disposition originale sans concevoir la carte.

Par exemple ...!

![exemple](https://cdn-ak.f.st-hatena.com/images/fotolife/s/swan_match/20180915/20180915184339.jpg)

[Cliquez ici pour](https://swan-match.hatenablog.com/entry/2018/09/15/184923) plus [de](https://swan-match.hatenablog.com/entry/2018/09/15/184923) détails.

De plus, nous avons révélé [comment fabriquer](https://swanmatch.github.io/topplate-tips) la [plaque supérieure](https://swanmatch.github.io/topplate-tips) .

[Anglais](https://translate.google.com/translate?hl=ja&sl=auto&tl=en&u=https%3A%2F%2Fswanmatch.github.io%2FMxLEDBitPCB%2F&sandbox=1)

## Série de possibilités infinies

### Maison ProMicro

Les broches ProMicro peuvent être retirées, plus OLED, interrupteur de réinitialisation, TRRS pour clavier divisé et trous de vis M2 pour le montage.
 L'affectation des broches TRRS est compatible Helix.

### Nexus

À moins que les 25 touches d'origine ne soient déconnectées, Col et Row et VCC et GND verticaux ne nécessitent pas de câblage.

Bien sûr, il peut être utilisé même s'il est séparé.

### Altana

Version précâblée comme Nexus et version commutable avec prise Kailh.

## Exemple de matériau (fournisseur)

- Assiette coupée arbitrairement
    - Planche acrylique de 2 mm (studio Yusha)
         Il est bon d'avoir un adhésif comme du bois acrylique de 3 mm et du sundae acrylique. (Centre d'accueil)
    - Boîtier 3D (DMM.make)
    - Carton de 5 mm (tel que ramassé à partir de là)
- Diode de commutation 1N4148 (par TALPKeyboard)
- SK6812mini (studio Yusha)
- Fil émaillé en uréthane (0,35 à 0,45 mm est recommandé. Il est également disponible dans les magasins de rénovation. Le fil de vinyle est également disponible, mais il peut être fondu ou assez difficile.)
- Prise TRRS, bouton RESET (M. Akizuki Denshi)
- OLED (en option, Yusha Kobo)
- Promicro (Yusha Kobo, TALPkeyboard)
- Différentes entretoises et vis (Hirosugi Keiki, Wilco, etc.)
- Interrupteurs à clé, cache-clés (Yusha Kobo, TalpKeyboard, etc. selon votre préférence)
- Câble USB, câble TRS (3,5 mm3 pôles)

De plus, des outils tels qu'un fer à souder à contrôle de température, un testeur et une pince à épiler sont nécessaires.

## Affectation des broches

![pcb](pcb1.png)

Les brochages des possibilités infinies sont:

- C: Ligne horizontale (Col)
- R: ligne verticale (ligne)
- DI: entrée de signal de commande LED (DataIn)
- DO: sortie du signal de commande LED (DataOUT)
- -: Masse (pour LED)
- +: VCC (5V pour LED)

## Procédure d'assemblage

1. Solder SK6812mini.
     Soudez à environ 220 ° C avec un fer à souder à température réglable.
     Il se cassera s'il est bloqué.
     Utilisez une soudure à basse température avec un point de fusion de 200 ° C ou moins.
2. Soudez la diode.
3. Placez l'interrupteur sur la plaque supérieure et soudez les pieds de l'interrupteur avec des possibilités infinies à l'arrière.
     (Altana est une prise.) Si vous utilisez une carte acrylique de 2 mm à ce moment, il est bon de fixer un matériau acrylique de 3 mm sur le côté de l'interrupteur à l'arrière de la plaque avec de l'adhésif acrylique pour empêcher l'interrupteur de se détacher.
4. Câblez la ligne horizontale (Col) et la ligne verticale (Row) selon la matrice de touches du clavier que vous souhaitez assembler.
5. Connectez tous les "-" et "+".
6. Câblez les perles de DI à DO dans l'ordre dans lequel vous souhaitez que les LED brillent. 1er DO → 2e DI → 2e DO → 3e DI…
7. Soudez le commutateur TRRSJACK et RESET.
8. Soudez la prise OLED.
9. Colonne et rangée de fils, LED (DO), GND, VCC à partir du trou à côté de n'importe quelle broche pour chacune des possibilités infinies.
10. Souder le Promicro à la prise.
     (Bien que vous puissiez utiliser un con à travers, mais il est moins cher de remplacer la prise entière si elle casse.)
11. Créez et écrivez le firmware à votre guise et complétez.
     Le firmware est très simple en utilisant [QMK_Firmware](https://github.com/qmk/qmk_firmware) .
     Référence: [Trois types de moyens pour préparer le firmware de votre propre clavier](https://skyhigh-works.hatenablog.com/entry/2018/10/09/120909)

## Exemple de câblage

Par exemple, si vous avez une matrice de réseau 3 * 3, le câblage sera le suivant.
 (Si vous ne déconnectez pas le Nexus Altana, le câblage de Col, Row, VCC vertical et GND entre les cartes n'est pas nécessaire.)
 Le fil émaillé en uréthane (UEW) est assez difficile à décoller le film, donc le câblage entre les cartes adjacentes où la possibilité de court-circuit est faible peut être un pied de diode de coupure.
 La LED est câblée en spirale en haut à droite.

![pcb](pcb9.png)

### Remarques

- Nexus Altana, qui est en circulation depuis avril 2019, possède déjà des lignes électriques Col, Row et verticales (VCC, GND).
- Altana est une version qui vous permet de remplacer le commutateur à l'aide d'une prise Kailh.
- Si vous n'avez pas besoin d'éclairer la LED par tous les moyens, connectez simplement Col et Row et cela fonctionnera comme un clavier.
- Dans le cas des claviers montés en sandwich, qui sont largement utilisés au Japon, la plaque supérieure et la plaque inférieure sont disposées avec des entretoises, mais il n'y a pas d'espace entre les touches pour la possibilité infinie. Prévoyez un trou de vis à l'extérieur de la clé.
- Si le "Home" est soudé au Promicro en premier, lors du câblage à la possibilité infinie, la soudure peut fuir du trou et court-circuiter les parties du corps du Promicro.
     Promicro doit être soudé en dernier.

## À la fin

Si vous avez assemblé un clavier à l'aide de cette carte, veuillez nous en [informer](https://twitter.com/swan_match) à [@swan_match](https://twitter.com/swan_match) .

Je soutiens votre EndGame! !

## Licence

https://creativecommons.org/licenses/by/4.0/
