---
title: SFB CS-9001 SF10 ABS客户技术文档
linktitle: SFB CS-9001 SF10 ABS客户技术文档
summary: "阐明SF10 ABS对客户相关技术需求"
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## 更新记录
| ![](media/18adad495b7088a124cf37a2e88efbdd.png) | **客户规范** **Customer Specification**                      |                 |                         |
| ----------------------------------------------- | ------------------------------------------------------------ | --------------- | ----------------------- |
| SPEC NO. : SFB CS-9001                          | SF10 ABS 客户技术文档 SF10 ABS Technical Customer Documentation | SF10 ABS System |                         |
| Version: V1.4                                   |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
|                                                 |                                                              |                 |                         |
| V1.4                                            | 修改8.2.1.1表格中“60minutes”对应温度。                       | 2/Jan/20        | Matthew                 |
| V1.3                                            | 4.3节修改原理图；7.1节，修改最大许可工作压力，20MPa改为25MPa；修改8.1.7节和8.2.1节参数 | 15/Aug/17       | Albert Ye               |
| V1.2                                            | Change Spec NO.to SFB CS-9001                                | 22/May/17       | Albert Ye               |
| V1.1                                            | 修改试验参数&加入英文 Modify test Parameters & Add English translation | 22/Jul/16       | Albert Ye               |
| V1.0                                            | 起草 Draft                                                   | 10/Aug/15       | Taylor Wang & Albert Ye |


# 1 重要信息（Important Information）

1.  客户不得对EHCU(电控单元和液压控制单元)进行维修和更改；

Customer can’t repair and change the EHCU (electronic control unit and hydraulic
control unit);

1.  客户需保证在液压制动系统加注完成后，制动系统内不得存在任何气体；

    After filling in the hydraulic brake system, customer should guarantee that
    there are no any gas in the brake system.

2.  未经许可，客户不得更改与 ABS（防抱死制动系统）性能有关的系统零部件和软件；

    Without permission, customer can’t change components and software related to
    the performance of ABS (Anti-lock Brake System) system.

3.  电控单元的输出信号应按照宁波赛福接口定义使用，未经同意使用所引起的问题，宁波赛福对此不负相关责任；

    The output signal of electronic control unit (ECU) should be used according
    to the interface definition of Ning Bo Safe, and Ning Bo Safe will take no
    responsible for the problem caused by usage without permission.

4.  电控单元损坏时，输出信号不可用；

    The output signal is unavailable when the ECU is breakdown.

5.  液压单元在跌落后不可继续使用。任何和本标准有差别的规范，需与宁波赛福达成一致意见。

    The hydraulic control unit (HCU) must not be used after it has been
    dropped.Any discrimination with this standard specification should reach
    consensus with NingBo Safe.

# 2 引言（Foreword）

## 2.1 定义（Definition）

第一回路：制动主缸到制动轮缸部分。

Primary circuit: the parts of brake master cylinder to the brake wheel cylinder.

第二回路：常闭电磁阀和柱塞泵的连接部分（包括蓄能器）。

Secondary circuit: the connectionpart of normally closed electromagnetic valve
and piston pump (including the accumulator).

## 2.2 缩略词(Abbreviation)

| ACC   | 蓄能器 Accumulator                    |
|-------|---------------------------------------|
| ABS   | 防抱死制动系统 Anti-lock Brake System |
| ECU   | 电子控制单元 Electronic Control Unit  |
| NC    | 常闭电磁阀 Normal Close Valve         |
| NO    | 常开电磁阀 Normal Open Valve          |
| HCU   | 液压控制单元 Hydraulic Control Unit   |
| FM/C  | 前轮制动主缸 Front Master Cylinder    |
| RM/C  | 后轮制动主缸 Rear Master Cylinder     |
| PWM   | 脉宽调制 Pulse Width Modulated        |
| EHCU  | 电子控制单元和液压控制单元 ECU&HCU    |


# 3 应用范围(Applied Range)

## 3.1 概述(Overview)

这个客户技术文件包含了针对两轮摩托车、高速电动车、电瓶车等防抱死制动系统（ABS）的相关产品信息。

This customer technical file contains related product information about two
rounds of motorcycle, high-speed electric vehicles, electromobile and other
anti-lock braking system (ABS).

## 3.2 制动主缸和管路的要求(Requirements for brake master cylinder and the pipe line)

