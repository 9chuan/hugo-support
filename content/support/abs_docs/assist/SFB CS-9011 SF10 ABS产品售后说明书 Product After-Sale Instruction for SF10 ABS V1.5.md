## 更新
| ![](media/18adad495b7088a124cf37a2e88efbdd.png) | **客户规范** **Customer Specification**                                                                                                                                                                                                                      |                 |               |
|-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------|---------------|
| SPEC NO.: SFB CS-9011                           | SF10 ABS产品售后说明书  Product After-Sale Instruction for SF10 ABS                                                                                                                                                                                          | SF10 ABS SYSTEM |               |
| Version: V1.5                                   |                                                                                                                                                                                                                                                              |                 |               |
|                                                 |                                                                                                                                                                                                                                                              |                 |               |
|                                                 |                                                                                                                                                                                                                                                              |                 |               |
|                                                 |                                                                                                                                                                                                                                                              |                 |               |
|                                                 |                                                                                                                                                                                                                                                              |                 |               |
| V1.5                                            | Speed of self-check：12km/h to 5km/h                                                                                                                                                                                                                         | 02Jan20         | Matthew       |
| V1.4                                            | Revise chapter 2.3.2.2 and 2.4.2                                                                                                                                                                                                                             | 6Jun19          | Albert Ye     |
| V 1.3                                           | Revise chapter 2.3.2, 2.4 ; DTC list add MCU DTC：C0024, C0032, C0033, C0040, C0041                                                                                                                                                                          | 24Jul18         | Albert Ye     |
| V1.2                                            | Change Figure 1; Chapter 2.3.2 10km/h change to 12km/h                                                                                                                                                                                                       | 11Aug17         | Albert Ye     |
| V 1.1                                           | Change NO. to SFB CS-9011; 2.3.1 add “Attention：Depending on the software, RBLS and FBLS may not need peripheral connection.”; 2.4 add “Attention：For the products settings without brake signal by software, the DTC C0060、C0061、C0062 will not occur.” | 22May17         | Albert Ye     |
| V1.0                                            | 起草 Draft                                                                                                                                                                                                                                                   | 17Feb17         | Albert Ye     |
| **序号/No.**                                    | **修改/Modification**                                                                                                                                                                                                                                        | **日期/Date**   | **作者/Name** |
| 发起 Prepared:                                  | 检查 Checked:                                                                                                                                                                                                                                                | 发布 Released： | Page:1 / 22   |

# 1 应用范围 (Scope of Application)

本文档对宁波赛福SF10系列ABS产品进行了相关介绍说明，并给出了对其维护保养的一些说明。

This document describes some related introduction about Ningbo SF10 series ABS
product, and gives some instructions on its maintenance.

# 2 组成以及系统原理介绍（Components and Principle of the Braking System）

## 2.1 组成(Components)

ABS单元，由液压控制单元(HCU)、电子控制单元(ECU)和电机组成，安装在车架中。在前后轮上分别装有一个车轮轮速传感器。

The ABS unit, installed in the frame, is composed of the hydraulic control unit
(HCU), electronic control unit (ECU) and the motor. The wheel speed sensors are
respectively equipped on the front and rear wheels.

## 2.2 ABS制动系统原理(Principle of the ABS Braking System)

图1 两通道ABS系统原理图

Figure 1 system schematic diagram of two channel ABS

ABS液压系统原理图，如图1所示，除共用一个电机外，它是两个对称并且独立的系统。每个单通道的液压控制系统单元由一个常开阀、一个常闭阀、一个蓄能器、一个回油泵及一个电机组成。

Figure 1 shows the ABS hydraulic system schematic diagram, it has two
independent system, but shares one motor. Every hydraulic control system
composes of a normally open valve, a normally closed valve, an accumulator, a
pump and a motor.

![](media/0da38a3807d699a1408ee26b0238a45c.png)

图2 两通道ABS控制原理简图

Figure 2 control diagram of two channel ABS

两通道ABS控制原理简图，如图2所示，轮速传感器检测车辆轮速信号，并传送给ABS控制单元(ECU)，当车轮趋于抱死时，ECU识别到这个信息，便对制动系统进行控制，调节制动压力，使车轮脱离抱死状态。通过制动手柄/踏板上的轻微跳动可以感觉到这一调节过程。

Figure 2 shows the control diagram of two channel ABS, vehicle wheel speed
signals detected by wheel speed sensors (WSS), and send to ECU. When the wheels
tend to lock, ECU will control the braking system, when identify this
information. We can feel this adjustment process by the mild beating on the
front brake handle or rear footboard.

