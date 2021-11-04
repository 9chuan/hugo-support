---
title: SFB CS-9013 SF10 ABS报警灯及轮速输出电路特性 
linktitle: SFB CS-9013 SF10 ABS报警灯及轮速输出电路特性 
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

##更新
| ![](media/18adad495b7088a124cf37a2e88efbdd.png) | **客户规范** **Customer Specification**                                                                   |                 |               |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------|-----------------|---------------|
| SPEC NO. :SFB CS-9013                           | SF10 ABS报警灯及轮速输出电路特性  SF10 ABS Warning Lamp and Wheel Speed Output Circuit Characteristics    | SF10 ABS System |               |
| Version: V1.4                                   |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
|                                                 |                                                                                                           |                 |               |
| V1.4                                            | Add clause 5 about requirement of Wheel speed output circuit                                              | 21/Jun/17       | Albert Ye     |
| V1.3                                            | SPEC NO. change to SFB CS-9013                                                                            | 22/May/17       | Albert Ye     |
| V1.2:                                           | Add clause 4 about the requirement of V_WL voltage for Warning Lamp; -add clause 1 about the WSSout_ctrl. | 17/Nov/16       |  Rich Chen    |
| V1.1                                            | Add English translation                                                                                   | 28/Jan/16       | Albert Ye     |
| V1.0                                            | 起草 Draft                                                                                                | 27/Sep/15       | Albert Ye     |
| **版本/Ver.**                                   | **修改/Modification**                                                                                     | **日期/Date**   | **作者/Name** |
| 发起 Prepared:                                  | 检查 Checked:                                                                                             | 发布 Released： | Page:1 / 4    |

# **1.ABS报警灯电路 (**ABS Warning Lamp circuit)

## 1.1 ABS ECU内部电路描述及要求(The internal circuit description and requirements of ECU)

![](media/20381f87592c71571c25c9cb97e6b0e6.emf)

图1 ECU内部报警灯电路

Figure1 The internal warning lamp circuit of ECU

ABS Warning
Lamp端接入报警灯外部电路，赛福提供电路输出特性及要求，整车厂设计电路。

要求及说明：

1.当WL_ctrl控制A、B点导通时，报警灯灭；当WL_ctrl控制A、B点关断时，报警灯亮。

2\. ABS Warning Lamp端的导通电阻为100欧姆，即RR10。

3\. A到B的最大允许电流100mA。

4\. 当WL_ctrl控制A、B点断开时，V_WL处最小电压需要达到3V。

The ABS Warning Lamp port need to be connected to the external warning lamp
circuit. SFB should provide internal circuit output characteristics and
requirements, while the customers need to design an external circuit.

Requirements and instructions of internal circuit:

1\. When A to B is connected by the control of WL_ctrl，the external warning lamp
goes out；While A to B is disconnected by the control of WL_ctrl，the external
warning lamp goes on.

2\. The on-resistance of ABS Warning Lamp port is 100Ω (RR10).

3\. The Max current from A to B should be under 100mA.

4\. When A to B is disconnected by the control of WL_ctrl, the min voltage at the
place of V_WL should be 3V.

# **2 AB**S轮速输出电路(Wheel speed output circuit)

## 2.1 ABS ECU内部电路描述及要求(The internal circuit description and requirements of ECU)

![](media/829e1714b09831543525aab7389a5061.emf)

图2 ECU内部轮速输出电路

Figure1 The internal wheel speed output circuit of ECU

WSSout端接入轮速输出外部电路，赛福提供电路输出特性及要求，整车厂设计电路。

要求及说明：

1\. WSSout_ctrl根据轮速传感器的信号进行通断控制，为仪表盘产生脉冲信号。

2.
ECU提供前轮速（17口）和后轮速（8口）输出口，从哪一路输出到仪表盘由整车厂确定。

3\. WSSout端的导通电阻为100欧姆，即SR7（17口）或者SR8（8口）。

4\. A到B的最大允许电流50mA。

5.
图2中的12V由ECU内部提供。但在某些情形下，由于安全机制的参与控制，会出现该点电压大幅降低的情况，所以还需要外部增加一个上拉电阻（推荐10K）接到12V（详见700003
SF10 ABS电路接线功能图），保证轮速输出信号的质量。

The WSSout port need to be connected to the external wheel speed output circuit.
SFB should provide internal circuit output characteristics and requirements,
while the customers need to design an external circuit.

Requirements and instructions of internal circuit:

1\. WSSout_ctrl is the on-off control according to the discretion of the wheel
speed sensor signal, then product the pulse signal for the dashboard.

2\. ECU provides the front wheel speed output port (port 17) and the rear wheel
speed output port (port 8), customers decide which port to use.

3\. The on-resistance of WSSout port is 100Ω. (SR7 or SR8 )

4\. The Max current from A to B should be under 50mA.

5\. The 12V in Figure 2 is provided internally by ECU, but in some cases, under
the control of security mechanism, there may be a dramatic drop with this point
voltage. So in order to get the high quality speed output signal, another
pull-up resistor (recommend 10K) to 12V is needed in the peripheral circuit.
（More details in “The Function Diagram of SF10 ABS Circuit Wiring” 700003）