| **主缸(Master cylinder)**                                                                                            | **数值(Numerical value)**            |
|----------------------------------------------------------------------------------------------------------------------|--------------------------------------|
| 最大允许压力(maximum permissible pressure)                                                                           | ≤ 25 MPa ( 250bar)                   |
| 主缸上对应 ABS 液压控制单元的油口直径(The oil outlet diameter for the ABS hydraulic control unit on master cylinder) | ≥(TBD) mm                            |
| **从主缸到液压单元(From the master cylinder to hydraulic unit)**                                                     |                                      |
| 流量(Flow) 环境温度(Environment temperature) 压降(Pressure drop)                                                     | ≥ 3.0 cm3/s -25 °C 30 kPa ( 300mbar) |

## 3.3 第一级回路压力-体积特征（Presssure-volume characteristics in Primary circuit）

| 第一级回路压力（Primary circuit pressur） | 10MPa（100 bar） |
|-------------------------------------------|------------------|
| 环境温度(Environment temperature)         | + 23 °C ± 5 °C   |
| 体积需求（Volume consumption）            | ≤3 cm3 (TBD)     |

## 3.4 ABS 系统对连接线束的要求(The wire and connection requirements on ABS system)

客户需采用宁波赛福试验验证的接插件型号，该接插件信息将在项目前期提供给客户。接插件的安装和线束具体要求参考CS-9006
文件。

Customers need to adopt the connector type which is verified by Ningbo Safe, and
the connector information will be provided to the customer in the early stage of
the project. The installation of the connector and wire line requirements refer
to the document CS-9006 for more details.

# 4 概要数据(Synopsis data)

## 4.1 尺寸安装及交货状态(Installation and delivery status)

1.  参见项目后期宁波赛福提供的客户图纸；

    See the customer drawings for reference.

2.  HCU 连接管路不得相互调换。

    The connections to the HCU must not be interchanged.

## 4.2 液压介质(Pressure medium)

以下制动液的混合是允许的，而且液压介质须符合SAE J 1703、FMVSS 116、DIN ISO
4925及JIS K2233 规范要求。

A mixture of these brake fluids is permissible. And the pressure medium should
meet the requirements of SAE J 1703、FMVSS 116、DIN ISO 4925 and JIS K2233.

1) DOT 3；

2) DOT 4；

3) DOT 4+ (plus) Super DOT4+ (plus) DOT 5.1。

如果制动系统加注了除上面指定之外的制动液，则必须更换液压单元。

If the brake system is accidentally filled with fluids other than the above
mentioned, replacement of the HCU is necessary.

此外，制动回路不得含氯、硫等无机物，也不得含矿物油或酯基可塑剂或软化剂（包括可能溶出该类物质的部件）。

Furthermore, brake circuits shall not contain chlorine, sulfur , other inorganic
substances and mineral oil or ester plasticizer or softener(including possible
dissolution components of this material).

## 4.3 原理图(Schematic Diagram)

液压原理图如下图所示。

Hydraulic schematic diagram is shown in the figure below.

# 5 环境条件（Environmental Conditions）

## 5.1 储存时间（自生产日期起）(Storage time from manufacturing date)

### 5.1.1 液压单元(干式)( The Hydraulic Unit (non filled))

储存时间：液压单元必须在自制造日期起 6
个月之内填充制动液，否则必须送回制造商处检查。

Storage time: the hydraulic unit must be filled with brake fluid within 6 months
after its manufacturing date, or it must be sent back to the manufacturer for
checking.

### 5.1.2 液压单元(湿式) ( The Hydraulic Unit (filled with brake fluid))

储存时间：3 年后，HCU 必须送回制造商处检查。

Storage time: The HU has to be sent back 3 years after its manufacturing date to
the manufacturer for examination.

## 5.2 ABS工作时间(ABS Operating time)

基于以下假设：

Based on the following assumptions:

| 车辆寿命(life time of vehicle)       | 15Year    |
|--------------------------------------|-----------|
| 里程寿命(mileage lifetime)           | 100000 km |
| 电控单元操作时间(ECU operating time) | 6000 h    |

以上提到的“寿命”及“里程寿命”不作为产品设计的耐久性保证。

"Lifetime" and "mileage lifetime " mentioned above are not as a guarantee of the
durability of the product design.

## 5.3 环境温度(Environment temperature)

### 5.3.1 储存温度(Storage temperature)

| 处于一般相对湿度(at an average relative humidity of)                                                                                                              | 60 %                |
|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------|
| 储存全过程温度(for the entire storage)                                                                                                                            | - 20 °C \~ + 50 °C  |
| 此温度下不超过 50 小时 (no more than 50 hours under this temperature)                                                                                             | - 40 °C \~ - 20 °C  |
| 管接口以橡胶件或塑料盖密封时，此温度下不超过50 小时 (For a storage time with port closure via rubber/ plastic caps of max. 50h is valid for temperature range of) | + 50 °C \~ + 100 °C |
| 管接口以胶带密封时，此温度下不超过 50 小时 (For a storage time with port closure via tape of max. 50h is valid for temperature range of)                          | + 50 °C \~ + 80 °C  |