## 2.3 电气原理(Electrical Principle)

### 2.3.1 电气接线图（Electrical Wiring Diagram）

图3 两通道ABS 电气线路图

Figure 3 electrical circuit diagram of two channel ABS

**注意：后刹车信号和前刹车信号，根据软件配置的不同，可能不需要外围接线。**

**Attention：Depending on the software configuration, RBLS and FBLS may not need
peripheral connection.**

表1 ABS 18pin接线端子定义

Table 1 ABS 18 pin terminal definition

| Pin Number | Definition in Chinese and English |                                  |
|------------|-----------------------------------|----------------------------------|
| 1          | ECU地                             | ECU GND                          |
| 2          | ABS状态切换                       | ABS OFF Switch                   |
| 3          | 前轮速传感器供电                  | Front Wheel Speed Sensor Power   |
| 4          | 前轮速传感器信号                  | Front Wheel Speed Sensor Signal  |
| 5          | 后轮速传感器供电                  | Rear Wheel Speed Sensor Power    |
| 6          | 后轮速传感器信号                  | Rear Wheel Speed Sensor Signal   |
| 7          | K线                               | Diagnostic K Line                |
| 8          | 后轮速输出                        | Rear Wheel Speed Sensor Out-put  |
| 9          | ECU供电                           | Supply valve relays              |
| 10         | 电机地                            | Motor GND                        |
| 11         | 前刹车                            | Front Brake Light Switch         |
| 12         | CAN低线                           | CAN Low                          |
| 13         | CAN高线                           | CAN High                         |
| 14         | 点火                              | Ignition power line              |
| 15         | 后刹车                            | Rear Brake Light Switch          |
| 16         | ABS报警灯                         | ABS Warning Lamp                 |
| 17         | 前轮速输出                        | Front Wheel Speed Sensor Out-put |
| 18         | 电机供电                          | Supply pump motor relays         |

### 2.3.2 报警灯(Warning Lamp)

报警灯的功能：显示ABS是否正常工作。若ABS出现故障，报警灯将会亮起以警示驾驶者。

The function of the warning lamp: Display the ABS is working correctly or not.
If fault occurs, the warning lamp will light up to alert the driver.

当极端行驶情况下前轮和后轮的转速差极大时，例如在表演前轮离地平衡特技或后轮打滑时，再次正常骑行，ABS可能会失效。为了保证ABS功能正常，需停车并关闭点火开关。如果重新启动车辆，车速达到5km/h后，报警灯会自动熄灭，ABS会重新启用。

When the speed of the front and rear wheels difference greatly under extreme
driving conditions, for example, the front wheel off the ground to performance
the balance stunt or rear wheel slip, then ride again normally, the ABS maybe
disabled. In order to assure the ABS function, riders need to stop and close the
ignition switch. If you restart the vehicle, and speed up to 12 km/h, alarm will
automatically put out, ABS is enabled.

为了适应市场的需求，赛福有两种配置的报警灯功能状态。

In order to meet the needs of the market, SAFE Brakes has two types of warning
lamp functions.

#### 2.3.2.1 第一种状态

打开点火开关之后，ABS报警灯亮起，然后在短时间内熄灭。如果ABS报警灯在打开点火开关之后一直亮起，或者在行驶过程中突然亮起，说明在ABS中存在故障。此时ABS无法启用，ABS功能失效。制动系统本身仍起作用，只是ABS调节系统失灵。

After ignition, ABS warning lamp will lit up, and then goes out after a short
period of time. If the ABS lamp is always on after the ignition, or suddenly
light up in the process of driving, these mean that there are faults in the ABS,
the ABS is disabled. But the braking system itself is still working, only the
ABS control system is failed.

#### 2.3.2.2 第二种状态

打开点火开关之后，ABS报警灯亮起，当首次骑行速度大于5km/h时，通过自检后，报警灯熄灭，之后在同一点火周期，若无异常，报警灯保持灭的状态。如果ABS在行驶过程中(≥5km/h)常亮，说明在ABS中存在故障。此时ABS无法启用，ABS功能失效。制动系统本身仍起作用，只是ABS调节系统失灵。

After ignition, ABS warning lamp will lit up, but when the speed is greater than
12kpm in the first cycle, if ABS has passed self-inspection, and lamp will go
out. And then in the same ignition cycle, if there is no abnormality, the lamp
remains off. If the ABS lamp is always on during driving (\> 12km/h), these mean
that there are faults in the ABS, the ABS is disabled. But the braking system
itself is still working, only the ABS control system is failed.

