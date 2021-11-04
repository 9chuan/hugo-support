---
title: SFB CS-9006 SF10 ABS线束安装规范
linktitle: SFB CS-9006 SF10 ABS线束安装规范
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## 更新

V1.6  修改第8节第3条关于地线接线的描述  12/ April/19  Albert Ye<br/>V1.5  修改SF10 电路接线功能图  6/Mar/18  Albert Ye <br/>V1.4  修改SF10 电路接线功能图  23/Jun/17  Albert Ye <br/>V1.3  修改文档名称，页眉页脚，文档编号，Update  22/May/17  Zhang Zhong <br/>V1.2  修改电路接线功能图，更新 Update  06/Aug/16  Zhang Zhong <br/>V1.1  更新 Update  11/Jul/16  Zhang Zhong  <br/>V1.0  起草 Draft  14/Mar/15  Taylor Wang





# Product and Application Purpose产品适用范围

Purpose of this document is to set out for the customer information and
requirements for what, according to our opinion, may be considered a proper and
correct wiring harness installation. Please note that SFB does not assume any
liability for the information/recommendations set out herein and that
responsibility for securing the tightness and the proper installation of the
wiring harness solely rests with the customer.

本文以用户需求的信息为目的，阐述了我们认为的合适的和正确的线束安装要求。请注意宁波赛福在此不承担任何关于信息/建议的责任，并且对于线束的牢固性和线束安装的正确性，相关责任仅由用户本身承担。

The ABS wiring harness has the task of electrical connection of the ABS
components. Special attention should be given to the arrangements of the wheel
speed sensors , the recommendation to EMC and waterproof requirement.

ABS线束的主要作用是用来连接ABS的电气部件，需要特别注意轮速度传感器的安装，对EMC的建议和防水要求。

# Environmental Conditions环境条件

The wiring harness should meet/exceed the minimum requirements which are
specified in the Technical Customer Document latest version.

线束必须符合或高于在客户技术文档最新版本中说明的最低使用环境要求。

# The choose of the wire gauges导线规格选择

根据车身线束一般要求以及ABS电气特性，选择导线规格。对于一般电源信号和比较强的，不易受干扰的信号，可选择普通导线，例如ECU供电线，电机供电线。对于弱信号电路和易受干扰的信号电路，建议选用双绞线或屏蔽线，例如can线，轮速信号线。在导线规格确定后，包括考虑附加阻值（如接触电阻），检测实际压降及发热，确保在所有工况下满足ABS工作要求。

According to the body harness general requirements and the characteristics of
ABS electric, we select wire gauge. As to the common power signal and relatively
strong signal, not easy to be influenced by interference signal, we can choose
ordinary wire, such as, the ECU power supply wire and motor power supply wire.
As to the weak signal circuit and the circuit easily to be influenced, twisted
pair or shielded wire are suggested, such as, CAN line, wheel speed line. After
the determination of the wire specifications, including the consideration of
additional resistance (contact resistance), to detect the actual pressure drop
and heat, make sure that it meets the requirements of ABS work under all
conditions.

**The critical current valve during ABS operation ABS工作时关键线路电流值：**

| Pin No. pin号 | Describe描述                                                             | Current电流 (at 13.5V，23℃) |
|---------------|--------------------------------------------------------------------------|-----------------------------|
| 10，18        | ground and power for pump motor 为泵马达提供地线和电源                   | 2A to 20A                   |
| 1，9          | ground and power for solenoid valves and ECU 为电磁阀和ECU提供地线和电源 | 3A to 14A                   |
| 14            | Ignition for ECU 为ECU提供点火信号                                       | ＜1A                        |
| 3，4          | Power and signal for front wheel speed sensor 前轮速传感器供电和信号     | 5.9mA to16.8mA              |
| 5，6          | Power and signal for rear wheel speed sensor 后轮速传感器供电和信号      | 5.9mA to16.8mA              |

Unless otherwise specified, the ECU remains operative with leakage
resistancesof≥200kΩto power or ground alternatively at each wire within supply
voltage range. For more, the wheel speed sensor power supply and signal lines is
≥230 Ω to ground, ≥280 Ω to power; Diagnosis of k line is ≥1 kΩ to ignition;
Diagnosis of K line, ignition line, warning lamp line, brake line, ABS
switch-off line of is ≥100 kΩ to ground.

除非另有规定，在供电电压范围内，每条导线对地或对电源的泄露电阻≥200kΩ。其中轮速传感器供电及信号线对地大于230Ω，对电源大于280Ω；诊断k线对点火线大于1
kΩ；诊断K线，点火线，报警灯线，刹车信号线，ABS切换开关线对地大于100 kΩ。