储存条件超出上述条件时，必须咨询供应商。It is necessary to contact Safe when the
storage and shipping conditions are outside of the specified range above.

### 5.3.2 工作温度（Operating temperature）

| 工作温度范围(operating temperature range) | - 40 °C \~ 105 °C |
|-------------------------------------------|-------------------|

## 5.4 允许的调节和工作时间(Permitted regulation and operating time)

### 5.4.1 试验和诊断状态(Testing and diagnostic mode)

电磁阀过长时间通电会导致线圈损坏，为避免出现这种损坏，在试验和诊断模式下，除人工排气和抽真空加注外，电磁阀通电时间受到
ECU 的限制。在人工排气和抽真空加注时，需要足够的冷却时间。

In order to prevent inadmissibly long actuation of the magnet valves in
diagnostic or testing mode (except bleeding evacuate and filling steps) which
could cause damage to the coils, the switch-on time of the magnet valves is
limited by the ECU. Sufficient cooling time is essential for bleeding evacuate
and filling steps.

### 5.4.2 实车状态(Real vehicle state)

1)
液压单元的部件在设计上也不能承受无限的通电时间，为避免这些部件的热损坏，必须在驾驶方式过程中空出适当的冷却时间；

The HCU are not designed for unlimited power-on time.To avoid thermal damage to
these components, an appropriate cooling time between driving maneuvers is
necessary.

2) “驾驶方式”由供应商的匹配和系统开发部门定义；

"Drive mode" should be defined by the vehicle application and system development
groups of the Supplier.

3) 这些“驾驶方式”代表了通电时间方面的、最恶劣现实驾驶工况；

These driving maneuvers represent the worst case real world stress with regard
to switch-on time of the components.

4) 连续执行这些“驾驶方式”，必须空出足够的冷却时间。

A repetition of these driving maneuvers without sufficient cooling time is not
allowed.

# 6 电气特性(Electrical Characteristic)

除非另有说明，在环境温度：-40 °C \~105 °C
情况下参考以本章给出的电气性能参数。并参考以下操作条件。

Unless otherwise stated, electric performance parameters for reference is given
in this chapter are valid for the environmental temperature: -40 °C \~105 °C.And
refer to the following operation conditions.

## 6.1 工作电压(Working Voltage)

HCU 的工作电压范围主要取决于 ABS 系统工作时的压降，以及点火电压打开及关闭时的
ECU 门限值。EHCU的正常工作电压为：9 V\~16 V。

The working voltage range of HCU mainly depends on the ABS system pressure drop
at work, and the ECU threshold when ignition is on and off.Normal working
voltage range of EHCU is：9 V\~16 V

### 6.1.1 电压门限(Voltage thresholds)

| 电压范围 (voltage range) | 描述 (description)                                                    | ABS 功能 ABS function | CAN 通信（如果有） CAN communication (if has) |
|--------------------------|-----------------------------------------------------------------------|-----------------------|-----------------------------------------------|
| \< 7V                    | 欠压 undervoltage                                                     | N                     | N                                             |
| 7 V \~ 9 V               | 低压,部分功能受限 Low pressure and part of the functional limitations | N                     | Y                                             |
| 9 V \~ 16 V              | 正常工作范围 Normal working range                                     | Y                     | Y                                             |
| \>16 V                   | 过压,功能关闭 Overvoltage, function to shut down                      | N                     | N                                             |

## 6.2 功耗(Power consumption)

| 电压(voltage)                     | 13.5 V         |
|-----------------------------------|----------------|
| 环境温度(environment temperature) | + 23 °C ± 5 °C |
| 待机（standby）                   | ＜2W           |
| ABS控制时（during ABS control）   | ≤280W          |

## 6.3 系统抗过压能力(Over voltage capability of the system)

| 点火时(At Ignition ON)            | 16 V \~ 18 V (持续循环 1 V/min) 16V\~18V(sustained circulating 1 V/min) |
|-----------------------------------|-------------------------------------------------------------------------|
| 持续时间(time of duration)        | 2 h                                                                     |
| 环境温度(environment temperature) | + 23 °C ± 5 °C                                                          |

## 6.4 系统的高压起动能力(Jump start ability of the system )

高压起动是指在使用快速充电器（24 V）进行启动时，系统的启动特性。

Jump start is a start assist feature which allows use of increased voltage from
a rapid charger (24 V).