特殊情况说明：

Special circumstances：

1.  点火启动，车辆在没有通过轮速自检的情况下，当出现一个车轮无速度，一个车轮大于5km/h（如架起中撑，驱动后轮转动，前轮不转动），系统立即确定轮速失真1故障，产生DTC，报警灯常亮，ABS失效。之后，若车辆经过停车重新骑行，通过轮速自检，则报警灯熄灭，ABS恢复正常。

    After Ignition , in the case that the vehicle does not pass the wheel speed
    self-check, when one wheel has no speed and the other wheel is quicker than
    12km/h (such as hold up the middle supporting point of vehicle and then
    driving the rear wheel to rotate rather than the front wheel), the system
    immediately determines the wheel speed distortion fault 1and generates DTC,
    the warning lamp stays on at the same time, showing the ABS was failure.
    After that, if the vehicle stops and starts riding again and passes the
    self-check of wheel speed, the warning lamp will be off and the ABS will
    return to normal.

2.  轮速通过自检后，若出现一个轮子无速度，一个轮速大于5km/h的情况，报警灯以200ms的频率闪烁，ABS
    算法猜测轮速异常，期间ABS失效，当该状态持续30s以上，算法确定轮速失真1故障，产生DTC，报警灯常亮。若该状态持续时间小于30s，车辆经过停车重新骑行，若通过轮速自检，则报警灯恢复熄灭，ABS恢复正常。

    If one wheel has no speed and the other wheel is quicker than 12km/h after
    the vehicle pass the self-check of wheel speed. The warning lamp flashes at
    a frequency of 200ms, and the ABS algorithm guesses that the wheel speed is
    abnormal and the ABS is failure. When the state lasts for more than 30s, the
    algorithm determines the wheel speed distortion fault 1 and generates DTC,
    the warning lamp stays on. Let the vehicle stop and start riding again if
    the duration of this state is less than 30s. The warning lamp will be
    restored and the ABS will return to normal when the vehicle passes the
    self-check of wheel speed.

3.  注意，若一个车轮无速度，另一个车轮速度过大（系统设置大于32km/h），系统同时会立即识别为轮速失真2故障，此时，ABS在当前点火周期永久失效。

    Note that if one wheel has no speed and the other wheel has too high speed
    (system setting is greater than 32Km/h), the system will immediately
    identify as wheel speed distortion fault 2. At the same time, ABS will be
    disabled permanently in the current ignition cycle.

备注：ABS自检包含两个阶段，第一阶段为车辆刚上电时的ECU内部电路自检；第二阶段为车辆加速后，前后轮速信号的自检。自检通过，报警灯熄灭。

NOTE: ABS self-check includes two stages. The first stage is the self-check of
ECU internal circuit when the vehicle is powered on. The second stage is the
self-check of the speed signal of front and rear after vehicle acceleration.
Self-check passed and warning lamp light stays off.

### 2.3.3 ABS状态切换开关(ABS State Off Switch)

状态切换开关：将ABS功能禁用或者打开。

State switch: ABS function is disabled or enabled.

进行ABS状态切换，请先确保摩托车一直处于上电状态；且需要在车速低于一定值的时候才可行，建议车辆静止时候进行状态切换。

To change the state of ABS, please ensure that the motorcycle has been on power;
and the speed is lower than a certain value. Doing the state changing when the
motorcycle stops is suggested.

1\. ABS功能从开启到关闭(ABS function from enabled to disabled)

按下车身ABS按钮并保持，3秒后ABS报警灯开始快闪，从灯闪烁开始计时，2s内松开按钮，那么ABS便不工作。当ABS功能关闭时，ABS报警灯慢闪。

Press and hold the ABS button on the vehicle, the ABS lamp start fast blinking
after 3 seconds , timing from the lights blinking, loosen the button within 2
seconds, then the ABS is disabled. When the ABS is disabled, ABS warning lamp
blinks slowly.

2\. ABS功能从关闭到开启(ABS function from disabled to enabled)

操作步骤和上面一样，按下按钮，3秒后ABS报警灯开始快闪，从灯闪烁开始计时，2s内松开按钮，那么ABS便又开始工作，报警灯不再闪烁，一直处于熄灭状态。

Steps as above, press the ABS button, the ABS lamp start fast blinking after 3
seconds , timing from the lights blinking, loosen the button within 2 seconds,
then the ABS is enabled. The warning lamp is no longer blinking, but goes out.

