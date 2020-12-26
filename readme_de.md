# unendliche Möglichkeiten

[Das Cherry-Mx-Bitboard](https://github.com/ogatatsu/Cherry-Mx-Bitboard) wurde so modifiziert, dass der SK6812mini in Bezug auf die Helix süchtig danach ist.

Eine Leiterplatte für eine selbstgemachte Tastatur, eine Karte entspricht einem Schalter.![pcb](./images/pcbs.jpg)

Mit dieser Karte können Sie eine vollfarbige Tastatur mit Hintergrundbeleuchtung und einem originellen Layout erstellen, ohne die Karte zu entwerfen.

Zum Beispiel ...!

![Beispiel Beispiel](https://cdn-ak.f.st-hatena.com/images/fotolife/s/swan_match/20180915/20180915184339.jpg)

[Klicken Sie hier für](https://swan-match.hatenablog.com/entry/2018/09/15/184923) Details.

Wir haben veröffentlicht, [wie man eine obere Platte macht](https://swanmatch.github.io/topplate_tips) .

# Sprachen

- [japanisch](./readme.md)
- [Englisch](./readme_en.md)
- [Französisch](./readme_fr.md)
- [Russisch](./readme_ru.md)
- [Chinesisch](./readme_zh.md)

## Unendliche Möglichkeiten Serie

### ProMicro House

Der ProMicro-Pin kann mit OLED, Reset-Schalter, TRRS für geteilte Tastatur und M2-Schraubenloch für die Montage herausgenommen werden.
 TRRS-Pinbelegungen sind Helix-kompatibel.

### Unendliche Möglichkeiten Serie

Es gibt mehrere Serien von unendlichen Möglichkeiten mit jeweils unterschiedlichen entsprechenden LEDs und Schaltdioden.
 Die Spezifikationen sind unten zusammengefasst.

Projekt | Schalter | Verfügbarkeit der Kailh-Steckdose | LED | Durchgangslochdiode | SOD-123
--- | --- | --- | --- | --- | ---
Nexus | MX | Nein | SK6812MINI | Ja | Nein
Altana | MX | Ja | SK6812MINI | Ja | Nein
Suxen | MX | Nein | YS-SK6812MINI | Ja | Ja (*)
Container | MX | Ja | YS-SK6812MINI | Ja | Ja (*)
Choc | KailhLowProfile | Nein | YS-SK6812MINI | Nein | Ja

(*) Bei Verwendung von SOD-123 mit Swen und Container wird aus Platzgründen ein Pad mit dem Durchgangsloch geteilt, sodass die Implementierung etwas schwierig ist.

## Materialbeispiel (Lieferant)

- Platte willkürlich schneiden
    - 2 mm Acrylplatte (Yusha Kobo)
         Es wäre schön, einen Kleber wie 3 mm Acrylquadrat und Acrylbecher zu haben. (Home Center)
    - 3D-Gehäuse (DMM.make)
    - 5mm Pappe (Abholung von diesem Bereich usw.)
- Schaltdiode 1N4148, SOD-123 (TALP-Tastatur)
- SK6812mini, YS-SK6812MINI-E (Yusha Kobo)
- Kailh-Buchse (Yusha Kobo, Talpkeyboard, Kbdfans)
- Urethan-Emaildraht (empfohlen ca. 0,35 bis 0,45 mm. Er ist auch in Heimzentren usw. erhältlich. Vinyldraht ist ebenfalls möglich, aber es ist ziemlich schwierig zu schmelzen.)
- TRRS-Buchse, RESET-Taste (Akizuki Denshi)
- OLED (optional, Yusha Kobo)
- Promicro (Yusha Kobo, TALP-Tastatur)
- Verschiedene Abstandshalter, Schrauben (Herr Hirosugi Keiki, Herr Wilco usw.)
- Schlüsselschalter, Tastenkappe (Yusha Kobo, Talp Keyboard usw., wenn Sie möchten)
- USB-Kabel, TRS-Kabel (3,5 mm, 3-polig)

Andere Werkzeuge wie Temperaturlötkolben, Tester und Pinzette sind erforderlich.

## Pinbelegung

![pcb](./images/PCB.png)

Die Pinbelegungen mit endlosen Möglichkeiten sind:

- C: Horizontale Linie (Spalte)
- R: Vertikale Linie (Reihe)
- DI: LED-Steuersignaleingang (DataIn)
- DO: LED-Steuersignalausgang (DataOut)
- -: Masse (für LED)
- +: VCC (5V für LED)

Das Beispiel auf dem Bild ist Suxen, aber die anderen sind ähnlich.

## Montageverfahren

1. Löten Sie den SK6812mini.
     Verwenden Sie einen Lötkolben mit Temperaturregelung, um bei etwa 220 ° C zu löten.
     Es wird brechen, wenn Sie sich darauf stützen.
     Verwenden Sie Niedertemperaturlot mit einem Schmelzpunkt von 200 ° C oder weniger.
2. Löten Sie die Diode.
3. Setzen Sie den Schalter auf die obere Platte und löten Sie die Schalterbeine auf der Rückseite mit endlosen Möglichkeiten. (Altana, Container ist eine Steckdose)
     Wenn Sie zu diesem Zeitpunkt eine 2-mm-Acrylplatte verwenden, wird empfohlen, ein 3-mm-Acrylquadrat mit Acrylkleber an der Seite des Schalters auf der Rückseite der Platte anzubringen, um ein Ablösen des Schalters zu verhindern.
4. Verdrahten Sie horizontale Linien (Col) und vertikale Linien (Row) entsprechend der Tastenmatrix der Tastatur, die Sie erstellen möchten.
5. Verbinden Sie alle "-" und "+".
6. Verdrahten Sie von DI nach DO in der Reihenfolge, in der die LEDs leuchten sollen. 1. DO → 2. DI → 2. DO → 3. DI…
7. Löten Sie den Schalter TRRS JACK und RESET.
8. Löten Sie die OLED-Buchse.
9. Verdrahten Sie Col und Row, LED (DO), GND und VCC von den Löchern neben einem Pin für endlose Möglichkeiten.
10. Löten Sie den Promicro an die Steckdose.
     (Sie können einen Con-Through verwenden, aber es ist billiger, die gesamte Steckdose auszutauschen, wenn sie kaputt geht.)
11. Erstellen und schreiben Sie eine Firmware nach Ihren Wünschen.
     Firmware ist mit [QMK_Firmware](https://github.com/qmk/qmk_firmware) sehr einfach.
     Referenz: [3 Arten von Mitteln, um die Firmware für Ihre eigene Tastatur vorzubereiten](https://skyhigh-works.hatenablog.com/entry/2018/10/09/120909)

## Verdrahtungsbeispiel

Im Fall der folgenden Anordnung in Suxen ist die Verkabelung beispielsweise wie folgt.
 Da es ziemlich schwierig ist, die Beschichtung auf Urethan-Emaildraht (UEW) zu entfernen, empfehlen wir, die Diodenschenkel für die Verdrahtung zwischen benachbarten Platinen abzuschneiden, da dies weniger wahrscheinlich einen Kurzschluss verursacht.

![pcb](./images/Wired2.png)

### Anmerkungen

- Altana und Container sind Versionen, mit denen Sie den Schalter durch eine Kailh-Buchse ersetzen können.
- Suxen und Container sind mit YS-SK6812MINI kompatibel. Bitte montieren Sie den Fuß ohne LED gemäß der dreieckigen Seide der Leiterplatte.
- Wenn Sie in dem unwahrscheinlichen Fall, dass Sie die LED nicht aufleuchten müssen, einfach Col und Row verkabeln können, um als Tastatur zu fungieren. [Verdrahtungsbeispiel](./images/Wired.png)
- Bei Tastaturen mit Sandwichmontage, die in Japan häufig verwendet werden, sind die obere Platte und die untere Platte mit Abstandshaltern versehen. Bei unbegrenzten Möglichkeiten ist jedoch kein Platz für Abstandshalter zwischen den Tasten vorhanden. Machen Sie ein Schraubenloch an der Außenseite des Schlüssels.
- Wenn Promicro zuerst mit dem "Haus" verlötet wird, kann das Lot aus dem Loch austreten, wenn es zur Seite mit den endlosen Möglichkeiten verdrahtet wird, was zu einem Kurzschluss in den Teilen des Promicro-Hauptgeräts führt.
     Stellen Sie sicher, dass Sie den Promicro zuletzt löten.

## Am Ende

この基板を使ってキーボードを組んだ際にはぜひ[@swan_match](https://twitter.com/swan_match)までご一報ください。

Wir unterstützen dein Endspiel! !!

## Lizenz

https://creativecommons.org/licenses/by/4.0/