| 过电压(over voltage)              | 26 V           |
|-----------------------------------|----------------|
| 持续时间(time of duration)        | 1 min          |
| 环境温度(environment temperature) | + 23 °C ± 5 °C |

## 6.5 电池极性接反保护(Reverse-polarity protection)

| 电池极性接反保护(Reverse-polarity protection) | - 13.5 V / 5 min  |
|-----------------------------------------------|-------------------|
| 环境温度(environment temperature)             | + 23 °C ± 5 °C    |

# 7 功能参数(Functional Parameter)

在本章中，如无特别说明，本文所有特性参数的有效环境温度是：- 40 °C \~ 105 °C。

Unless otherwise specified, in this chapter, the effectively environment
temperature of all parameters in this paper is : - 40 °C \~ 105 °C.

## 7.1 压力特性参数(Pressure characteristic parameters)

| 液压管路最大许可工作压力 (The maximum permissible working pressure of hydraulic pipe)                                                                                                                                                       | ≤ 25 MPa  (≤ 250 bar)             |
|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| 在对主缸进行产品性能评审试验时，最大许可压力 (Product performance review to master cylinder test, maximum permission pressure)                                                                                                              | 25 ± 1 MPa  (250±10bar)           |
| 泵工作时第一回路的最大许可压力 (The maximum permissible pressure of the primary circuit when the pump work)                                                                                                                                 | 25 MPa (250 bar)                  |
| 在常开电磁阀关闭时，主缸接口和轮缸接口间的最大许可压力差值 (The maximum permissible differential pressure valuebetween master cylinder interface and wheel cylinder interface when the normally open solenoid valve is closed)              | 20 MPa (200 bar)                  |
| 在常开电磁阀关闭时，主缸接口和轮缸接口间的压力差峰值的最大 许可值 (The peak value of maximum permission pressure difference between master cylinder interface and wheel cylinder interface when the normally open solenoid valve is closed) | 25 MPa (250 bar)                  |
| 制动液泄漏的最小压力门限 (The minimum pressure threshold brake fluid leakage) 第一回路(Primary circuit) 第二回路(Secondary circuit)                                                                                                         |   35 MPa(350 bar) 19 MPa(190 bar) |

# 8 试验方法(Test Method)

如果满足第 5 章和第 6
章中的特征数据，则认为以下各项试验通过（在客户反馈被评估为无缺陷的情况下）。

The individual tests and customer returns are passed / assessed without defects
when the classified data from chapter 5 and 6 are fulfilled.

客户负责在场地条件下实车验证（ABS）单元在系统中能正确发挥其功能。

The customer must verify the proper function of the unit in the vehicle through
a vehicle test under realistic field conditions.

8.1 气候试验中须连接线束。8.1 和 8.2 中液压接口须封闭。除非另外指定。

Unless otherwise specified.Climate experiment in chapter 8.1 must connect wiring
harness，and hydraulic interface must be closed in 8.1 and 8.2.

## 8.1 气候试验(Climatic Test)

试验条件：IEC 60068 – 1。

Test conditions: IEC 60068-1.

所有气候实验中都须使用 HCU 安装支架，但支架的使用不影响试验结果。

All climate experiment must use HCU mounting bracket, but the use of the bracket
will not affect the test results.

### 8.1.1 低温(Low Temperature)

目的：验证在低温环境下，无电气动作的EHCU情况。

Purpose: to simulate the EHCU exposed to low temperature environment without
electrical activity.

| 试验基于(test according to) | IEC 60068-2-1                            |
|-----------------------------|------------------------------------------|
| 温度范围(temperature range) | - 40 °C ± 3 °C                           |
| 试验时间(test duration)     | 48 h                                     |
| 监控(monitoring)            | 无(None)                                 |
| 操作方式(operating mode)    | ECU 不连接插头(without ECU plug)         |
| 评判标准(judgment criteria) | 在试验前后 EHCU 系统功能满足所有设计要求 |

### 8.1.2 高温(High Temperature)

目的：验证在高温环境下，无电气动作的EHCU情况。

Purpose: to simulate the EHCU exposed to high temperature environment without
electrical activity.

| 实验基于(test according to) | IEC 60068-2-2                              |
|-----------------------------|--------------------------------------------|
| 温度范围(temperature range) | + 125 °C ± 3 °C                            |
| 试验时间(test duration)     | 48 h                                       |
| 监控(monitoring)            | 无(None)                                   |
| 操作方式(operating mode)    | ECU 不连接插头(without ECU plug)           |
| 评判标准(judgment criteria) | 在试验前后 EHCU 系统功能满足所有设计要求。 |

### 8.1.3 热冲击试验(Thermal shock test)

目的：用于验证 EHCU 抵抗热老化的能力。