上述1、2条中“从灯闪烁开始计时，2s内松开按钮”，若没有在2s内松开，而是在2s后松开，那么ABS状态切换失败，ABS保持原态，此时重新进行切换即可。

In the above item 1、2,“timing from the lights blinking, loosen the button
within 2 seconds”, without operation within 2 s, but after 2 s, ABS state change
failed, ABS keep the current state, you can change it again.

上述1、2条中“从灯闪烁开始计时，2s内松开按钮”，若一直未松开，27s之后报警灯常亮，此时ABS
功能默认为开启。

In the above item 1、2, “timing from the lights blinking, loosen the button
within 2 seconds”, if no operation for a long time，the warning lamp will lit up
after 27s, and ABS is enabled in this situation.

无论ABS功能是开启或是关闭，断电之后再重新上电，ABS自动变为开启状态。

Regardless of the ABS is enabled or disabled, ABS is enabled automatically after
reigniting the motor.

## 2.4 故障检修(Fault and maintaining)

故障诊断需要在停车状态下进行测试。

The fault diagnosis needs to be tested in the parking condition.

### 2.4.1 诊断仪（Diagnostic apparatus）

维修人员可通过诊断仪，读取ABS的信息，诊断仪的操作界面如下：

The fault diagnosis needs to be tested in the parking condition. Serviceman can
read the information of ABS through the diagnostic apparatus, the operation
interface is as following.

![](media/d29ac8d6395a9e42cad29cb58cc87461.png)

图4 诊断界面

Figure 4 diagnostic interface

该诊断界面可显示当前ABS出现的故障代码(DTC)，DTC故障列表请见附件1。如果**多次诊断后**（操作详见诊断仪使用手册），DTC仍然存在，请按照表2对故障件进行处理。

The diagnostic interface can display the current the failure code (DTC) of ABS,
DTC list shows in attachment 1. If DTC still exist after several times of
diagnosis (details please see “Instructions For SAFE-Brakes ABS Diagnostic
System”), please deal with the failure parts follow the table 2.

### 2.4.2 K线短接地诊断（Diagnosed by Kline short circuits to ground）

可不采用诊断仪，利用K线接地快速诊断故障，说明如下：

Without using diagnostic apparatus，the fault diagnosis can be also made quickly
by the short circuits to ground of Kline , which is explained as follows:

1)
ABS无DTC的状态下，K线接地或长时间接地无反应；ABS有当前DTC，K线接地大于等于5s，报警灯开始依次显示所有当前DTC（取代码后3位）。

When there is no DTC, no response to Kline short circuits to ground; When ABS
has the current DTC, after 5s connection to ground，the lamp starts to display
all the current DTC successively (last 3 bits of the code are taken).

2)
数字0显示时间为1000ms，即报警灯熄灭1000ms；非零数字以300ms的频率闪烁，闪烁次数即为数字大小，如数字3，以300ms的频率闪烁3次。

The display time of number 0 is 1000ms, namely the lamp will be off for 1000ms;
The non-zero number flashes at the frequency of 300ms, and the numbers of
flashing is the number size, such as the number 3 , lamp will flash 3 times at
the frequency of 300ms ;

3)
同一个DTC的数字间隔为1s（期间报警灯常亮）；DTC之间的时间间隔为3s（期间报警灯常亮）；

The time interval of different number in the same DTC is 1 second (the lamp is
always on during the period);The time interval between different DTC is 3s.

4)
ABS有当前DTC，K线接地大于等于5s之后松开，报警灯显示一遍所有当前DTC；K线接地之后不松开，报警灯循环显示所有当前DTC。

When ABS has the current DTC, and release K-line from ground after 5s, the lamp
will display all the current DTC once; If do not release, the lamp will display
all the current DTC circularly.

**举例说明（Examples）:**

1) 诊断一个DTC“C0083”（there is only one DTC- "C0083"）：

K线接地大于等于5s，松开，报警灯端控制机制见下简图。

After K-line short circuits to ground last above 5s ,then disconnect, the
control logic of lamp is shown as the following diagram.

2) 诊断两个 DTC“C0083”、“C0213” (There are two DTC - "C0083", "C0213" ) ：

K线接地大于等于5s，松开，报警灯端控制机制见下简图。

After K-line short circuits to ground last above 5s ,then disconnect, the
control logic of lamp is shown as the following diagram.

表2 故障处理措施

Table2 Fault handling