# Wheel Speed Sensor Wiring轮速传感器布线

These two wires must be twisted with a length l = 40 - 58 mm per one twist.

两根线采用双绞线并且每一个绞距长度要达到40-58mm。

Due to the high requirements of this connection (speed sensor - ECU) it is
proposed to use only high quality material suppliers. If there are problems with
the EMC on the wheel speed sensor wire (e.g high interference) the application
of a twisted wire with an additional shield is recommended. The shield is
separately connected to ground. Deviations from this recommendation are still
possible, but should be agreed by SFB.

由于轮速传感器连接到ECU对接口有较高的要求，为了保证产品质量建议采用高品质材料供应商。如果轮速传感器线出现电磁干扰问题（如：强干扰），建议使用附加屏蔽功能的双绞线。屏蔽线单独接地。采用与此建议不同的方法也可以，但是必须征得宁波赛福同意。

# CAN Wiring CAN布线

For the CAN wiring it is recommended to use also a twisted pair with a length l
= 40 - 58 mm per one twist. If there are any problems with the EMC the use of a
twisted wire with an additional shield is recommended. The shield is separately
connected to ground.

对于CAN线建议采用双绞线并且每个绞距长度为40-58mm。如果出现电磁干扰问题，建议使用带屏蔽功能的双绞线，屏蔽线单独接地。

# Warning Lamp报警灯

To fulfill the requirements of ECE R78 in regards to the actuation of the
warning lamp, an active warning lamp is mandatory.

根据ECE R78中关于报警灯运行的要求，主动式报警灯是强制性的。

The mean of the active warming lamp：In case of broken warming lamp wire or loss
of ECU power supply circuit which lead to ABS not work, the warning lamps can be
actuated.

主动式报警灯用意：当报警灯线损坏或者ECU供电线路丢失导致ABS不工作时，报警灯能够激活亮起。

The warning lamps can be hard wired or also actuated via CAN. This depends on
the customer layout of the wiring and actuating of the warning lamps.

报警灯可以是硬件驱动或者通过CAN通讯驱动。这取决于用户的布线和报警灯的驱动方式。

# EMC Recommendations EMC的建议

These are general recommendations depending on the different locations of the
components and wiring in the car.

这些是根据部件安装位置和布线位置不同而定的一般性建议。

—wheel speed sensor wires and power cable routing don’t at the same side of the
car .

轮速传感器线束与电源电缆路线不要在车身同一侧

—do not route the wheel speed sensor wires in parallel to high tension wires
(ignition cables), a minimum distance of more than 10 cm is necessary

不要将轮速传感器的线与高压线（点火线）并行，最小距离必须大于10cm

—the wire from ECU to battery should be as short as possible

从ECU到电池的线要尽可能短。

—ECU ground as short as possible fixed directly to battery ground

ECU的地线要尽可能短地直接接到电池地

—avoid loops in the routing

避免安装线路上存在回环

—avoid wires which are not in use for the system interference for the ABS wiring
harness

避免没有被系统使用到的线对ABS线束产生干扰

—diagnostic wires as short as possible and place the diagnostic connector as
close as possible to the ABS unit

诊断线尽可能短，且诊断连接器尽可能靠近ABS单元放置

—if the wiring harness routing is changed the EMC-tests should be performed
again

如果线束的路线改变了，那么需要重新进行电磁兼容性测试。

— CAN wires with high frequency are important to keep resistance (e.g. 120 Ohm)
in general.

通常，高频CAN线保持120Ohm恒定电阻非常重要。

—if additional support is needed, please contact SFB

如果需要其他帮助，请联系宁波赛福。

# Wiring Layout线束布置

**1)** The ABS wiring harness should be routed away from the engine control
module and other electronic modules. All attempts should be made to maintain as
much distance as possible between the ABS harness and other conductive wiring.
If a common layout with other wiring harness is planned, it is recommended to
contact SFB.

ABS的线束应该远离引擎控制模块和其他电气模块。尽量确保ABS线束与其他导电线保持足够的距离。如果需要和其他线束一起布置，请联系宁波赛福。

**2)** The power leads 9 and 18 must be connected directly to the battery itself
to minimize a voltage drop created by other electric or electronic devices. It
is not allowed to create one common power line and splice this for ABS and other
high current consumers.If a different connection becomes necessary a separate
voltage drop calculation should be made. This can also be done by SFB when all
harness information like cross section and cable length is available.

电源线9和线18必须分别直接连接到电池，以减小由其他电器和电子设备引起的压降。不允许共用一条电源线将ABS和其他大电流设备连接。如果必须采用不同的连接方式，那么必须进行单独压降计算。当线束规格如线径和线长已知时，计算可由宁波赛福完成。