Purpose: to validate the thermal aging resistance of EHCU.

| 试验基于(test according to)           | IEC 60068-2-14 Test Na                                                                                                                                                                          |
|---------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 温度下限(lower temperature limit)     | - 40 °C ± 3°C                                                                                                                                                                                   |
| 温度上限(upper temperature limit)     | + 105 °C ± 3 °C                                                                                                                                                                                 |
| 试验持续时间(test duration)           | 2 h                                                                                                                                                                                             |
| 过渡时间(transient time)              | ≤ 30s                                                                                                                                                                                           |
| 温度循环次数(Temperature cycle times) | 100                                                                                                                                                                                             |
| 监控(monitoring)                      | 无(None)                                                                                                                                                                                        |
| 操作方式(operating mode)              | ECU 不连接插头(without ECU plug)                                                                                                                                                                |
| 评判标准(judgment criteria)           | 在试验前后 EHCU 系统功能满足所有设计要求，不发生破裂和变形。(In the before and after the test, EHCU system functions should meet all the design requirements, with no fracture and deformation) |

### 8.1.4 耐腐蚀性 (Corrosion resistance)

8.1.4.1 恒定湿度(constant humidity)

目的：潮湿周期变化导致材料老化，特别是塑料件。

Purpose: wet cycle changes cause material aging, especially the plastic parts.

| 试验基于(test according to) | IEC 60068-2-78                                                                                                                                                                                   |
|-----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 温度(temperature)           | + 85 °C ± 3 °C                                                                                                                                                                                   |
| 湿度(humidity)              | 85% \~ 95%                                                                                                                                                                                       |
| 循环时间(cycling time)      | 10 day                                                                                                                                                                                           |
| 监控(monitoring)            | 上电(power on)                                                                                                                                                                                   |
| 评判标准(judgment criteria) | 试验期间，不能出现电气故障。并通过功能试验。不能出现破裂和变形。 (During the test, no electrical faults appear,and the function test should be passed through, with no fracture and deformation) |

8.1.4.2 盐雾(salt spray)

目的：盐雾引起液压单元表面锈蚀，由此快速检出暗伤。

Purpose: salt spray causes hydraulic unit surface rusting, thus rapid detection
internal injury.

| 试验基于(test according to)  | ASTM-B117                                                                                                                                                                                                                                                                                                   |
|------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 试验时间(test duration)      | 168 h                                                                                                                                                                                                                                                                                                       |
| 监控(monitoring)             | 无(None)                                                                                                                                                                                                                                                                                                    |
|  评判标准(judgment criteria) | 试验期间不能出现电气故障、关键区域（譬如电气插头以及 ECU 内部）不许盐水侵入、功能试验要求必须满足。 (During the test, no electrical faults are allowed, key areas (such as electrical plugs and ECU internal) are not allowed to be intruded by salt water, and the function test should be passed through) |

8.1.4.3 温度、湿度混合循环试验(Temperature, humidity mixed cycling test)

目的：高温加高湿循环试验引起电控单元内部的电子元器件锈蚀。本试验模拟热带环境条件。

Purpose: electronic components in the electronic control unit (ECU) corrosion
caused by high temperature and heightening wet cycling test. The experimental
simulate the tropical environment conditions.

| 试验基于(test according to) | IEC 60068-2-38 Z/AD test |
|-----------------------------|--------------------------|

单个试验循环包括：(single test cycle include:)

| 48 小时循环(48 hours circulation)                              |                                                                                                                                           |
|----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| 温度上限(upper temperature limit) 湿度：93%±3%                 | + 65 °C ± 2 °C  Humidity: 93%±3%                                                                                                          |
| 中间温度(medium temperature) 湿度：93%±3%                      | + 25 °C ± 2 °C                                                                                                                            |
| 温度下限(lower temperature limit) 湿度：25°C以下，湿度不作要求 | - 10 °C ± 2 °C Humidity: under 25°C , unrequired                                                                                          |
| 持续时间(test duration)                                        | 10 day                                                                                                                                    |
| 监控(monitoring)                                               | 阀泵电机测试，检测电流值 (valve on the pump motor testing, check the current value)                                                       |
| 评判标准(judgment criteria)                                    | 试验期间不能出现电气故障，并通过功能试验。 (during the test, no electrical faults appear, and the function test should be passed through) |

### 8.1.5 保护级别（Protection Class）

8.1.5.1 尘土（Dust）

目的：验证 EHCU 的防止尘土侵入能力。

Purpose: to verify the preventing dust invasion ability of the EHCU.