| **故障类型(failure type)**                            | **DTC**                   | **采取措施(Handling)**                                                                                                                                                                                                                                                                                                          |
|-------------------------------------------------------|---------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 微控制器故障 (MCU Failure)                            | C0024\~C0041              | **ABS 故障**，请咨询供应商后，更换新ABS ABS failure, please replace new ABS after consulting supplier.                                                                                                                                                                                                                          |
| 固态继电器故障 (Solid State Relay Failure)            | C0044\~C0046              | **ABS 故障**，请咨询供应商后，更换新ABS ABS failure, please replace new ABS after consulting supplier.                                                                                                                                                                                                                          |
| 电池电压故障 (The battery voltage Failure)            | C0051\~C0052              | **主要是外围电路故障！** **Mainly peripheral circuit failure!** 检查车辆供电系统(线束连接、保险丝、电瓶，整流器) Check the vehicle power supply system(The fuse, battery, rectifier)                                                                                                                                            |
| 刹车信号故障 (The brake signal failure)               | C0060\~C0062              | **主要是外围电路故障！** **Mainly peripheral circuit failure!** 1.检查刹车二极管是否损坏； Check the brake diode 2.检查刹车信号线和ABS连接情况。 Check the connection between brake line and ABS                                                                                                                                |
| 电机故障(Pump motor fault)                            | C0070、C0071              | **主要是外围电路故障！** **Mainly peripheral circuit failure!** 检查电机供电线 Check the motor power supply line                                                                                                                                                                                                                |
| 电机故障(Pump motor fault)                            | C0072\~C0075              | **ABS 故障**，请咨询供应商后，更换新ABS ABS failure, please replace new ABS after consulting supplier.                                                                                                                                                                                                                          |
| 轮速传感器接线故障 (Wheel speed sensor wiring fault)  | C0080\~C0083 C0100\~C0103 | **主要是外围电路故障！** **Mainly peripheral circuit failure!** 1.检查传感器线束与ABS连接通断情况，若问题未解决，进行下一步； Check the connection between sensor wire and ABS 2.尝试更换轮速传感器。 Try to change the wheel speed sensor.                                                                                     |
| 轮速信号质量故障 (Wheel speed signal quality failure) | C0084\~C0088 C0104\~C0108 | **主要是外围故障！Mainly peripheral failure!** 1.检查前后轮速传感器安装是否规范(传感器头部与齿圈的距离≤1.5mm)； Check the installation of wheel speed sensor(The gap between sensor head and the tone wheel is 1.5 mm or less) 2.检查齿圈是否有变形以或损坏。 Check if there is a deformation , or a damage with the tone wheel |
| 线圈故障 (coil failure)                               | C0120\~C0171              | **ABS故障**，请咨询供应商后，更换新ABS ABS failure, please replace new ABS after consulting supplier.                                                                                                                                                                                                                           |
| 报警灯输出故障 (warning lamp output failure)          | C0210、C0213              | **主要是外围电路故障！Mainly peripheral circuit failure!** 检查仪表盘与ABS连接处线束，若问题未解决，请更换仪表，若问题仍未解决，请咨询供应商 Check the connection between dash board and ABS, if the problem not solved, please change the dash board. If the problem remains unresolved, please consult the supplier.          |
| 轮速输出口故障 (WSS output failure)                   | C0230、C0231              | **主要是外围电路故障！Mainly peripheral circuit failure!** 检查外围电路和仪表，若问题未解决，请咨询供应商后，更换新ABS Check the circuit and dash board, if the problem not solved, please replace new ABS after consulting supplier.                                                                                           |

注意：对于软件配置无刹车信号的产品，将不会出现C0060、C0061、C0062的故障。

Attention：For the products configuration without brake signal by software, the
DTC C0060、C0061、C0062 will not occur.

关于C0084\~ C0088/C0104\~C0108轮速故障的详细说明如下：

| **轮速故障代码** | **解释**                                    | **说明**                                                                                             |
|------------------|---------------------------------------------|------------------------------------------------------------------------------------------------------|
| C0084/C0104      | 轮速传感器信号失真等级01 WSS_Plausibility01 | 低速加速阶段，轮速信号丢失 During the low speed acceleration phase, the wheel speed signal is lost.  |
| C0085/C0105      | 轮速传感器信号失真等级02 WSS_Plausibility02 | 高速加速阶段，轮速信号丢失 During the high speed acceleration phase, the wheel speed signal is lost. |
| C0086/C0106      | 轮速传感器信号失真等级03 WSS_Plausibility03 | 动态轮速信号丢失 Loss of dynamic wheel speed signal.                                                 |
| C0087/C0107      | 轮速传感器信号失真等级04 WSS_Plausibility04 | 前后轮速偏差过大 Excessive deviation in front and rear wheel speed.                                  |
| C0088/C0108      | 轮速传感器信号失真等级05 WSS_Plausibility05 | 轮速信号差 Wheel speed signal is poor.                                                               |

