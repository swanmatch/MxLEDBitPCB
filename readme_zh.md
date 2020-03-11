# 无限的可能性

修改了[Cherry-Mx-Bitboard](https://github.com/ogatatsu/Cherry-Mx-Bitboard) ，使SK6812mini沉迷于螺旋线。

自制键盘的印刷电路板，其中一块板对应一个开关。 ![印刷电路板](pcbs.jpg)

使用此板子，无需设计板子，就可以创建具有原始布局的全色背光键盘。

例如...！

![例子](https://cdn-ak.f.st-hatena.com/images/fotolife/s/swan_match/20180915/20180915184339.jpg)

[单击此处了解](https://swan-match.hatenablog.com/entry/2018/09/15/184923)详细信息。

另外，我们公开了[如何制造顶板](https://swanmatch.github.io/topplate-tips) 。

[英文](https://translate.google.com/translate?hl=ja&sl=auto&tl=en&u=https%3A%2F%2Fswanmatch.github.io%2FMxLEDBitPCB%2F&sandbox=1)

## 无限可能性系列

### 宝微之家

可以取出的ProMicro引脚，以及OLED，复位开关，分离式键盘的TRRS和用于安装的M2螺孔。
 TRRS引脚分配与Helix兼容。

### 连结

除非断开原来的25个键，否则Col和Row以及垂直VCC和GND不需要布线。

当然，即使分开也可以使用。

### Altana

像Nexus这样的预接线版本，以及带有Kailh插座的可切换版本。

## 物料示例（供应商）

- 任意切板
    - 2mm压克力板（Yusha工作室）
        最好使用3mm丙烯酸木材和丙烯酸圣代等粘合剂。 （居家中心）
    - 3D外壳（DMM.make）
    - 5毫米纸板（例如从那里捡起）
- 开关二极管1N4148（TALP键盘）
- SK6812mini（Yusha工作室）
- 氨基甲酸酯漆包线（推荐为0.35至0.45mm。也可在家居装饰商店购买。可以使用乙烯基线，但会熔化或变得非常困难）
- TRRS插孔，RESET按钮（秋月电机先生）
- OLED（可选，Yusha Kobo）
- Promicro（Yusha Kobo，TALP键盘）
- 各种垫片和螺丝（Hirosugi Keiki，Wilco等）
- 按键开关，键帽（Yusha Kobo，TalpKeyboard等，根据您的偏好）
- USB电缆，TRS（3.5mm3极）电缆

此外，还需要诸如温度控制烙铁，测试仪和镊子之类的工具。

## 引脚分配

![印刷电路板](pcb1.png)

无限可能性的引脚图是：

- C：水平线（Col）
- R：垂直线（行）
- DI：LED控制信号输入（DataIn）
- DO：LED控制信号输出（DataOUT）
- -：接地（用于LED）
- +：VCC（LED为5V）

## 组装程序

1. 焊锡SK6812mini。
    使用可调温烙铁在约220°C的温度下焊接。
    如果卡住，它将破裂。
    使用熔点为200°C或更低的低温焊料。
2. 焊接二极管。
3. 将开关放在顶板上，并在背面焊接开关脚，可能性无限。
     （Altana是插座。）如果此时使用2mm的丙烯酸板，最好用丙烯酸粘合剂将3mm的丙烯酸材料附着在板背面的开关侧，以防止开关脱落。
4. 根据要组装的键盘的键矩阵连接水平线（Col）和垂直线（Row）。
5. 连接所有的“-”和“ +”。
6. 按照您希望LED发光的顺序，将菊花链从DI连接到DO。第一DO→第二DI→第二DO→第三DI…
7. 焊接TRRSJACK和RESET开关。
8. 焊接OLED插座。
9. 将孔和行，LED（DO），GND，VCC布线到任意引脚旁边的孔中，以实现每种无限可能。
10. 将Promicro焊接到插座上。
     （尽管您可以使用con through，但是如果整个套接字损坏了，则更换整个套接字要便宜一些。）
11. 根据您的喜好创建并写入固件。
    使用[QMK_Firmware](https://github.com/qmk/qmk_firmware)固件非常简单。
    参考： [为您自己的键盘准备固件的三种方法](https://skyhigh-works.hatenablog.com/entry/2018/10/09/120909)

## 接线实例

例如，如果您有一个3 * 3的栅格阵列，接线将如下。
 （如果不断开Nexus Altana的连接，则无需在板之间进行Col，Row，垂直VCC和GND的布线。）
聚氨酯漆包线（UEW）很难剥离薄膜，因此，短路可能性很小的相邻板之间的布线可能是切断的二极管脚。
 LED从右上方螺旋式布线。

![印刷电路板](pcb9.png)

### 注意事项

- Nexus Altana自2019年4月起开始流通，已连接Col，Row和垂直电源线（VCC，GND）。
- Altana是允许您使用Kailh插槽更换交换机的版本。
- 如果您不需要完全照亮LED，只需为Col和Row接线，它将用作键盘。
- 在日本广泛使用的三明治式键盘的情况下，顶板和底板上都装有垫片，但按键之间没有空间，因此可能性无限。在钥匙的外侧提供一个螺丝孔。
- 如果您先将Promicro焊料焊接到“家”，则在连接到无限可能性时，焊料可能会从Promicro本体的孔和短路部件漏出。
     Promicro应该最后焊接。

## 最后

如果您使用此板来构建键盘，请通过[@swan_match](https://twitter.com/swan_match)告诉我们。

我支持您的EndGame！ ！

## 执照

https://creativecommons.org/licenses/by/4.0/