| 试验基于(test according to)    | ISO 20653                                                                                                                                           |
|--------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| 保护级别(protection class)     | IP 6K                                                                                                                                               |
| 试验时间(test duration)        | 8 h                                                                                                                                                 |
| 尘粒大小(dust particles size ) | 参考 ISO 12103-1、 Arizona 沙尘、 A2 测试细沙等级。 (refer to ISO 12103-1, the Arizona desert dust, A2 testing level of fine sand)                  |
| 监控(monitoring)               | 无(None)                                                                                                                                            |
| 评判标准(judgment criteria)    | 不得有尘粒进入试件的密封区，并通过功能试验。 (no dust particles can go into the specimen seal area, and the function test should be passed through) |

8.1.5.2 液体相容性(Fluid compatibility)

目的：本试验用于检验液压单元的耐腐蚀性。

Purpose: this test is used to test the corrosion resistance of the hydraulic
unit.

| a) 擦拭试验(wipe test)                                                                                                                            |                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| 筑路焦油(road tar)                                                                                                                                |                                                                                                             |
| 制动液(brake fluid)                                                                                                                               | DOT4                                                                                                        |
| 清洗剂(cleaning agent)                                                                                                                            | 发动机清洗剂(engine cleansing agent)                                                                        |
| 液体均匀地擦拭在单元的所有表面，然后存放，存放时间 (all the surface of the unit should be wiped evenly by liquid , and then stored, storage time) | 24 h                                                                                                        |
| b) 喷淋测试(Spray test)                                                                                                                           |                                                                                                             |
| 汽油(gasoline) 无铅/超级无铅(unleaded /super unleaded)                                                                                            | 50/50                                                                                                       |
| 柴油(diesel oil)                                                                                                                                  |                                                                                                             |
| 机油(engine oil)                                                                                                                                  | SAE 10 W 40                                                                                                 |
| 装配润滑油(lubricating oil of assembly)                                                                                                           |                                                                                                             |
| 发动机冷却液(engine Coolant)                                                                                                                      |                                                                                                             |
| 试验条件(test condition)                                                                                                                          |                                                                                                             |
| 液体均匀地喷淋在单元的所有表面，然后存放。存放时间 (all the surface of the unit should be wiped evenly by liquid , and then stored, storage time) |  24 h                                                                                                       |
| 监控(monitoring)                                                                                                                                  | 无(None)                                                                                                    |
| 评判标准(judgment criteria)                                                                                                                       | 被测试件无物理损坏、开裂、变形。 (no physical damage, cracking and deformation appear to the tested sample) |

### 8.1.6 高压水喷淋(High pressure water spray)

目的：验证样件密封完整性

Purpose: to verify the seal integrity of the sample.

| 试验基于(test according to)     | ISO20653                                                                                                                                                          |
|---------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 测试设备(test equipment)        | 高压水喷头(high pressure water sprayer)                                                                                                                           |
| 水压力(water pressure)          | 大致 80 bar \~100 bar (About 80 bar \~100 bar)                                                                                                                    |
| 水温度(water temperature)       | 80 ±5°C                                                                                                                                                           |
| 水流量(water-carrying capacity) | 14 \~ 16 L/min                                                                                                                                                    |
| 距离(distance)                  | 100\~ 150 mm                                                                                                                                                      |
| 测试时间(test duration)         | 10 min                                                                                                                                                            |
| 评判标准(judgment criteria)     | 不得有水进入试件的密封区。在试验前后通过功能试验。(No water may enter the sealed areas.And the function test should be passed through before and after the test.) |

### 8.1.7 浸水(Soaking)

目的：检验液压单元在极限状况下的密封完整性（蓄能器活塞孔除外），比如车辆在深水中行驶，液压单元完全浸泡到水中。

Purpose: inspection of the seal integrity of the hydraulic unit in a limit
condition (except the accumulator piston hole), such as vehicles running in deep
water, hydraulic unit completely soaked into the water.

| 预处理(pretreatment) 温度(temperature) 持续时间(time duration)                              |  + 85 °C ± 5 °C ≥50 min                                                                                                                                                                                                                                  |
|---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 浸泡深度（液压单元完全浸入水中） (immersion depth (hydraulic unit fully immersed in water)) | 150mm                                                                                                                                                                                                                                                    |
| 水槽温度(The sink temperature)                                                              | 0 °C ± 4 °C                                                                                                                                                                                                                                              |
| 浸泡持续时间(time duration of soaking)                                                      | 1 min                                                                                                                                                                                                                                                    |
| 循环次数(cycle times)                                                                       | 12                                                                                                                                                                                                                                                       |
| 评判标准 (judgment criteria)                                                                | 不得有液体进入密封区（蓄能器活塞孔除外）。试验期间不得有电气故障发生并通过功能试验。no liquid can go into the seal area(except the accumulator piston hole).During the test, no electrical faults appear, and the function test should be passed through |