# 3 产品存储、安装更换(Storage, Installation, Replacement)

## 3.1 产品的存储(Storage)

### 3.1.1 存储时间(Storage Time)

**干式**液压单元储存时间：液压单元必须在自制造日期起 6
个月之内填充制动液，否则必须送回制造商处检查。

Storage time (unfilled unit): the hydraulic unit must be filled with brake fluid
within 6 months after its manufacturing date, or it must be sent back to the
manufacturer for checking.

**湿式**液压单元储存时间：3 年后，HCU 必须送回制造商处检查。

Storage time (filled unit): The HU has to be sent back 3 years after its
manufacturing date to the manufacturer for examination.

### 3.1.2 储存温度(Storage temperature)

| 处于一般相对湿度(at an average relative humidity of)                                                                                                              | 60 %                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| 储存全过程温度(for the entire storage)                                                                                                                            | - 20 °C \~ + 50 °C  |
| 此温度下不超过 50 小时 (no more than 50 hours under this temperature)                                                                                             | - 40 °C \~ - 20 °C  |
| 管接口以橡胶件或塑料盖密封时，此温度下不超过50 小时 (For a storage time with port closure via rubber/ plastic caps of max. 50h is valid for temperature range of) | + 50 °C \~ + 100 °C |
| 管接口以胶带密封时，此温度下不超过 50 小时 (For a storage time with port closure via tape of max. 50h is valid for temperature range of)                          | + 50 °C \~ + 80 °C  |

储存条件超出上述条件时，必须咨询供应商。

It is necessary to contact Safe when the storage and shipping conditions are
outside of the specified range above.

## 3.2 产品安装与排气(Installation and Exhaust)

### 3.2.1 安装(Installation)

为了保证油口密封良好，对于端面密封（如图5），请采用力矩扳手安装ABS油管，推荐安装力矩为22±2N·m，每次更换ABS，需要更换垫片。

For end face seal(Figure 5), in order to ensure the hydraulic fluid port
sealing, please install ABS with the torque wrench, recommended installation
torque : 22±2 N·m. Replace the gasket when replace ABS.

![](media/0c05ca4de19bbfc72ddad99e2c1812db.png)

图5 端面密封

Figure 5 End face seal

对于锥面密封（图6），请采用力矩扳手安装ABS油管，推荐安装力矩为15±2
N·m。安装ABS前，请观察与ABS连接的油管蘑菇头是否有变形，若有明显变形，也需要更换油管。

For taper sealing, please install ABS with the torque wrench, recommended
installation torque : 15±2 N·m. Before installation, please check the ABS tubing
mushroom head, replacement of tube is needed with obviously deformation.

![](media/6f333c20e41c7d99a418c3d3042a667b.png)

图6 锥面密封

Figure 6 Taper sealing

已经安装在ABS上的油管，严禁再对油管进行弯折等操作，这样会使ABS连接处的密封面受力不均匀，严重影响ABS的密封性。图6中的一根管路就是错误操作：安装完毕之后，进行了人为弯折。

Has been installed on the ABS tubing, it is strictly prohibited to bend the
tube, this will seriously affect the sealing of ABS with the sealing surface
uneven force. A tube is wrong operation in figure 6.

### 3.2.2 安装后排气(Exhaust)

维修人员在安装ABS完毕后，为了保证ABS正常工作，管路中不能有气体。此时需要借助诊断仪对ABS进行人工排气操作。注意：**请使用厂家推荐型号的制动液，不可混合使用。**

After the installation of ABS, manual exhaust is needed by diagnostic apparatus,
to guarantee the normal work of ABS. **Note: Please use the recommended brake
fluid, mixed usage is banned.**

以下，以前轮ABS系统排气为例，进行说明：

Following is the exhaust procedure of the front braking system:

1.打开上泵制动液盖，加入足量的制动液，打开下泵放油螺栓。

Open the brake fluid cover of the upper pump, add brake fluid, and then open the
oil drain screw on the brake caliper.

2.连接诊断仪，双击![](media/15492a11f053b70e6c61333a07b7a4d3.png)，此时维修人员边捏手刹，边加制动液。手刹频率大概1次/s。该过程持续大概25s。