**3)** The connection of wire 10 (ground wire recirculation pump) and wire 1
(ground wire ECU and solenoid valves) must be respectively connected to the
battery terminal or vehicle body directly，and the ends must be connected
together. Similar to the power supply also the ground must have its own ground
stud. It is also not allowed to splice different consumers with one common
ground wire. This could create an additional ground shift for the ABS system.

线10（电机泵地线）和线1（ECU和电磁阀地线）不可共线，线端必须连接到一起，接到车体或者电池负极接线柱。与电源供电线一样，地线必须有独立的接线柱。禁止将不同设备的地线连接在一起。这将对ABS系统产生附加的地移。

**4)** The wheel speed sensor wiring and the brake light switch wire may not be
guided in parallel to high voltage wiring (e.g. ignition cable). In case of
crossing a minimum distance of d \> 10 cm is required. Avoid proximity to fuel
injectors, PWM lines or high power ignition/battery wiring, even for short
distance. In order to make proper detection, even in case of failure, extra
screening measures are necessary. In any case, EMC test is necessary for other
internal devices.

轮速传感器线和刹车灯开关线不能与高压线并行（如点火线）。要求最少有10厘米的距离。避免靠近喷油嘴、PWM线或者大功率点火线/电池线，就算短距离也不可以。为了做出适当的检测，避免故障，需要进行屏蔽测试。无论如何，需要对其他设备进行ECM测试。