## 8.2 机械振动试验（Mechanical shock test）

在机械振动试验之前，需进行如 8.1.1 和 8.1.2
所述的预老化试验。进行机械振动试验时需连接线束，并遵照各自的方式安装支架。

The mechanical-dynamic test is to be preceded by a pre-aging process in
accordance to chapter 8.1.1 and 8.1.2. The mechanical tests are performed with
the wire harness connected and the respective bracket concept.

### 8.2.1 振动试验(vibration test)

目的：检验振动对液压单元功能的影响。

Purpose:this test checks the influence of vibration on the function of the
hydraulic unit.

| 试验基于(test according to)                                     | IEC 60068-2-64                                                                                                                                                |
|-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 频率范围(frequency range)                                       | 10 Hz \~ 1000 Hz                                                                                                                                              |
| 每一基轴的加载时间 (Duration of the loading per principle axis) | 16 h                                                                                                                                                          |
| 总试验持续时间(total test duration)                             | 48 h                                                                                                                                                          |
| 监控(monitoring)                                                | 故障诊断(Failure diagnosis)                                                                                                                                   |
| 评判标准 (judgment criteria)                                    | 试验后，被测试件无物理损坏、开裂、变形。(After test, the EHCU shall show no signs of physical damage, cracks, deformations or loose parts are not permitted.) |

备注：试验时的安装方式必须和交货状态相同。如果用到振动阻尼元件，则一个阻尼元件只能做一次试验。

Remark: mounting during the testing must correspond to the delivered
configuration. Vibration dampers are only used for one test.

8.2.1.1 试验频谱(Test spectrum)

**![](media/714b8a9d3b7cd854cb7c03a418d651bb.png)**

| Frequency (HZ) | Power Spectral Density |
|----------------|------------------------|
| 10             | 9.9069                 |
| 55             | 3.2245                 |
| 180            | 0.1238                 |
| 300            | 0.1238                 |
| 360            | 0.0695                 |
| 1000           | 0.0695                 |

随机振动谱 Random Vibration Profile

![](media/739861f3612d2fb6cd61e6ee8cfca389.png)

| Duration    | Temperature |
|-------------|-------------|
| 0 minutes   | 20℃         |
| 60 minutes  | -40℃        |
| 150 minutes | -40℃        |
| 210 minutes | 20℃         |
| 300 minutes | 105℃        |
| 410 minutes | 105℃        |
| 480 minutes | 20℃         |

所有振动测试中使用的温度循环序列(Thermal Cycle Profile Used During All Vibration
Tests)

### 8.2.2 冲击试验(Shock test)

目的：检验机械冲击加速度对 EHCU 功能的影响。

Purpose: the functional influence of the shock acceleration on the EHCU is
evaluated.

| 试验基于(test according to)                                                  | IEC 60068-2-29                                                                                                                                                                                                                                                                                                                               |
|------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 测试温度(test temperature)                                                   | + 23 °C± 5°C                                                                                                                                                                                                                                                                                                                                 |
| 冲击加速度（激励） Shock acceleration (exciter)                              | 250m / s                                                                                                                                                                                                                                                                                                                                     |
| 名义冲击持续时间 Duration of the nominal shock                               | 10 ms                                                                                                                                                                                                                                                                                                                                        |
| 冲击形式(Shock form)                                                         | 半正弦(half-sine)                                                                                                                                                                                                                                                                                                                            |
| 每一基轴和方向的冲击次数 (number of shocks per principle axis and direction) | 400                                                                                                                                                                                                                                                                                                                                          |
| 总计(total)                                                                  | 2400                                                                                                                                                                                                                                                                                                                                         |
| 监控(monitoring)                                                             | 无                                                                                                                                                                                                                                                                                                                                           |
| 评判标准(judgment criteria)                                                  | 试验期间不得有电气故障发生，试验前后被测试样件不得有破损、断裂、部件遗失以及影响功能的变形，并通过功能试验。 During the test, no electrical faults are allowed, before and after the test，the sample shall not be damaged, broken, missing parts and distorted which affects the functions, and the function test should be passed through. |

## 8.3 功能耐久试验(Functional endurance test)

### 8.3.1 目的(Purpose)

本试验的目的：在一个较短的时间内、验证EHCU在生命周期内的耐久性。在功能耐久试验进行之前，要根据
8.1.3 对液压单元做预老化试验。

This test is performed in order to provide an indication of the lifetime
durability behavior of the EHCU in a short period of time. The units will be
pre-aged according to section 8.1.3 before the functional endurance test.