Connect the diagnostic tool,
double-click![](media/8db1dce90bcbda72beacabc80ce24ecd.png), and the serviceman
should pinch the brake handle while add brake fluid. Braking frequency is about
1 times/s, lasted about 25 s.

3.前轮排气阶段1
执行完毕之后，诊断仪界面会有提示，表明执行完毕。此时，双击![](media/360853ceb5cb5f19d3dcc1ed247d9e05.png)，该过程中维修人员仍然需要边捏手刹，边加制动液。该过程持续大概90s。

After execute the![](media/8db1dce90bcbda72beacabc80ce24ecd.png), there will be
prompt on the diagnosis instrument interface. Keep pinching the brake
handle.Then，double-click ![](media/fc8d7d9fa83a80f8163b4316739ffb0b.png). This
routine lasted about 90 s.

4.前轮排气阶段2执行完毕之后，捏住手柄，关闭下泵放油螺栓。然后，反复捏几次前刹车手柄，感受力度来判断排气是否完毕。

After execute the ![](media/fc8d7d9fa83a80f8163b4316739ffb0b.png), hold the
handle, close the oil drain screw. Then, pinch the brake handle several times,
judge the exhaust by feeling the strength of braking.

**排气注意事项：严禁短时间内重复执行排气程序2次及以上!如需重复执行排气程序，请先等待5分钟，冷却电磁阀，用以保护电磁阀因过热损坏!**

**Attention：It is not allowed to repeat the repair bleeding routines twice
times within a short time! In case of repetition of the entire bleeding routine,
it is absolute necessary to wait a time of 5 minutes to cool the solenoid
valves!**

# 4 ABS制动注意事项（Attentions for Braking）

## 4.1 ABS功能受损(ABS Function Impairment)

若进行改装，例如缩短或延长减震行程、采用其它轮毂、其它轮胎规格、错误的胎压、其它制动摩擦片等。可能使ABS无法继续发挥最佳作用。只有在制动系统上使用经供应商
批准或推荐的备件和轮胎时，才能保证ABS的最佳功能。

\- If the vehicle to be modified, for example, shorten or extend the suspension
travel、using other wheels or wheel hub、wrong tire pressure、other brake lining
and so on. The ABS may cannot be in the best function, except this changes are
approved or recommended by supplier.

## 4.2 ABS系统制动建议(Tips For Braking With ABS)

\- ABS制动的第一条原则：像未配备ABS一样进行制动。

\- The first rule of braking with ABS: brake as though you did not have ABS.

\- 刹车手柄制动时，不要过于迅速猛烈。制动片完全介入后，再大量增加制动压力。

\- Pull the brake lever quickly, but not abruptly. Once the brake pads have fully
engaged, increase the braking pressure quickly.

\- 您可以通过刹车手柄或者脚制动杆的轻微振动以及短暂声音感知到ABS的介入情况。

\- you can feel that the ABS has been on working through a gentle pulsing on the
hand and foot brake levers, as well as a tacking noise.

\- 请勿带档进行完全制动操作。

\- When performing a full braking maneuver, always disengage the clutch at the
same time.

\-
定期在ABS控制范围内练习制动。这使您能够在发生严重事故时充分利用防抱死制动系统的全部潜能。

\- Practice braking in the ABS control range regularly. This will allow you to
use the antilock braking system to its full potential in the event of a serious
incident.

# 附录I 故障代码列表（Appendix I DTC List）