**5)** The ABS transmits/receives different CAN messages from other ECU\`s (e.g.
Motronic/engine controller...). To prevent failures due to different voltage
levels and switch ON/OFF behavior it is recommended to use the same power supply
and ground level for the different ECU\`s.

ABS从其他的ECU（如引擎/发动机控制器）发送/接收不同的CAN信号。为了防止由于不同电压等级和开关行为造成的故障，建议对不同的ECU采用同样的电源和接地线。

**6)** No fuse must be installed between terminal 14( ignition ) and ABS warning
lamp, because if the fuse is blown an ABS failure cannot be detected. Deviations
require the approval of SFB, (e.g. other lamps are fused together so that a
blown fuse can be indicated immediately to the driver).

在14针脚（点火）和ABS 报警灯之间不能安装保险丝，因为一旦保险丝熔断，
ABS的故障就不能被检测到。不同的要求需要得到宁波赛福的批准（如所有报警灯的保险丝共用，这样保险丝的熔断可以直接提示驾驶员）。

**7)** SFB recommends fuses for the following wires:

宁波赛福建议为以下线路安装保险丝：

no. 18 (between battery and motor power supply) 15 A (T.B.D)

18号线（在电源与电机供电之间）15A（待定）

no. 9 (between battery and ECU power supply) 10 A (T.B.D)

9号线（在电源与ECU供电之间）10A（待定）

no. 14 (between battery and ignition key) 1A

14号线（在电源与点火钥匙之间）1A

These fuses are necessary to fulfill the requirements of failure mode effect
analyses (FMEA) to avoid overheating of the wiring harness in case of a short
circuit.

这些保险丝必须满足故障失效分析（FMEA）以避免线束过热引起短路。

The value of the fuse in wire 18 depends also on the environmental conditions of
temperature and applied pressure at the master cylinder during an ABS
actuation.This value is a first assumption of SFB and depends on the ABSpump
motor characteristics and can be changed after approved by SFB.

线18保险丝的值也取决于在ABS动作状态下的环境温度和作用于主缸上的压力。这个值是宁波赛福的一种假定，它取决于ABS的泵马达特性。其值经宁波赛福允许后可以更改。

The use of fusible links is not allowed, because the blow characteristic of this
device is very different.

不允许使用熔丝连接，因为它的熔断特性都不相同。

1.  In order to distinguish between front signal and rear signal，brake cable
    must increase diode. These diode are necessary to fulfill the requirements
    of failure mode effect analyses (FMEA) to avoid diode broken down.

    Attention：Brake cable is not required, and Brake cable has been cancelled
    in some vehicle.

    为了区分前后刹车信号，刹车线回路增加二极管，这些二极管需要满足故障失效分析（FMEA），以防止击穿损坏。

    注意：刹车线回路属于可选电路，有些车型已经取消刹车线回路。

    **9)** The voltage level at the terminal power supply (pin 14) for ECU, pump
    motor (pin 18) and solenoid valves (pin 9) must be in all cases \> 10V to
    prevent any undervoltage shut off in any situations.

    在任何情况下，ECU点火（14针脚）、泵马达（18针脚）和电磁阀（9针脚）端子的压必须大于10V，以防止出现欠电压关闭的情况。

# Fixing of the wiring harness线束的固定

Due to the mechanical stress and vibration of the wiring harness and the
modulator the wiring harness must be fixed at least 200mm to 400mm after the
18-pin connector. SFB recommends to fix the wiring harness directly at the
hydraulic control unit in a way that the wiring harness is fixed at the moving
element, e.g. hydraulic control unit. With this solution it is prevented that
the terminals in the 18-pin connectors are not damaged.

由于机械应力、线束震动和调解器等原因，线束必须被固定在离18针连接器至少200mm至400mm的地方。宁波赛福建议把线束直接固定在液压控制单元上，从某种程度上说就是固定在移动单元上。例如：液压控制单元。这种方法可以防止18针连接器上的端子损坏。

# Sealing Requirements密封性要求

It is possible that a lower pressure is created when the hot unit and connector
is cooled down when the ABS unit is splashed by water or immerse into water.
This can cause water to be soaked via the wire ends e.g. ground wires into the
connector. This means that all wires, which end in a wet or splash water area
must be protected that no water can penetrate into the wire and through the wire
into the connector. The sealing of these wire ends is required. The same
requirement is also valid for splices which are installed in wet or splash water
area.If this requirements cannot be fulfilled the system can fail due to
corrosion in the ECU connector.

当ABS组件被溅上水或者浸入水中时，热的元件和连接器会被冷却下来，此时内部气压会降低。这可能会导致水通过线端渗入连接器。所有处在潮湿环境或者有可能溅到水的线束连接端必须被保护起来，以防止水浸入线束或者通过线束渗入连接器。因此，所有线束连接端必须密封。这个要求同样适用于安装在潮湿环境或可能被水溅到区域的接合点。如果不满足这项要求，系统将因ECU连接器的腐蚀而不正常工作。

**Interface validation接口验证：**

The validation of the connector/header interface is the responsibility of the
wiring harness connector supplier.

线束连接器供应商有责任对连接器/插头进行验证。

SFB supports this activities by providing housings for validation.

宁波赛福会提供外壳给供应商进行验证。

**Water tightness for the wiring harness线束的防水性：**

Water tightness is one of important requirementsto be met when designing a
harness.It is also within the wiring harness suppliers responsibility to check
it.

当设计线束时，线束防水性是其中重要的要求之一，线束供应商的有责任验证防水性能。

**The wiring routing recommendations排线建议：**

Due to the effects of gravity passing water through the wires the ECU should be
packaged higher than any wire end or splice in the harness.

由于水会因重力原因沿着线束流下，所以ECU应该布置在线束的端部和连接处上方。

Measures should be taken to prevent water from collecting around the wiring
harness.

应采取有效措施防止在线束周围积水。

Plastic wire covering/protection should allow water to drain from harness.

线的覆盖/保护必须可以让水从线束表面流走。

Wiring should be routed away from water drainage areas.

排线布置须远离排水区域。

Wires that are routed around sharp edges or that can be damaged from impact
should be protected.

处在锋利边缘或可能受到硬物冲击损坏的线束应该被保护起来。

Water in the wiring harness can cause interference on various signal wires, e.g.
PWM-signal interference with wheel speed sensor wires due to poor wiring
insulation. Wires splices and ground eyelets must be located away from direct
contact with high pressure cleaner.

在线束中的水能够对各种信号线产生干扰，例如：由于线束的绝缘不良导致PWM信号干扰轮速传感器线束信号。线束连接点和表面孔眼必须放置在远离直接接触高压冲洗的位置。

Any wire end terminating in a splash water area should be orientated so that the
wire end is pointing down.

任何在溅水区域的线端都应该端部朝下布置。

**Connector Precautions连接器防护措施：**

During the OEM assembly process care must be taken that no water/ fluid /
foreign materials can enter an open connector (male or female).

在OEM装配过程中必须防止水/液体/外部物质进入未封装的连接器（公头或者母头）。

The assembly plant must ensure that connector is fully engaged and slider or
lever is in locked position.

在装配中必须确保连接器安装到位且处于锁定位置。

Terminal wire seals must be of correct size and installed properly.

线束端部密封必须尺寸正确且安装适当。

Seal plugs must be installed in all open cavities

所有空孔必须安装密封塞。

Terminal wire crimps must meet manufactures strength requirements.

线缆压接的末端必须满足强度要求。

# The function diagram of ABS circuit wiring电路接线功能图

The following wiring diagram is SFB’s minimum request of the vehicle wiring
interface. Any deviations from this wiring diagram should be clearly
communicated to SFB.

如下接线图1是宁波赛福对于车身线路接线的最低要求，任何对于接线图的改动都需要向宁波赛福交流明确。

![](media/d9b09b70c0997fca85669a8473351bed.png)

图1 SF10 ABS电路接线功能图