### 8.3.2 试验条件(Test conditions)

试验设备：(Test equipment:)

根据其功能，试验台和车辆制动系统相对应。制动部件按以下方式模拟：

Regarding its function, the test bench corresponds to a vehicle braking
system.The braking-system components are simulated:

1.  制动主缸（MC）由一个柱塞泵代替，产生可调压力，压力范围 0 \~ 25 MPa（0 \~ 250
    bar）；

    The master cylinder (MC) is replaced by a piston pump, which generates a
    continuously variable pressure,pressure range 0 \~ 25 MPa（0 \~ 250 bar）

2.  制动卡钳由模拟装置代替。模拟装置内的制动液压缩特性和卡钳的典型工况相当。

    The brake calipers are replaced by simulators which simulate the volume
    consumption of typical brake calipers.

试验步骤：(Test procedure :)

计算机控制的试验程序选择性地启动多项耐久试验模块，尽量模拟真实工况。不同的试验均匀地排列

结合在一起。

The computer controlled test program tries to achieve a real life stress by
selectively activating several endurance modules.Different test evenly arranged
together.

试验条件：液压介质 DOT4。

Test condition: Pressure medium DOT4.

模拟一种标准定义的线束结构。试验方法的设置须考虑温度敏感部件（电控单元，马达）不得超过极

限。

Simulating a kind of harness structure of the standard definition. The set of
test method should be consider the permitted regulation time of the thermally
critically components AECU, motor) which shall not be exceeded.

### 8.3.3 耐久试验(Endurance testing)

8.3.3.1 耐久试验条件(Endurance testing conditins)

试验项目：(Test items:)

1) 常规制动模式(Conventional braking mode)；

2) ABS 制动模式(ABS braking mode)；

3) 点火自检模式(Ignition self-inspection mode)。

试验参数范围：(Test parameters range:)

1) 试验温度范围(Test temperature range)：- 40 °C \~ 105 °C；

2) 压力变化范围(Pressure change range)： 0 \~ 200 bar；

3) 模拟路面附着系数(the tire-road friction coefficient of simulation)：0.1 \~
1.0。

8.3.3.2 试验评价指标(Test evaluation)

试验完成后，系统需满足各项性能指标要求。

After completion of test, system should meet the various performance
requirements.

# 9 液压单元的安装(The installation of the hydraulic unit)

## 9.1 总则（General Rules）

1) 液压单元必须用一个支架安装到车辆上；

Hydraulic unit must be installed with a bracket to the vehicle.

2) 振动噪声安装指南(Vibration noise installation guide)：

1.  采用有限元分析、激光扫描、交互式测量等方法选择合适的支架安装点，使液压单元的振动噪声最低；

    Adopting finite element analysis, laser scanning and interactive measurement
    methods to choose the appropriate bracket mounting point, and make the
    lowest vibration noise of hydraulic unit.

2.  制动管路必须从同一方向与液压单元连接，并且能允许液压单元绕电机轴的方向转动；管路夹应使用弹性材料并且离液压单元不能太近；各个管路间保持一定间隙，避免发生碰撞而产生噪声；从主缸到液压单元的管路不能太短并且需要弯曲，这样可以衰减振动强度和改变振动的方向。

    Brake pipeline must be connected to the hydraulic units from the same
    direction, and the rotation of the hydraulic unit around the direction of
    the motor shaft is allowed; Elastic material should be used to pipe clamp
    and can't be too close to hydraulic units; Keep a certain gap between each
    line to avoid collision noise; The length from the master cylinder to the
    hydraulic unit pipeline can't be too short and the pipeline need to bend,
    and this can attenuate the vibration intensity and change the direction of
    vibration.

3.  标准安装接口（参见CS-9007文件）。

    Standard installation interface (refer to CS-9007 file).

4.  液压模块内有2个供安装模块用的螺纹（M6×1）。

    Two fastening screws thread in the hydraulic module for installation(M6×1).

## 9.2 客户支架(Customer Bracket)

支架设计参见CS-9007文件。

Bracket design please refer to refer to CS-9007 file.

## 9.3 支架随机振动试验（Random vibration test of the bracket）

支架设计必须保证不能超出 8.2.1.1
指定的加速度频谱密度。频谱的确定来自于试验，该试验的对象为一个带标准支架的ABS
液压单元，相关的装配规范见CS-9007 文件。

Stent design must ensure that it cannot exceed 8.2.1.1 specified acceleration
spectrum density.The determination of spectrum should come from the test, the
test object is an ABS hydraulic unit with standard bracket, related assembly
specification refer to CS-9007 file.