| **DTC** | **Failure Description**                                                                                   |
|---------|-----------------------------------------------------------------------------------------------------------|
| C0024   | MCU_MU_CLK_Monitor_Failed 微控制器时钟检测错误                                                            |
| C0032   | MCU_MC_ROM_Failed 微控制器ROM错误                                                                         |
| C0033   | MCU_MC_RAM_Failed 微控制器RAM错误                                                                         |
| C0040   | MCU RAM Stack Overflow Fault 微控制器RAM堆栈错误                                                          |
| C0041   | MCU Hardware Reset 微控制器硬件复位                                                                       |
| C0044   | Solid State Relay\_ Relay over current 固态继电器_过流                                                    |
| C0045   | Solid State Relay\_ Relay shorted (Stuck on) 固态继电器_继电器短路（卡死）                                |
| C0046   | Solid State Relay\_ shorted to ground 固态继电器_与地短接                                                 |
| C0051   | Battery Voltage \_Battery under-voltage 1 (7V \< Voltage \< 9V)  电池电压过低1，（大于7伏小于9伏）        |
| C0052   | Battery Voltage \_Battery under-voltage 2 (Voltage \<= 7V)  电池电压过低2，（小于等于7伏）                |
| C0053   | Battery Voltage \_Battery over-voltage 电池电压过高                                                       |
| C0060   | Brake Pedal Not Applied with Decel不踩刹车有减速度                                                        |
| C0061   | Brake Pedal Always Applied Without Decel Fault 踩下刹车时没有减速度                                       |
| C0062   | Brake Diode Breakdown 刹车二极管击穿                                                                      |
| C0070   | Pump Motor control\_ Bad connection or Pump supply open or low voltage 泵电机连接差或供电端开路或电压过低 |
| C0071   | Pump Motor control\_ Pump ground open or Motor open 泵电机开路或地线开路                                  |
| C0072   | Pump Motor control_Pump FET shorted 泵电机开关管短路                                                      |
| C0073   | Pump Motor control\_ Pump FET open 泵电机的开关管开路                                                     |
| C0074   | Pump Motor control\_ Pump over current 泵电机过流                                                         |
| C0075   | Pump Motor control\_ Pump motor blocked 泵电机堵转                                                        |
| C0080   | Front_WSS_HSS_Short_To_Battery前轮轮速传感器高端与电源短接                                                |
| C0081   | Front_WSS_LSS_Short_To_Battery前轮轮速传感器低端与电源短接                                                |
| C0082   | Front_WSS_HSS_Short_To_Ground or WSS short circuited 前轮轮速传感器高端接地或短路                         |
| C0083   | Front_WSS_LSS_Short_To_Ground or WSS open  前轮轮速传感器低端接地或开路                                   |
| C0084   | Front\_ WSS_Plausibility01前轮轮速传感器信号失真等级01                                                    |
| C0085   | Front_WSS \_Plausibility02前轮轮速传感器信号失真等级02                                                    |
| C0086   | Front_WSS \_Plausibility03前轮轮速传感器信号失真等级03                                                    |
| C0087   | Front_WSS \_ Plausibility04前轮轮速传感器信号失真等级04                                                   |
| C0088   | Front_WSS \_ Plausibility05前轮轮速传感器信号失真等级05                                                   |
| C0100   | Rear \_WSS_HSS_Short_To_Battery后轮轮速传感器高端与电源短接                                               |
| C0101   | Rear\_ WSS_LSS_Short_To_Battery后轮轮速传感器低端与电源短接                                               |
| C0102   | Rear\_ WSS_HSS_Short_To_Ground or WSS short circuited 后轮轮速传感器高端接地或短路                        |
| C0103   | Rear\_ WSS_LSS_Short_To_Ground or WSS open 后轮轮速传感器低端接地或开路                                   |
| C0104   | Rear\_ WSS_Plausibility01后轮轮速传感器信号失真等级01                                                     |
| C0105   | Rear\_ WSS \_Plausibility02后轮轮速传感器信号失真等级02                                                   |
| C0106   | Rear\_ WSS \_Plausibility03后轮轮速传感器信号失真等级03                                                   |
| C0107   | Rear\_ WSS \_ Plausibility04后轮轮速传感器信号失真等级04                                                  |
| C0108   | Rear\_ WSS \_ Plausibility05后轮轮速传感器信号失真等级05                                                  |
| C0120   | Front \_NO Coils Short to battery 前轮常开线圈接电源                                                      |
| C0121   | Front\_ NO Coils Short to ground or Open solenoid 前轮常开线圈接地或开路                                  |
| C0130   | Front\_ NC Coils Short to battery 前轮常闭线圈接电源                                                      |
| C0131   | Front\_ NC Coils Short to ground or Open solenoid 前轮常闭线圈接地或开路                                  |
| C0160   | Rear\_ NO Coils Short to battery 后轮常开线圈接电源                                                       |
| C0161   | Rear\_ NO Coils Short to ground or Open solenoid后轮常开线圈接地或开路                                    |
| C0170   | Rear\_ NC Coils Short to battery后轮常闭线圈接电源                                                        |
| C0171   | Rear\_ NC Coils Short to ground or Open solenoid后轮常闭线圈接地或开路                                    |
| C0210   | Warning Lamp output\_ Short to battery 报警灯输出与电源短路                                               |
| C0213   | Warning Lamp output\_ Short to ground or open报警灯输出与地短路或开路                                     |
| C0230   | Vehicle speed output\_ Short to ground 车速输出口与地短路                                                 |
| C0231   | Vehicle speed output\_ Short to battery 车速输出口与电源短路                                              |
