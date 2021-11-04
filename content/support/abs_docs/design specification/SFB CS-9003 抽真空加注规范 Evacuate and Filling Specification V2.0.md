
---
title: SFB CS-9003 抽真空加注规范
linktitle: SFB CS-9003 抽真空加注规范
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---


## 更新记录
|                       | 客户规范 CUSTOMER SPECIFICATION                   |                 |
|-----------------------|---------------------------------------------------|-----------------|
| SPEC NO. SFB CS- 9003 | Evacuate and Filling Specification 抽真空加注规范 | SF10 ABS System |
| Version: V2.0         |                                                   |                 |

**Project Information**

| Customer客户： Vehicle车型：                                |                                                                                                          |
|-------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| System系统： Channel通道：                                  | ABS  2 Channel System两通道管路/1 Channel System单通道管路                                               |
| Diagnosis诊断： Kind of communication通信： Equipment设备： | Based on Customer KWP2000基于KWP2000协议 K-Line K线 On Line Evacuate and Filling machine线上抽真空加注机 |

**Release Department**

| **Department** | **Date** | **Signature** |
|----------------|----------|---------------|
|                |          |               |

**History list:**

| **Version** | **Edit**    | **Date**   | **Descriptions**                                                                                                                                                                                                                |
|-------------|-------------|------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.0         | Taylor Wang | 2015.04.09 | Draft                                                                                                                                                                                                                           |
| 1.1         | Taylor Wang | 2015.05.11 | Release                                                                                                                                                                                                                         |
| 1.2         | Taylor Wang | 2015.11.10 | Change the value of “Maximum allowed dry run time of the pump elements” from 150ms to 60s in “Hydraulic data (important for evac/fill)”.                                                                                        |
| 1.3         | Taylor Wang | 2015.12.05 | Update “Diagnostics at the beginning and during the evacuation and fill process”.                                                                                                                                               |
| 1.4         | Taylor Wang | 2015.12.11 | Update “Diagnostics at the beginning and during the evacuation and fill process”.                                                                                                                                               |
| 1.5         | Rich Chen   | 2015.12.31 | Update the Chinese translation in the section 5.1. Modify the diagram in the section 4.4.1.                                                                                                                                     |
| 1.6         | Rich Chen   | 2016.3.30  | Modify the request message of vacuum filling：the sixth byte is used for channel selection.                                                                                                                                     |
| 1.7         | Rich Chen   | 2016.5.30  | Change delivery stat of the hydraulic filling indicator from 00H to FFH in the section 4.10.1.                                                                                                                                  |
| 1.8         | Rich Chen   | 2016.6.20  | Delete the ECU responses with a negative response if the tester request is larger than the allowed 150s in the section 4.4.5.                                                                                                   |
| 1.9         | Rich Chen   | 2017.5.22  | 1-Document standardization and “PS3003” to “SFB CS-9003” 2-add the description about the ignition off in the section 4.11 3- Modify the diagram in the section 4.4.1 and 11.1 4-Modify some details in the section 5.2 and 9.2. |
| 1.10        | Matthew     | 2020.1.2   | Modify the buildup pressure schematic in the section 4.9                                                                                                                                                                        |

**  
Table of Contents目录**

[1General总述](#1general总述)

[1.1 Acronyms缩写](#11-acronyms缩写)

[1.2 Diagnostic Document诊断文档](#_Toc449392124)

[1.3 Attachments附件](#_Toc449392125)

[2 Application应用](#2-application应用)

[3 Procedure进程](#3-procedure进程)

[3.1 Scope范围](#31-scope范围)

[3.2 Process Diagram流程示意图](#32-process-diagram流程示意图)

[4 Process Step
Description流程步骤描述](#4-process-step-description流程步骤描述)

[4.1 Handling操作](#41-handling操作)

[4.2 Air Pressure Leak Check
(optional)气压泄漏检测（可选）](#42-air-pressure-leak-check-optional气压泄漏检测可选)

[4.3 Evacuation Cycle 1 抽真空循环1](#43-evacuation-cycle-1-抽真空循环1)

[4.4 Diagnostics at the beginning and during the evacuation and fill
process抽真空加注开始及过程中诊断](#44-diagnostics-at-the-beginning-and-during-the-evacuation-and-fill-process抽真空加注开始及过程中诊断)

[4.4.1 Diagram of diagnostic functions and
actuation诊断功能执行示意图](#441-diagram-of-diagnostic-functions-and-actuation诊断功能执行示意图)

[4.4.2 Communication Set Up建立通信](#442-communication-set-up建立通信)

[4.4.3 ECU-Identification
电子控制器身份标识](#443-ecu-identification-电子控制器身份标识)

[4.4.4 Check System Status校验系统状态](#444-check-system-status校验系统状态)

[4.4.5 Evacuation and Fill
Sequence抽真空加注序列](#445-evacuation-and-fill-sequence抽真空加注序列)

[4.4.6 Request Evac/Fill Routine
Results请求抽真空加注例程结果](#446-request-evacfill-routine-results请求抽真空加注例程结果)

[4.4.7 Stop Fill Process停止加注流程](#447-stop-fill-process停止加注流程)

[4.4.8 Pump motor activation to discharge the accumulator chamber
驱动电机抽空蓄能器](#448-pump-motor-activation-to-discharge-the-accumulator-chamber-驱动电机抽空蓄能器)

[4.4.9 Request Actuator Test Routine
Results请求执行器控制例程结果](#449-request-actuator-test-routine-results请求执行器控制例程结果)

[4.5 Fine Leak Check
(optional)泄漏检测（可选）](#45-fine-leak-check-optional泄漏检测可选)

[4.6 Evacuation Cycle 2
(optional)抽真空阶段2（可选）](#46-evacuation-cycle-2-optional抽真空阶段2可选)

[4.7 Fill Cycle加注循环](#47-fill-cycle加注循环)

[4.8 Pressure Leak Check
(optional)压力泄漏检测（可选）](#48-pressure-leak-check-optional压力泄漏检测可选)

[4.9 Top Off Reservoir
(Scavenging)油壶复压](#49-top-off-reservoir-scavenging油壶复压)

[4.10 Diagnostics at the end of the fill and evacuation process
抽真空加注结束后诊断](#410-diagnostics-at-the-end-of-the-fill-and-evacuation-process-抽真空加注结束后诊断)

[4.10.1 Write Process Control
Byte写加注状态值](#4101-write-process-control-byte写加注状态值)

[4.10.2 Clear fault code memory (optional)清除故障代码（可选）](#_Toc449392151)

[4.11 End of Cycle/
Handling循环结束/操作](#411-end-of-cycle-handling循环结束操作)

[5 Valve protective measures and hydraulic data of the ABS
system防抱死制动系统电磁阀保护及液压模块数据](#5-valve-protective-measures-and-hydraulic-data-of-the-abs-system防抱死制动系统电磁阀保护及液压模块数据)

[5.1 Valve protective measures for all
projects电磁阀保护措施](#51-valve-protective-measures-for-all-projects电磁阀保护措施)

[5.2 Hydraulic data (important for
evac/fill)液压数据（非常重要）](#52-hydraulic-data-important-for-evacfill液压数据非常重要)

[6 Process Timing流程时间](#6-process-timing流程时间)

[6.1 Timing for Valve
Activation’s操作时间](#61-timing-for-valve-activations操作时间)

[6.2 Timing for Evacuation
Cycle抽真空循环时间](#62-timing-for-evacuation-cycle抽真空循环时间)

[6.3 Timing for Vacuum Leak
Check抽真空泄漏校验时间](#63-timing-for-vacuum-leak-check抽真空泄漏校验时间)

[6.4 Timing for Evacuation Cycle
2抽真空阶段2时间](#64-timing-for-evacuation-cycle-2抽真空阶段2时间)

[6.5 Timing for Fill Cycle加注时间](#65-timing-for-fill-cycle加注时间)

[6.6 Timing for Pressure Leak
Checks泄漏压力测试](#66-timing-for-pressure-leak-checks泄漏压力测试)

[6.7 Timing for Reservoir Top Off
(Scavenging)油壶复压时间](#67-timing-for-reservoir-top-off-scavenging油壶复压时间)

[6.8 Timing for Operator
Handling操作人员操作时间](#68-timing-for-operator-handling操作人员操作时间)

[7 Failure Handling故障处理](#7-failure-handling故障处理)

[8 Data Specifications数据指标](#8-data-specifications数据指标)

[8.1 Hydraulic Data
Specifications液压数据规范](#81-hydraulic-data-specifications液压数据规范)

[8.2 Electrical Data
Specification电气数据规范](#82-electrical-data-specification电气数据规范)

[9 Electrical Adaptations电气连接](#9-electrical-adaptations电气连接)

[9.1 Adaptation onto the diagnostic link of the
vehicle车辆诊断接口](#91-adaptation-onto-the-diagnostic-link-of-the-vehicle车辆诊断接口)

[9.2 Adaptation onto the ECU
connector连接电子控制器接插件](#92-adaptation-onto-the-ecu-connector连接电子控制器接插件)

[10 Equipment Information设备相关信息](#10-equipment-information设备相关信息)

[11 Attachments附件](#11-attachments附件)

[11.1 Hydraulic Circuit
Diagrams液压原理图](#111-hydraulic-circuit-diagrams液压原理图)

[11.2 Electric Wiring Diagram Customer with
ABS电气接线图纸](#112-electric-wiring-diagram-customer-with-abs电气接线图纸)

[11.3 ABS connector drawing (18-pin
connector)端子连接器图纸](#113-abs-connector-drawing-18-pin-connector端子连接器图纸)

# 1General总述

## 1.1 Acronyms缩写

ABS antilock braking system防抱死制动系统

ABS-WL ABS warning lamp防抱死故障报警灯

NC normal close valve常闭电磁阀

BLS brake light switch刹车灯开关

DTC diagnostic trouble code故障代码

ECU electronic control unit电子控制单元

NO normal open valve常开电磁阀

FA front axle前轴

FCM fault code memory故障代码缓存

RA rear axle后轴

ACC accumulator蓄能器

RLI record local identifier本地身份标识

UM pump motor feedback电机反馈

WSS wheel speed sensor轮速传感器

EOL end of line下线

M/C master cylinder主缸

PB process byte流程字节

P/U pressure sensor unit压力传感器单元

RP return pump回油泵

ROM read only memory只读存储器

SV solenoid valve电磁阀

TSI Test & Service Interface routine测试服务接口程序

W/C wheel cylinder轮缸

## 1.2 Diagnostic Document诊断文档

| **NO**      | **Version版本** | **Description描述**                                           |
|-------------|-----------------|---------------------------------------------------------------|
| SFB CS-9010 | V1.8            | 诊断功能描述文档 Diagnosis Function Description Specification |
|             |                 |                                                               |

## 1.3 Attachments附件

| **NO** | **Version版本** | **Description描述** |
|--------|-----------------|---------------------|
|        |                 |                     |
|        |                 |                     |

# 2 Application应用

This document contains the procedure that has to be carried out to evacuate and
fill dry ABS systems on line with existing equipment’s and additional actuation
units. The procedure is based on K-Line diagnosis and the corresponding
features. The appropriate version of the customer/vehicle specific “Diagnosis
function description” provides information on the handling and function of the
diagnosis and which features should be used. All used diagnostic functions are
ROM-resident functions. For more details look in the “Functional description of
serial diagnosis”.

本文档包括如下必须执行的进程：用现有设备和其他执行设备对干式防抱死制动系统进行抽真空和加注。此进程基于K线诊断及其相关说明，“诊断功能描述文档”细述了诊断功能和相应参数设置。所有诊断相关的功能已固化进电子控制器的存储器中，详见“诊断功能描述文档”。

Requirements for the test facilities provided by the customer测试装置功能要求：

\-Communication with the SFB ECU能与宁波赛福电子控制器建立通信

\-Control of the test sequence控制测试序列

\-Control of the evac/fill equipment控制抽真空加注设备

\-Evaluation of the data评估测试数据

\-Issue process protocol打印流程信息

# 3 Procedure进程

## 3.1 Scope范围

All the SFB ABS components, such as hydraulic modulator is delivered to the
customers assembly plant in a dry state (free of brake fluid).Both, primary and
secondary circuits of the hydraulic modulator are dry. In order to evac/fill the
entire modulator, valves and pump motor must be energized by using electrical
adaptations and an additional equipment’s to fire valves and pump motors with a
pre-defined ROM resident routine.

所有宁波赛福防抱死制动系统组件，如液压控制单元，交付给客户工厂时均为干式（没有制动液）。一级回路和二级回路均为干式。为了抽真空和加注整个模块，需要通过加注设备来控制阀和电机得电来进行相应操作，阀和电机执行的操作已固化进电子控制器的存储器中。

The procedure will then be executed in a same way than a standard foundation
brake system with the exception of the evacuation and fill times to be adapted
onto the design of the ABS modulator orifice sizes. This will extend the
evacuation and fill times by physical limitations. The electrical adaptation can
either be done by connecting onto the diagnostic link of the vehicle (requires a
complete installation) or onto the modulator connector (requires an external
power supply with an external car battery as a buffer – SFB recommendation).

装有ABS制动系统的抽真空和加注的进程与标准基础制动系统的不同在于，前者抽真空和加注的时间要根据ABS模块的孔径大小调整，这在实体限制上延长了抽真空加注执行时间。诊断电气端可连接至车辆诊断接口（需全部连接），也可外供电源单独连接（宁波赛福推荐）。

The data for vacuum levels and minimum fill pressure of the hydraulic modulator
are specified in the “Technical Customer Documentation” of the hydraulic
modulator as well as in this document. Technical data for external power supply
are also specified in this document. The evac/fill equipment must be capable to
meet the requirements as specified in this document. In order to achieve a
sufficient vacuum level, all components, such as master cylinder, wheel calipers
and pressure relieve valves must meet the minimum requirements as specified in
this document.

液压模块抽真空达到的真空度和加注最小压力除了本文描述外，还可参见“客户技术文档”。本文也描述了外部供电的技术数据，抽真空加注设备必须满足本文所述要求。为达到所需的足够真空度，所有零件，如主缸、轮缸卡钳、减压阀等均要满足本文所列最低要求。

The final timing of the production cycle can only be determined by trials with
production parts (or parts close to production level) and on line equipment. On
line equipment may need to be modified onto the requirements of the hydraulic
configuration of the vehicle. In case of any failures of the evac/fill cycle or
a replacement of the hydraulic modulator, a repair bleed procedure must be
performed according to a specific sequence. Refer to separate document.

本过程所需生产时间需经生产线调试确定，各部件、在线设备均处于生产状态（或近生产状态）。在线设备相关参数可能要根据车型配置信息加以修改。如果在抽真空加注过程中出现故障，或者需要更换液压控制模块，该车必须按照特定顺序进行人工排气，可参见“人工排气文档”。

## 3.2 Process Diagram流程示意图

**Remarks备注：**

| **Diagram Columns:** |                                                     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no              | Activity                                            | Remarks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 1                    | Handling 操作                                       | Hook up fill head. Hook up electrical connections. 安装加注口和电气连接。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| 2                    | Air Pressure Leak Check (opt.) 气压泄漏检测（可选） | Pressure tests prior the evacuation cycle are allowed. Follow test conditions  have to be met本系统允许在抽真空之前进行泄漏测试，测试条件如下： Maximum Pressure最大压力：20 bar (depends on brake fluid reservoir视油壶来确定) Medium介质：Air, Nitrogen空气或氮气  At a following evacuation process, it is required and must be guaranteed, that the valves are actuated a minimum time of 20 seconds (1s on / 1s off) in the following evacuation phase! To reduce the locked up pressure in the accumulator chamber (possible to the defined and allowed leakage of the outlet valves) it is necessary to actuate the valves this minimum time during the evacuation cycle. 在后续的抽真空过程中，必须确保电磁阀动作时间不得少于20秒（1秒开1秒关间隔工作）。这样做的目的是防止蓄能器腔室内产生锁止压力（跟常闭电磁阀的泄漏有关）。 |
| 3                    | Evacuation Time 1 抽真空阶段1                       | Time to achieve a certain level at the calipers.  卡钳达到一定真空度所需时间。 A difference may occur by the circuit structure and orifice size at the time of achieves the vacuum level of Front circuit and Rear circuit. 由于管路长度和孔径大小不同，前后轮回路达到真空度所需时间不同。This time is the time to achieve the specified vacuum level at the calipers. 本段时间旨在确保前后卡钳都能达到所需真空度。                                                                                                                                                                                                                                                                                                                                                                                                                     |
| 4                    | Leak Test 泄漏测试                                  | To check the fittings and external leaks of the brake system. 检测管路接口和制动系统外部泄漏。 This time is a machine time and not related to the evac time of the system. 本段时间是设备的操作及响应时间，与系统抽真空时间无关。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 5                    | Evacuation Time 2 抽真空阶段2                       | This time is required to get back to a sufficient vacuum level after the leak test was performed.  泄漏检测完成后，等待系统达到稳态真空度所需时间。 It is a machine time and not related to the evac time of the system. 本段时间是设备的操作及响应时间，与系统抽真空时间无关。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 6                    | Fill Time 加注时间                                  | Time to fill both the front and rear calipers.  加注满前后卡钳所需时间。 A difference may occur by the circuit structure and orifice size at the time of achieves the pressure level of Front circuit and Rear circuit. 由于管路长度和孔径大小不同，前后轮回路达到压力值所需时间不同。 This time is the time to achieve the specified pressure level at the calipers. 本段时间是卡钳达到指定压力所需时间。                                                                                                                                                                                                                                                                                                                                                                                                                              |
| 7                    | Leak Check 泄漏检测                                 | To check the fittings and external leaks of the brake system. 检测接头和制动系统外部泄漏。 This time is a machine time and not related to the fill time of the system. 本段时间是设备响应时间，与ABS管路加注时间无关。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 8                    | Top Off  (Scavenge) 复压                            | This time is required to get back to atmospheric pressure and to top off the reservoir to a certain level.  油壶压力恢复至大气压力所需时间。 This time is a machine time and not related to the fill time of the system. 本段时间是设备响应时间，与ABS加注时间无关。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| 9                    | Handling 操作                                       | Remove fill head and unplug electrical connections. 移走加注头，断开电气连接。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| 10                   | Handling and  Diagnostic Timing 操作诊断时间        | If the communication (initiate the ECU, establish communication, check the system status) is done after the adaptations and prior to the start of the evacuation, this will delay step 1 for up to 10 seconds according to the diagnostic communication protocol. 如果通信（初始化电子控制器，建立通信，检验系统状态）在设备连接后和抽真空之前执行，根据诊断通信协议，这将使得步骤1延迟10秒钟。                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| 11                   | Diagnostic Timing 诊断时间                          | In order to optimize the entire timing, it is recommended to initiate the ECU, establish communication, check the system status and start the ROM resident routine to cycle the valves with a delay after the start of the evacuation. This delay time depends on the total cycle time. 为节省整个流程时间，在抽真空开始一段时间后，初始化电子控制器，建立通信，校验系统状态，命令电子控制器驱动阀循环动作，这段时间由整个循环周期决定。                                                                                                                                                                                                                                                                                                                                                                                                |

# 4 Process Step Description流程步骤描述

## 4.1 Handling操作

| **Handling操作**                                                                                                                        |                                                |
|-----------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------|
| Operator 操作员                                                                                                                         | Diagnostic Unit / ECU 诊断设备/电子控制器      |
| Adapt fill head to the reservoir 连接加注头至油壶口 Adapt electrical connection 电气连接 Turn Ignition ON 点火开 Start Process 开始操作 | Turn external power supply ON 打开外部供电电源 |

**Remarks备注：**

The electrical connection can be designed either in connecting onto the
diagnostic link of the vehicle or straight onto the ECU connector (depending
onto the system, the access to the unit and the installation of the vehicle
harnesses and components) (See chapter 9). Depending onto the electrical
adaptation and the equipment, the operator must either turn the ignition ON or
the equipment must turn the external power supply ON.

电气端可以通过车载诊断口连接也可以直接连接至电子控制器的接头上（具体根据不同系统、线束和零件安装等而定）（详见第9章）。根据不同接线方式，操作人员需打开点火开关或者开启外部电源。

## 4.2 Air Pressure Leak Check (optional)气压泄漏检测（可选）

| **Air Pressure Leak Check (optional)气压泄漏检测（可选）** |                                                                                                                                                                                                              |                            |
|------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| Evac/Fill Unit  抽真空加注机                               | Conditions 条件                                                                                                                                                                                              | Value 数值                 |
| Air Pressure leak check  气压泄漏检测                      | pressure level decrease within a determined test time一定时间内的压降：  time for leak check t1泄漏检测时间t1： maximum pressure level on the master cylinder reservoir (to be achieved)主缸油壶的最大压力： |  TBD sec  TBD sec  TBD bar |

**Remarks备注：**

The air pressure leak check is performed to detect leaks of the entire brake
system. The evac/fill equipment isolates the source and measures the pressure
drop within a given amount of time and compares this value with given limits.
The timing of this test step must be set to customer related requirements.

压力泄漏检测旨在检测整个制动系统的泄漏情况。抽真空加注设备能隔绝压力源，测量给定时间内系统的压降，并与标定值进行对比，检测时间由客户根据加注设备来确定。

This test step does not affect the general fill cycle of the system, but is an
additional test step. Pressure leak checks are machine related test steps and
not related to the ABS system. The valves and pump motor must be turned off
during this step.

此步骤不影响加注周期，仅作为附加测试步骤，是与设备相关的测试步骤，与防抱死制动系统无关。此步操作不得动作电磁阀和电机（失电）。

Conditions条件：

Maximum Pressure最大压力：20 bar (depends on brake fluid
reservoir与制动液油壶有关)

Medium介质：Air空气，Nitrogen氮气

At a following evacuation process, it is required and must be guaranteed, that
the valves are actuated a minimum time of 20s (1s on / 1s off) in the following
evacuation phase! To reduce the locked up pressure in the accumulator chamber
(defined and allowed leakage of the outlet valves) it is necessary to actuate
the valves this minimum time during the evacuation cycle.

在后续的抽真空过程中，必须确保电磁阀动作时间不得少于20秒（1秒开1秒关间隔工作）。这样做的目的是防止蓄能器腔室内产生锁止压力。

Air Pressure Leak Check ok. -\> continue压力泄漏检测通过，继续

Air Pressure Leak Check not ok. -\> continue, set failure
message压力泄漏检测失败，故障报警

**Air Pressure Leak Check Diagram气压泄漏检测示意图：**

| **Diagram Columns:** |                                                                                      |                                                                                                                                                                                                                                  |
|----------------------|--------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                                                             | Remarks                                                                                                                                                                                                                          |
| 1                    | Start of pressure leak Check 开始压力泄漏检测                                        | Time to start the pressure leak check and to pick up the pressure level. 开始泄漏检测，达到压力位所需时间。                                                                                                                      |
| 2                    | End of pressure leak Check 泄漏检测结束   Relax to atmospheric Pressure 恢复至大气压 | Time to end the pressure leak check and to pick up the pressure level again for evaluation of the pressure drop. 结束泄漏测试，压力恢复到大气压所需时间。  Evac/fill equipment to release the air pressure. 抽真空加注设备泄压。 |
| t1                   | Time of air pressure leak check  泄漏检测时间                                        | Must be defined by the customer in order to meet the total cycle time. 由客户指定，以满足整个循环时间。                                                                                                                          |

## 4.3 Evacuation Cycle 1 抽真空循环1

| **Evacuation Cycle 1抽真空循环1**  |                                                                                                                                                                                                             |                                 |
|------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------|
| Evac/Fill Unit 抽真空加注机        | Conditions 条件                                                                                                                                                                                             | Value 数值                      |
| Evacuation cycle 1  抽真空循环1    | Minimum vacuum level on the master cylinder reservoir (to be achieved)主缸油壶口最低真空度：  Minimum vacuum level on the wheel calipers (to be achieved)轮缸最低真空度：  Evacuation time t2抽真空时间t2： |  \<2 mbar   \<10 mbar   TBD sec |
| Great Leak Check 泄漏检测          | Minimum vacuum level on the master cylinder reservoir (to be achieved) 主缸油壶口最低真空度：                                                                                                               |  TBD mbar                       |

**Remarks备注：**

The evac/fill unit must be capable to achieve a sufficient vacuum level at the
master cylinder reservoir in order to get a good vacuum level on the wheel
calipers due to the pressure drop of each component.

The evacuation time is a function out of the orifice sizes of the hydraulic
modulator and the volumes of the wheel calipers, the pipes and hoses must be set
by running trials with production level components, using the on line equipment.

抽真空加注设备需使主缸油壶达到一定真空度，这样才能使每个轮缸卡钳达到所需真空度。抽真空时间与液压模块孔径、轮缸卡钳容积、管路、接头都有关系，具体参数要根据生产线调试结果而定。

The communication set up between the Tester and the ECU and the corresponding
functions as described in the following chapters can be integrated within the
first seconds of the evacuation cycle with a minor extension of the evacuation
time (approximately 2 to 4 seconds).The Great leak check detects big leakages in
the entire brake system.

下一章将讲述设备与电子控制器间通信、功能操作，这些操作在抽真空初期就需要执行，这样可以节省整个操作时间（大约2到4秒）。泄漏检测能识别整个制动系统的泄漏。

Evacuation value ok. -\> Continue抽真空通过，继续

Evacuation value not ok. -\> Abort抽真空失败，中断

**Evacuation Diagram抽真空示意图：**

**Remarks备注:**

| **Diagram Columns:** |                                                               |                                                                                                                                                                                                                                                                                                                                                                                                          |
|----------------------|---------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                                      | Remarks                                                                                                                                                                                                                                                                                                                                                                                                  |
| 1                    | Start of evacuation cycle 1 开始抽真空循环阶段1               | Operator push the start button on the fill head. 操作者按下加注头上的开始按钮。                                                                                                                                                                                                                                                                                                                          |
| 2                    | Communication Set Up 建立通信                                 | Diagnostic equipment to establish the communication.  诊断设备建立通讯。                                                                                                                                                                                                                                                                                                                                 |
| 3                    | System Identification 系统身份识别                            | Diagnostic equipment to check whether the correct system is installed. 诊断设备检测系统信息校验。                                                                                                                                                                                                                                                                                                        |
| 4                    | Check System Status 检查系统状态                              | Diagnostic equipment to check whether the system is enabled and can execute the following valve and pump activations. 诊断设备检测系统能否执行阀和电机的动作。 Diagnostic equipment executes the ROM resident routine to activate the valves. A pump motor activation is not required. 诊断设备请求执行电子控制器内部程序驱动阀，不需驱动电机。                                                          |
| 5                    | Start Evacuation and Fill Sequence 开始抽真空加注序列         | The routine cycles the valves during the entire evacuation and fill cycle. This is required to evacuate the secondary circuits of the hydraulic modulator. 在抽真空加注过程中电磁阀一直会工作，这样有助于对液压模块二级回路抽真空。                                                                                                                                                                      |
|                      | Timing of diagnosis 诊断时间                                  | Numbers 2 to 5 can be integrated into this step in order to minimize the total cycle time. The delay time from the start of the evacuation until the start of the routine must not exceed 10 seconds in order to minimize the additional evacuation time. 步骤2到5可整合到抽真空此流程中，这样可降低整个抽真空总时间。从开始抽真空到开始抽真空加注序列之间延时不得超过10秒，这样可降低整个抽真空总时间。 |
| 6                    | Great Leak Check 泄漏检测                                     | This check detects leakages in fittings and components of the entire break system. 泄漏检测可检测出接口和制动系统管路中的泄漏。 In case of any failure detection the process must be aborted and a failure message must be indicated. The test is performed within the first evacuation cycle. 遇有错误时，先中断测试，故障报警，重新开始抽真空阶段1测试。                                               |
| 7                    | Evacuation of the front axle and the rear axle 前后轴抽真空   | A difference may occur by the circuit structure and orifice size at the time of achieves the vacuum level of Front circuit and Rear circuit. 由于管路长度和孔径大小不同，前后轮回路达到真空度所需时间不同。                                                                                                                                                                                              |
| t2                   | Evacuation Timing 抽真空时间                                  | The required evacuation time must be determined by running trials with production level brake components using the on line evac/fill equipment. 抽真空时间必须使用线上抽真空加注设备在生产线上调试确定，制动系统各零件必须处于生产状态。                                                                                                                                                                 |

## 4.4 Diagnostics at the beginning and during the evacuation and fill process抽真空加注开始及过程中诊断

### 4.4.1 Diagram of diagnostic functions and actuation诊断功能执行示意图

NC FA

NC RA

**Remarks备注：**

This procedure is valid for all ABS systems. An actuation of the pump motor
during the entire evacuation and fill process is not required, because a
sufficient fill result is reached without pump activation’s. At some projects
the entire evac/fill process could be longer than the limited actuation time of
the valves. For these projects SFB recommends an actuation delay time to start
the ROM resident function.

本流程适合防抱死制动系统，在抽真空加注过程中不需要驱动电机转动，因为加注结果与电机驱动无关。一些项目的抽真空加注时间可能超出电磁阀工作时间限制，宁波赛福建议在启动电子控制器内部程序前先延时一段时间。

**Important remark to the pump actuation泵驱动重要备注：**

At the end of line tests or at another assembly step the pump motor must be
activated for a minimum time of 2 seconds to discharge the accumulator chamber.
The activation of the pump is an absolute must and the execution must be
guaranteed, because no ABS control is possible with a filled accumulator
chamber.

The actuation of the pump motor at the end of the fill process or at the end of
line tests must be executed with the ROM resident function “Actuator test”.

在下线检测或其他生产线上驱动泵转动至少2秒才能抽空蓄能器腔室的制动液，驱动泵运转是必要的，且必须得到保证，因为蓄能器满时会影响防抱死制动系统工作效果。在加注或测试最后，驱动泵运转需要通过电子控制器内部“执行器测试”程序来完成。

**Important remark about actuation of pump motor valid泵马达运行重要备注：**

For safety reasons to avoid any damages at the pump Seal-rings, the maximum
allowed pump dry run time was reduced to 60sec! In case of a pump motor
activation during the evac process on account of technical reasons of the
customer it must be guaranteed that the entire dry run time while the evac/fill
and possible following repair bleeding process might not be longer than 60sec!

出于安全考虑，为了避免泵密封圈损坏，泵干转的最小运行时间应降至60s。由于客户技术问题，造成抽真空过程中泵马达需要运行，那么必须确保在抽真空加注过程中及接下来可能发生的人工排气过程中，泵马达总的运行时间不能超过60s。

**Important remark about actuation of the valves valid阀运行重要备注：**

The ROM resident routine is internal limited to a maximum activation time of
150s. That means, if the tester do not send the command end of routine within
the 150s, the ECU deactivates and hydraulic data. For more details look also in
the chapter “Valve protective measures and hydraulic data”. It is not allowed to
repeat the valve actuation routine immediately after the first actuation cycle,
because the valves might be damaged by overheating!

电子控制器驱动程序内部限制了最大运行时间为150s，也就是说，如果测试设备没有在150s内发出结束命令，ECU和液压模块数据将失效。更多详情见章节“电磁阀保护及液压模块数据”。不允许在第一个运行周期后立刻反复动作阀，这样会使阀因过热而受损。

### 4.4.2 Communication Set Up建立通信

| **Diagnostic Function诊断功能：Start Diagnostic Session开始诊断**                                                     |                                             |
|-----------------------------------------------------------------------------------------------------------------------|---------------------------------------------|
| Start Diagnostic Session (Request) 开启诊断会话（请求）                                                               | 10h                                         |
| Start Communication开始通信                                                                                           | 83h                                         |
| Start Diagnostic Session (P. Response) 开启诊断会话（肯定应答）                                                       | 50h                                         |
| Start Communication开始通信                                                                                           | 83h                                         |
| Diagnostic Equipment诊断设备 Communication Set Up建立通信                                                             | ECU Enters into diagnostic mode进入诊断模式 |
| Initialization and communication set up see “functional description of diagnosis”. 初始化和通信见“诊断功能描述文档”。 |                                             |

**Remarks备注:**

The communication set up between the Tester and the ECU is based on K-Line
diagnosis according to the corresponding specification. It can be started
immediately after the system is powered up. In case of a non successful
communication set up repeat for about 3 times before the test is interrupted.

诊断设备和电子控制器间诊断通信基于K线诊断技术规范，系统上电即可进行通信。通信不成功可以重复3次，如果还不成功，应停止通信，尝试排除故障。

Communication not successful -\> set failure message,
continue通信失败，故障报警，继续

Communication successful -\> continue通信成功，继续

In case of a non successful communication, the process can be continued, however
the equipment must indicate a failure message. The foundation brake system will
be evacuated and filled with the exception of the secondary circuits of the
hydraulic modulator. This makes it easier to repair bleed the brake system.

通信不成功时，抽真空加注设备仍可以继续测试，只需提示故障信息。基础制动回路将被抽真空加注，但不包括液压模块的二级回路，这使得制动系统的人工排气更加容易。

### 4.4.3 ECU-Identification 电子控制器身份标识

| **Diagnostic Function诊断功能：Read ECU Identification电子控制器身份标识**                                                     |                                           |
|--------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| Read ECU Identification (Request)读取ECU身份标识（请求）                                                                       | 1Ah                                       |
| Record Local Identifier本地身份标识 -Customer Part Number客户零件号 -SFB Part Number赛福零件号 -Project Name项目名称           |  91h 92h 9Ah                              |
| Service Code (P. Response) 服务代码（肯定应答） Record Local Identifier本地身份标识                                            | 5Ah  XXh                                  |
| Customer Part Number客户零件号(13 bytes ASCII)  SFB Part Number赛福零件号(13 bytes ASCII) Project Name项目名称(13 bytes ASCII) | XXXXXXXXXXXXX XXXXXXXXXXXXX XXXXXXXXXXXXX |

**Remarks备注:**

See ECU data in diagnostic specification for details of byte numbers, values and
ranges. The ECU data must be verified with the demand data of the tester
software. (These data may change in case of revision changes and should be
capable to be edited and to add new numbers).

电子控制器数据的字节数、数值、范围定义请参考诊断技术文档，诊断设备软件数据与电子控制器软件数据要相互校验。(如果版本变更，这些数据有可能会改变，因此它们能够被编辑和增加)。

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat request”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request (7Fh 1Ah 21h)” shows the ECU, that the request is understood, but
the previous request is still being executed and its result might affect the
response to the requested service. The tester has to send the same request
again, until it gets a final response (positive or negative with LID different
from 21)).

如果服务执行时间超过50毫秒，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断设备发送的服务请求，如“7Fh
1Ah
21h”）诊断设备应重复当前命令，直至电子控制器回复正面应答（或者非“繁忙（21h）”应答）。

Unknown System -\> Abort Test系统未知，中断测试

System detected -\> Continue系统识别，继续

### 4.4.4 Check System Status校验系统状态

| **Diagnostic Function诊断功能：Read Data By Local ldentifier本地身份标识**      |                     |                                         |                         |              |
|---------------------------------------------------------------------------------|---------------------|-----------------------------------------|-------------------------|--------------|
| Read Data By Local Identifier (Request)通过本地身份标识读取数据（请求）         | 21h                 |                                         |                         |              |
| Record Local Identifier本地身份标识                                             | 04h                 |                                         |                         |              |
| Read Data By Local Identifier (P.Response) 通过本地身份标识读取数据（肯定应答） | 61h                 |                                         |                         |              |
| Record Local Identifier本地身份标识                                             | 04h                 |                                         |                         |              |
| ECU Data to be evaluated待评估的ECU数据：                                       |                     |                                         |                         |              |
| ECU-Data ECU数据：                                                              | Byte / Bit字节/位： | Actual Data驱动数据：                   | Demand Data需求数据：   | System系统： |
| Valve relay status阀继电器状态                                                  | Byte 4/ Bit 6       | actuated (1)驱动 not actuated (0)未驱动 | Correct正确 Failure错误 | both 两者    |

**Remarks备注:**

See ECU data in diagnostic specification for details of byte numbers, values and
ranges. Prior to the evac/fill process, the diagnostic equipment must identify
whether the ECU is active or passive. In case of any failure detection, the ECU
will have disabled the system and have aborted the valve and pump motor
activation’s.

Following failures lead to a shutdown of the valve relay, a valve fault, a valve
relay fault or a voltage drop. A pump motor fault (also a disconnected PM
ground) doesn’t lead to a valve relay shut down! The ECU data must be verified
with the limit data of the tester software.

电子控制器数据中的字节数、数值、范围定义请参考诊断技术文档，诊断设备应能识别电子控制器处于在线、离线状态。遇有故障，电子控制器应能识别故障类型并立即中断阀和电机的操作。遇有下列错误应关断阀继电器：阀故障、阀继电器故障、电压跌落。电机故障（接地线开路）不会导致阀继电器关断。诊断设备软件应校验电子控制器数据在限定值范围内。

Data correct -\> Continue数据正确，继续

Data not correct -\> Failure message, continue故障报警，继续

This step checks whether the system is enabled or disabled by evaluating the
data above. In case the system is disabled, no valves can be activated. This
check is performed prior and at the end of the evac/fill cycle in order to
detect system failures. During the valve activation’s, the ECU is internally
monitoring the activation’s and in case of a failure disables the system to
avoid any damage.

这一步旨在检测抽真空数据状态是否正确激活，如果没有激活，阀将不会动作。该检测在抽真空加注之前和最后都会被执行，以检测系统是否失效。在电磁阀动作期间，电子控制器一直会监控其运行状况，一旦有故障会立即停止驱动电磁阀，防止对系统产生损坏。

### 4.4.5 Evacuation and Fill Sequence抽真空加注序列

| **Diagnostic Function诊断功能：Start Evac and Fill Routine By Local Identifier根据本地身份标识开始抽真空加注例程** |             |                                       |
|--------------------------------------------------------------------------------------------------------------------|-------------|---------------------------------------|
| Service Identifier(Request)服务身份标识（请求）                                                                    | 31h         |                                       |
| Routine Local Identifier例程本地身份标识                                                                           | D1h         |                                       |
| Routine Control Parameter输入输出控制参数                                                                          | 00h         | Start periodic control开始周期控制    |
| Type Of The Control控制形式                                                                                        | 00h         | Vacuum filling抽真空加注              |
| Duration Time持续时间                                                                                              | 5Ah         | 1 Bit = 1s                            |
| Chanel selection通道选择                                                                                           | 01h/02h/03h | Front/Rear/Both  前轴/后轴/前后轴同时 |
| Service Identifier (P. Response)服务身份标识（肯定应答）                                                           | 71h         |                                       |
| Routine Local Identifier例程本地身份标识                                                                           | D1h         |                                       |

| **Diagnostic Function诊断功能：Start Evac and Fill Routine By Local Identifier根据本地身份标识开始抽真空加注例程** |     |                                 |
|--------------------------------------------------------------------------------------------------------------------|-----|---------------------------------|
| Negative response data (Hex Codes)否定应答数据                                                                     |     |                                 |
| Service Identifier服务身份标识                                                                                     | 7Fh |                                 |
| Request Service Identifier请求服务身份标识                                                                         | 31h |                                 |
| Response Code应答代码                                                                                              | 21h | Busy Repeat Request繁忙重复请求 |

**Remarks备注：**

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat re-quest”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request” shows the ECU, that the request is understood, but the previous
request is still being executed and its result might affect the response to the
requested service. The tester has to send the same request again, until it gets
a final response (positive or negative with LID different from 21).

如果服务执行时间超过50ms，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断设备发送的服务请求，如“7Fh
31h
21h”）诊断设备应重复当前命令，直至电子控制器回复肯定应答（或者非“繁忙（21h）”应答）。

The cycle is defined to cover for following systems ABS. The start message 1
starts the ROM resident routine without pump motor actuation. This routine
switches the outlet valves alternating 1 second on and 1 second off. The entire
evac/fill time depends on the duration of the entire evacuation and fill
process. This final production cycle time can only be determined by trials with
production parts (or parts close to production level) and on line equipment.

此抽真空加注操作适用于防抱死制动系统。序列1启动电子控制器内部程序，该程序主要驱动常闭电磁阀1秒开1秒关间断操作，并不驱动电机运转。抽真空加注时间依据整个产线工位来决定，具体时间应在生产线上来调试确定，所用零件均需为生产件（或接近生产状态）。

Example evac/fill time抽真空加注时间示例：

Evacuation 1抽真空阶段1：45 s

Fine Leak Check泄漏检测：5 s

Evacuation 2抽真空阶段2：5 s

Filling加注：35 s

Entire evac/fill actuation time整个抽真空加注时间：90 s= 5Ahx

It’s not allowed to use the value “00H” for the entire evac/fill time (t1).The
routine is internal limited to a maximum actuation time of 150s (96 Hex). If the
tester request is larger than the allowed 150s (96 Hex), the ECU uses the
maximum allowed value . It is not allowed to repeat the routine twice within a
short time (valves might be damaged by overheating).

在整个抽真空加注过程中时间参数不准设为“00H”，该操作内部限时最大值为150s(96
Hex)，如果诊断设备请求程序执行的时间超过150s(96
Hex)，电子控制器会使用最大允许值。另应避免短期内连续驱动电磁阀，以防损坏电磁阀。

### 4.4.6 Request Evac/Fill Routine Results请求抽真空加注例程结果

| **Diagnostic Function诊断功能：Request Evac/Fill Control Routine Results By Local Identifier根据本地身份标识请求抽真空加注例程结果** |     |                     |
|--------------------------------------------------------------------------------------------------------------------------------------|-----|---------------------|
| Service Identifier(Request)服务身份标识（请求）                                                                                      | 33h |                     |
| Routine Local Identifier例程本地身份标识                                                                                             | D1h |                     |
| Service Identifier服务身份标识                                                                                                       | 73h |                     |
| Routine Local Identifier例程本地身份标识                                                                                             | D1h |                     |
| Status Of the Request Question请求问题的状态                                                                                         | XXh | Result Byte结果字节 |

**Remarks备注：**

Following results are possible最后电子控制器可能会回复以下响应：

“02 Hex” means routine was correct finished. “02 H”说明程序执行成功。

“00 Hex” means routine error during execution. To ensure a correct filled brake
system, the vehicle must be repair bleed. “00
H”说明程序执行出错，为确保制动系统加注完好，请先人工排气。

### 4.4.7 Stop Fill Process停止加注流程

| **Diagnostic Function诊断功能： Stop Evac and Fill Routine By Local Identifier根据本地身份标识停止抽真空加注例程** |     |   |
|--------------------------------------------------------------------------------------------------------------------|-----|---|
| Service Identifier(Request)服务身份标识（请求）                                                                    | 32h |   |
| Routine Local Identifier例程本地身份标识                                                                           | D1h |   |
| Service Identifier (P. Response)服务身份标识（肯定应答）                                                           | 72h |   |
| Routine Local Identifier例程本地身份标识                                                                           | D1h |   |

**Remark备注：**

The routine can be stopped at each time. Before the routine is stopped, it is
necessary to evaluate the status of the routine. If the answer is a “Busy repeat
request, the routine works and no failure is detected.

程序可以随时停止命令请求。在停止程序前，需先评估程序当前状态。如果电子控制器回复“繁忙”，说明程序正在执行，且暂无故障。

### 4.4.8 Pump motor activation to discharge the accumulator chamber 驱动电机抽空蓄能器

| **Diagnostic Function诊断功能： Start Actuator Test Routine By Local Identifier根据本地身份标识开始执行器测试例程** |                                                       |
|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|
| Service Identifier (Request)服务身份标识（请求）                                                                    | 31h                                                   |
| Routine Local Identifier例程本地身份标识                                                                            | D5h                                                   |
| Start the Periodic Control开始周期控制                                                                              | 00h                                                   |
| Without Results无结果                                                                                               | 00h                                                   |
| Actuation动作                                                                                                       | FF FF 00 22 00 00 00 00 00 C8 00 00 00 22 00 00 00 00 |
| Service Code(P. Response)服务代码（肯定应答）                                                                       | 71h                                                   |
| Routine Local Identifier例程本地身份标识                                                                            | D5h                                                   |

**Important Remark重要备注：**

This part can either be done at the end of the fill process, at the end of line
tests or at other station where it is possible to do diagnostics. The actuation
of the pump motor to discharge the accumulator chamber is absolute must!!The
minimum actuation time of the pump motor amounts 2000ms to make sure that the
accumulator chamber is discharged.

这一步可以在加注结束、下线检测或者其他能进行诊断通信的工位进行。加注完成后必须驱动电机2秒抽空蓄能器。

**Remark备注：**

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat re-quest”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request (7Fh 31h 21h)” shows the ECU, that the request is understood, but
the previous request is still being executed and its result might affect the
response to the requested service. The tester has to send the same request
again, until it gets a final response (positive or negative with LID different
from 21)).

如果服务执行时间超过50ms，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断仪发送的服务请求，如“7F
31
21”）诊断仪应重复当前命令，直至电子控制器回复肯定应答（或者非“繁忙（21H）”应答）。

### 4.4.9 Request Actuator Test Routine Results请求执行器控制例程结果

| **Diagnostic Function诊断功能：Request Actuator Test Routine Results By Local Identifier根据本地身份标识请求执行器例程结果** |     |   |
|------------------------------------------------------------------------------------------------------------------------------|-----|---|
| Service Identifier(Request)服务身份标识（请求）                                                                              | 33h |   |
| Routine Local Identifier例程本地身份标识                                                                                     | D5h |   |
| Service Code(P. Response)服务代码（肯定应答）                                                                                | 73h |   |
| Routine Local Identifier例程本地身份标识                                                                                     | D5h |   |
| Control completed控制完成                                                                                                    | 02h |   |

## 4.5 Fine Leak Check (optional)泄漏检测（可选）

| **Fine Leak Check (optional)泄漏检测（可选）** |                                                                                                                              |                    |
|------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|--------------------|
| Evac/Fill Unit  抽真空加注机                   | Conditions 条件                                                                                                              | Value 数值         |
|                                                | vacuum level increase within a determined test time单位时间内真空度上升值：  time for fine leak check t3泄漏检测所需时间t3： |  TBD mbar  TBD sec |

**Remarks备注：**

The fine leak check is performed to detect minor leaks of the entire brake
system. The evac/fill equipment isolates the source and measures the vacuum
increase within a given amount of time and compares this value with given
limits. The timing of this test step must be set to customer related
requirements. This test step does not effect the general evacuation time of the
system, but is an additional test step. Fine leak checks are machine related
test steps and not related to the ABS system. Timing of this test step is
additional to the requirements of the system.

泄漏检测旨在检测整个制动系统的泄漏情况。抽真空加注设备能隔绝压力源，测量给定时间内系统的压力上升值，并与标定值进行对比，检测时间由客户根据加注设备来确定。此步骤不影响加注周期，仅作为附加测试步骤，是与设备相关的测试步骤，与防抱死制动系统无关。此步骤所需时间属系统的额外需求。

Fine Leak Check ok. -\> Continue泄漏检测通过，继续

Fine Leak Check not ok. -\> Set failure message,
continue泄漏检测失败，故障报警，继续

**Fine Leak Test Diagram泄漏检测测试示意图：**

| **Diagram Columns:** |                                                       |                                                                                                                                                                                                                                                                                                                                                                                    |
|----------------------|-------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                              | Remarks                                                                                                                                                                                                                                                                                                                                                                            |
| 1   2                | Measuring point 1 检测点1  Measuring point 2 检测点2  | Vacuum level after evacuation cycle 1 抽真空阶段1后真空度  Vacuum level after leak test time  泄漏检测后真空度  Evaluation of vacuum increase and comparison with given limit values. 真空度对比结果评估。                                                                                                                                                                         |
| t3                   | Time of fine leak check 泄漏检测时间  Evaluation 评估 | Must be defined by the customer in order to meet the total cycle time. 由客户根据系统节拍来确定。  The evaluation is done by calculating the vacuum increase data for a given leak check time. 通过真空度上升数据和泄漏检测结果来评估。 This time is a machine time and is not related to the general required evacuation time of the system. 这段时间属于机器响应时间与系统无关。 |

## 4.6 Evacuation Cycle 2 (optional)抽真空阶段2（可选）

| **Evacuation Cycle 2 (optional)抽真空阶段2（可选）**  |                                             |            |
|-------------------------------------------------------|---------------------------------------------|------------|
| Evac/Fill Unit  抽真空加注机                          | Conditions 条件                             | Value 数值 |
| Evacuation Cycle 2抽真空循环2                         | time for evac 2 cycle t4抽真空循环2时间t4： | TBD sec    |

**Remarks备注：**

The second Evacuation cycle is performed to get back to the initial vacuum level
after the fine leak check. The evac/fill equipment opens the source again and
evacuates for another amount of time to get back to the initial vacuum level.

该阶段旨在将真空度恢复至泄漏检测前的真空度。设备会继续抽真空一段时间用以达到所需真空度。

The timing of this test step must be set to customer related requirements. This
test step does not effect the general evacuation time of the system, but is an
additional test step. It is machine related test steps and not related to the
ABS system. Timing of this test step is additional to the requirements of the
system.

这一步时间由客户确定，且不影响系统总的抽真空时间，仅作为附加步骤，属于机器相关操作，与防抱死制动系统无关。此步骤所需时间属系统的额外需求。

**Evacuation Cycle 2 Diagram抽真空阶段2原理图：**

| **Diagram Columns:** |                                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
|----------------------|----------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                                                   | Remarks                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 1   2                | Start of evac 2 开始抽真空阶段2  End of evac 2  抽真空阶段2结束            | Vacuum level at the end of leak check. 泄漏检测完后的真空度。  Vacuum level after second evacuation cycle. 二次抽真空后的真空度。 The vacuum level must be again below the certain levels after evac1. 此时真空度应比阶段1完成后的真空度还低。                                                                                                                                                                                                                          |
| t4                   | Evaluation Fine Leak Test and Evacuation Cycle 2 评估泄漏检测与抽真空阶段2 | This time is a machine time and is not related to the general required evacuation time of the system. 这步时间与机器有关，与系统抽真空通常所需时间无关。 The cycle is used to get down to the initial vacuum level again after the fine leak test has been performed. 该步旨在恢复至泄漏检测前真空度。 This test steps are optional, not related to the basic system process but to the process set up of the evac/fill equipment. 该步可选，具体视抽真空加注设备而定。 |

## 4.7 Fill Cycle加注循环

| **Fill Cycle加注循环**       |                                                                                                                                                                                                                                                                                                      |                                                                               |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|
| Evac/Fill Unit  抽真空加注机 | Conditions 条件                                                                                                                                                                                                                                                                                      | Value 数值                                                                    |
| Fill cycle 加注循环          | minimum pressure level on the master cylinder reservoir (absolute)主缸油壶压力最小值（绝对值）：  maximum pressure level on the master cylinder reservoir主缸油壶压力最大值：  minimum pressure level on the wheel calipers (to be achieved)轮缸卡钳压力最小值（目标值）：  fill time t5加注时间t5： |  \> 3 bar  limited due to brake reservoir 由制动液油壶确定   TBD bar  TBD sec |

**Remarks备注:**

The evac/fill unit must be capable to achieve a sufficient fill pressure at the
master cylinder reservoir in order to get a proper fill and pump supply due to
the pressure drop of each component. The fill time is a function out of the
orifice sizes of the hydraulic modulator and the volumes of the wheel calipers,
the pipes and hoses and must be set by running trials with production level
components, using the on line equipment. Valves will be activated during the
entire fill cycle.

抽真空加注设备在主缸油壶处加压，使制动液能从主缸流进轮缸和管路中。生产线设备调试加注时间需考虑前后卡钳的液压模块孔径大小，管路长度，接头连接等因数，所以加注时间要通过实验来确定。整个加注过程中电磁阀一直处于工作状态。

Filling ok. -\> Continue加注完成，继续

Filling not ok. -\> Abort加注失败，中断测试

**Filling Diagram加注原理图：**

**Remarks备注：**

| **Diagram Columns:** |                                                            |                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|----------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                                   | Remarks                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 1                    | Start of fill cycle 开始加注  Diagnostic routine 诊断程序  | Evac/fill equipment starts the fill cycle. 设备开始加注循环  Diagnostic equipment executes the valve activation’s. Pump activation’s are not required. 诊断仪只驱动阀动作，不需驱动电机。  The routine cycles the valves during the entire evacuation and fill cycle. This is required to evacuate the secondary circuits of the hydraulic modulator. 整个抽真空加注过程中阀一直处于工作状态，这样可以确保液压模块的二级回路也能加注满制动液。 |
| 2                    | Front caliper fill 前卡钳加注                              | Time when front calipers are filled. 前卡钳加注满时间。                                                                                                                                                                                                                                                                                                                                                                                        |
| 3                    | Rear caliper fill 后卡钳加注                               | Time when rear calipers are filled. 后卡钳加注满时间。                                                                                                                                                                                                                                                                                                                                                                                         |
| 4                    | End of fill cycle 加注结束                                 | End of fill cycle (with minimum reserve time).  加注结束（最短时间内）。                                                                                                                                                                                                                                                                                                                                                                       |
| t5                   | Fill Timing 加注时间                                       | The required fill time must be determined by running trials with production level brake components using the on line evac/fill equipment. A difference may occur by the circuit structure and orifice size at the time of achieves the pressure level of Front circuit and Rear circuit. 加注时间应在生产线上调试确定，由于管路长度和孔径大小不同，前后轮回路达到压力值所需时间不同。                                                          |

## 4.8 Pressure Leak Check (optional)压力泄漏检测（可选）

| **Pressure Leak Check (optional)压力泄漏检测（可选）** |                                                                                                                                                                                                                                  |                             |
|--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------|
| Evac/Fill Unit  抽真空加注机                           | Conditions 条件                                                                                                                                                                                                                  | Value 数值                  |
| Pressure leak check 压力泄漏检测                       | Pressure level decrease within a determined test time指定时间内压力下降值：  time for leak check t6泄漏检测时间：  maximum pressure level on the master cylinder reservoir (to be achieved)主缸油壶达到最大压力所需时间（TBD）： |  TBD bar  TBD sec   TBD sec |

**Remarks备注:**

The pressure leak check is performed to detect leaks of the entire brake system.
The evac/fill equipment isolates the source and measures the pressure drop
within a given amount of time and compares this value with given limits. The
timing of this test step must be set to customer related requirements. This test
step does not effect the general fill cycle of the system, but is an additional
test step. Pressure leak checks are machine related test steps and not related
to the ABS system. The valves and pump motor must be turned off during this
step. Timing of this test step is additional to the requirements of the system.

泄漏检测旨在检测整个制动系统的泄漏情况。抽真空加注设备能隔绝压力源，测量给定时间内系统的压降，并与标定值进行对比，检测时间由客户根据加注设备来确定。此步骤不影响系统加注通常所需时间，仅作为附加测试步骤，是与设备相关的测试步骤，与防抱死制动系统无关，此时应关闭电磁阀和电机。此步骤所需时间属系统的额外需求。

Pressure Leak Check ok -\> continue泄漏检测通过，继续

Pressure Leak Check not ok -\> continue, set failure
message泄漏检测失败，故障报警

**Pressure Leak Check Diagram压力泄漏检测原理图：**

| **Diagram Columns:** |                                            |                                                                                                                                                           |
|----------------------|--------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                   | Remarks                                                                                                                                                   |
| 1                    | End of fill cycle 加注结束                 | Front/rear calipers are filled.  前/后卡钳已加注满。                                                                                                      |
| 2                    | Start of pressure leak check 开始泄漏检测  | Time to start the pressure leak check and to pick up the pressure level. 开始泄漏检测，记录开始压力值。                                                   |
| 3                    | End of pressure leak check 泄漏检测结束    | Time to end the pressure leak check and to pick up the pressure level again for evaluation of the pressure drop. 结束泄漏检测，记录结束压力值以评估压降。 |
| 4                    | Relax to atmospheric pressure 恢复至大气压 | Evac/fill equipment to release fill pressure. 设备移除加注压力。                                                                                          |
| t6                   | Time of pressure leak check 泄漏检测时间   | Must be defined by the customer in order to meet the total cycle time. 由客户确定。                                                                       |

## 4.9 Top Off Reservoir (Scavenging)油壶复压

| **Top Off Reservoir (Scavenging)油壶复压** |                                                                                           |            |
|--------------------------------------------|-------------------------------------------------------------------------------------------|------------|
| Evac/Fill Unit 抽真空加注机                | Conditions 条件                                                                           | Value 数值 |
| Top off reservoir (Scavenging) 油壶复压    | Set reservoir level to correct limits time for top off t7将油壶压力回复到指定值所需时间t7 |  TBD sec   |

**Remarks备注:**

The reservoir must be filled to a certain level. The timing of this test step
must be set to customer related requirements.

壶口液位必须加注到指定位置。这一步骤所需时间由客户需求确定。

Level ok. -\> continue液位正常，继续

Level not ok. -\> continue, set failure message液位异常，故障报警

**Top off (Scavenging) Diagram复压原理图：**

**Remarks备注:**

| **Diagram Columns:** |                                                                                                                                   |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|----------------------|-----------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Item no.             | Activity                                                                                                                          | Remarks                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 1   2                | Top off the reservoir 复压  End of top off  复压结束                                                                              | Suck or fill reservoir fluid.  抽取或加注制动液。  The reservoir fluid must be within the given limits. 油壶应达到指定液位。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 3                    | End of cycle 循环结束                                                                                                             | Evaluate the evac/fill result.  评估加注结果。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| 4         5          | Write Process Byte 写加注状态        Erase fault code memory of the ECU (optional) 清除故障代码        Diagnostic timing 诊断时间 | Diagnostic equipment to write the process byte (ok/not ok) information into the ECU. 诊断设备把加注结果写进电子控制器。 The process byte can be verified at the end of line test of the system to ensure, that the secondary circuits of the modulator have been energized during this process and have been properly filled. 在下线检测中，需要验证加注状态来确定二级回路已被正确加注。  Diagnostic equipment to erase the fault code memory of the ECU. During the evac/fill process fault codes may have been stored in the ECU. 诊断设备清除电子控制器故障代码，加注过程可能会存储故障代码。 To erase the fault code memory depends onto the remaining cycle time and may also be included in the end of line testing of the system.根据剩余的循环时间决定是否清除故障代码，也可以留到下线检测中清除。  Numbers 4 to 5 can be included into this step in order to minimize the total cycle time. 第4到5步可包含在这一阶段中以缩短整个循环时间。 |
| t7                   | Time of Top off reservoir 油壶复压时间                                                                                            | Must be defined by the customer in order to meet the total cycle time. 由客户确定。                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |

## 4.10 Diagnostics at the end of the fill and evacuation process 抽真空加注结束后诊断

### 4.10.1 Write Process Control Byte写加注状态值

| **Diagnostic Function诊断功能：Write Data By Local Identifier通过本地身份标识写数据** |                                                              |                                        |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------|----------------------------------------|
| Service Identifier服务身份标识                                                        | 3Bh                                                          |                                        |
| Routine Local Identifier本地身份标识                                                  | 20h                                                          |                                        |
| Status状态                                                                            | XXh                                                          | Status of Filling加注状态              |
| ECU Data to be written待写的ECU数据                                                   |                                                              |                                        |
| 55h AAh FFh                                                                           | Filling Successfully Filling Not Successfully Delivery State | 加注成功 加注失败 交付状态（初始状态） |
| Positive Response肯定应答：                                                           |                                                              |                                        |
| Service Code服务代码                                                                  | 7Bh                                                          |                                        |
| Routine Local Identifier本地身份标识                                                  | 20h                                                          |                                        |

**Remarks备注:**

The ECU is shipped to the customer assembly line with a predefined process byte:
“FFHex”. This number is reserved by SFB. In case of a non successful
communication this data will still stay in the EEPROM of the ECU (“incorrect”).
The EEPROM location is defined by SFB.

电子控制器由宁波赛福运至客户工厂时，加注状态初始值为“FFH”，这个值是宁波赛福设定的初始值，在没有通信（写加注状态值）之前，这个初始值始终在电子控制器的存储器中，其具体地址由宁波赛福定义。

### 4.10.2 Clear fault code memory (optional)清除故障代码（可选）

| **Diagnostic Function诊断功能：Clear Diagnostic Information清除故障代码** |      |
|---------------------------------------------------------------------------|------|
| Service Code (Request)服务代码（请求）                                    | 14h  |
| Group Of DTC High Byte诊断故障码组高字节                                  | FFh  |
| Group Of DTC Low Byte诊断故障码组低字节                                   | 00h  |
| Service Code (Response)服务代码（应答）                                   | 54h  |
| Group Of DTC High Byte诊断故障码组高字节                                  | FFh  |
| Group Of DTC Low Byte诊断故障码组低字节                                   | 00h  |
| ECU Data to be evaluated待评估的ECU数据                                   | None |

**Remarks备注:**

See ECU data in diagnostic specification for details. This step is an optional
step for all systems. Depending to the adaptation onto the system and the
installation of the vehicle harness, fault codes may have been stored in the ECU
during the evac/fill process. This step allows erasing of the fault code memory
of the ECU. Different actual fault codes cannot be cleared. It’s only possible,
if the timing allows to be integrated in the process. Otherwise it must be
included in other diagnostic test equipment on line such as the end of line
testing. Erasing the fault code memory can only be performed if the diagnostic
mode is not ended with the command “end of diagnosis”, but by turning the power
supply off while the ECU is in diagnostic mode. Adding this test step into the
evac/fill procedure is upon customer request.

此步可选，电子控制器数据的详细内容请参见“诊断描述文档”。在抽真空加注过程中是否会产生故障与电气接线方式有关。此步操作可以擦除故障代码，有些特殊故障将无法擦除。如果时间允许，此步操作可集成进抽真空加注过程，否则应由其他诊断设备来进行清除故障代码操作，如下线检测工位。在诊断模式下，才可擦除故障代码；当直接断电退出诊断模式时并不能清除故障代码。是否把此步骤加进抽真空加注循环由客户确定。

## 4.11 End of Cycle/ Handling循环结束/操作

| **End of Cycle / Handling循环结束/操作**                                                                          |                                               |
|-------------------------------------------------------------------------------------------------------------------|-----------------------------------------------|
| Operator 操作员                                                                                                   | Diagnostic Unit / ECU 诊断单元/电子控制器     |
| Turn Ignition (Power supply) OFF 点火关 Remove electrical connection 移除电气连接线 Remove fill head 移除加注管路 | Turn external power supply OFF 关闭外部电源   |

**Remarks备注：**

Turning off the power supply or the ignition depends onto the design of the
equipment. In case of an external power supply, the equipment has to turn off
prior to the disconnection of the harness by the operator.

In case of using the vehicle battery, the operator has to turn off the ignition
prior to disconnecting the harness from the system. In order to completing to
clear the DTC in this process, regardless of the external power supply or the
vehicle battery , please turn off the ignition firstly, after at least 2
seconds, then turn off the power supply.

关闭电源或熄灭点火开关视系统而定，如果是外部供电，先断电再拔出电气接线；如果使用车载电池，请先熄火再拔下电气接头。若希望在抽真空加注过程上完成清除DTC操作，无论外部供电还是车载供电，请先关闭点火开关，延迟至少2s后再断电。

# 5 Valve protective measures and hydraulic data of the ABS system防抱死制动系统电磁阀保护及液压模块数据

## 5.1 Valve protective measures for all projects电磁阀保护措施

| **Valves电磁阀** | **Evac/fill routine抽真空加注程序**                       |
|------------------|-----------------------------------------------------------|
| NO 4,06 Ω        | Not actuated无操作                                        |
| NC 4,06 Ω        | 1s on/1s off; limited to 150s 1秒开1秒关，最长不超过150秒 |

**Remarks备注：**

All valve protective measures automatically active. These protective measures
cannot be disabled. With using of the described ROM resident “evac/fill” routine
the standard valve protection measures (up/down counters) are disabled to
realize an actuation time ≤150s. The valves are protected by cycling with 1s on
/ 1s off. It is not allowed to repeat the routine several times without a
waiting time to cool the valves!

所有阀保护措施都是自动运行的，这些保护措施无法关闭。通常的阀保护措施在执行电子控制器内的抽真空加注程序时无法识别阀得电时间是否超过150秒。电磁阀通过1秒开1秒关来保护其不被烧坏。重复执行此程序时应先冷却一段时间，否则会损坏电磁阀。

## 5.2 Hydraulic data (important for evac/fill)液压数据（非常重要）

| **Specific hydraulic data详细液压数据**                       | **Value数值** |
|---------------------------------------------------------------|---------------|
| Volume of primary circuit per circuit基础回路容量：           | TBD           |
| Volume of secondary circuit per circuit二级回路容量：         | TBD           |
| Dead space volume of one pump element泵死腔容积：             | TBD           |
| Inlet valve orifice size (front axle)前轴常开阀孔径：         | TBD           |
| Inlet valve orifice size (rear axle)后轴常开阀孔径：          | TBD           |
| Outlet valve orifice size (front axle)前轴常闭阀孔径：        | TBD           |
| Outlet valve orifice size (rear axle)后轴常闭阀孔径：         | TBD           |
| Maximum allowed dry run time of the pump elements泵空转时间： | \<60s         |

**Remarks备注：**

All volume values are rounded. For further information about the valve orifice
sizes, see the dependent project specific hydraulic technical customer
documentation (HCU-TCD).

所有容积值都已圆整，阀孔径尺寸详细内容请见相关技术文档。

# 6 Process Timing流程时间

## 6.1 Timing for Valve Activation’s操作时间

| **Evacuation and Fill Cycle抽真空加注循环** |                                                                            |
|---------------------------------------------|----------------------------------------------------------------------------|
| Valve Cycling 阀动作时间                    | Automatically done from the ECU (ROM resident function) 电子控制器自动运行 |
| Pump Motor 电机泵                           | A pump actuation is not required 无需驱动泵                                |

**Remarks备注：**

The activation time of the outlet valves must be limited. It is dependent on the
supply voltage.

常闭电磁阀驱动时间是受限的，视供电电压而定。

## 6.2 Timing for Evacuation Cycle抽真空循环时间

| **Timing for evacuation cycle抽真空循环时间**                                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|-------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum vacuum level to be achieved at the calipers卡钳应达到的真空度最小值： | Time to reach minimum vacuum level at the front calipers前卡钳达到真空度最小值时间：                                                                                                                                                                                                                                                                                                                                                                 | Time to achieve minimum possible vacuum level at the rear calipers后卡钳达到真空度最小值时间：                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| \<10 mbar                                                                     | Time to reach the minimum vacuum level at the calipers is a function of the volumes of the calipers, the pipes and hoses and the orifice sizes of the hydraulic modulator. It is also dependent on the evac equipment. 达到真空度时间与卡钳容量、油管长度、液压模孔径大小有关，与抽真空设备息息相关。 Evac times are usually in the range of 30 to 60 seconds and should be defined by trials. 常见抽真空时间是30到60秒，具体时间根据调试来确定。    | Time to reach the minimum achieve vacuum level at the calipers is a function out of the volumes of the calipers, the pipes and hoses and the orifice sizes of the hydraulic modulator. It is also dependent on the evac equipment.  达到真空度时间与卡钳容量、油管长度、液压模块孔径大小有关，与抽真空设备息息相关。 Achieving a lower vacuum level, will extend the evacuation time. The timing must be set by trials. To achieve a vacuum level less than 10 mbar depends onto the capability of all components of the entire brake system 达到较低的真空度将延长抽真空的时间，具体时间根据调试来确定。能否达到小于10 mbar压力要视各零件状况而定。 |

**Remarks备注:**

For optimization, all diagnostic functions can be integrated into the first 10
seconds of the evacuation cycle. This will extend the evacuation time by about 2
to 3 seconds, but will reduce the entire cycle time. All used components have to
be absolute dry. In case of used wet components, it is not guaranteed that the
system is complete evacuated.

为了优化工序，所有诊断功能可以在抽真空加注循环的前10秒内完成。这样会使抽真空多耗时2到3秒，但能减少整个循环时间。所有零件都必须完全干燥，如果零件是湿的，则不能保证系统完全抽真空。

## 6.3 Timing for Vacuum Leak Check抽真空泄漏校验时间

| **Timing for vacuum leak check抽真空泄漏校验时间** |                                                                                                                                                                                                                                                |
|----------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maximum vacuum level increase最大真空度增量：      | Time for vacuum leak check抽真空泄漏检测时间：                                                                                                                                                                                                 |
| TBD mbar                                           | Time for the vacuum leak check is set by customer specifications. 时间由客户定。 This step is optional and not ABS related. 这一步是可选的且与防抱死制动系统无关。 A typical time for a leak check is about 5 seconds. 一般泄漏检测时间为5秒。 |

## 6.4 Timing for Evacuation Cycle 2抽真空阶段2时间

| **Timing for evacuation cycle 2抽真空阶段2时间**                  |                                                                                                                                                                                                                                             |
|-------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum vacuum level increase (at the wheels)轮缸最小真空度增量： | Time for evacuation cycle 2抽真空阶段2时间：                                                                                                                                                                                                |
| \<10 mbar                                                         | Time for the evacuation cycle 2 is set by customer specifications. 时间由客户定。 This step is optional and not ABS related. 这一步是可选的且与防抱死制动系统无关。 A typical time for a leak check is about 5 seconds. 一般检查时间为5秒。 |

## 6.5 Timing for Fill Cycle加注时间

| **Timing for fill cycle加注时间**                              |                                                                                                                                                                                                                                                                                                                                                                                                                                 |                                                                                                                                                                                                                                                                                                                                                                                                                               |
|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Minimum pressure to be achieved at the reservoir油壶最小压力： | Time to reach minimum pressure level at the front calipers前卡钳压力到达所需时间：                                                                                                                                                                                                                                                                                                                                              | Time to reach minimum pressure level at the rear calipers后卡钳压力到达所需时间：                                                                                                                                                                                                                                                                                                                                             |
| 3 bar ≤ P ≤ max. pressure (dependent on reservoir由油壶决定)   | The time to reach the minimum pressure level of 3 bar at the front calipers is a function out of the volumes of the calipers, the pipes and hoses and the orifice sizes of the hydraulic modulator. A typical timing for the front wheels is 20 to 25 seconds. The timing must be defined by trials. 前卡钳达到最小压力3bar所需时间与卡钳容量、油管长度、液压模块孔径大小有关。一般前轮加注要20到25秒，具体时间可通过调试确定。 | The time to reach the minimum pressure level of 3 bar at the rear calipers is a function out of the volumes of the calipers, the pipes and hoses and the orifice sizes of the hydraulic modulator. A typical timing for the rear wheels is 30 to 50 seconds. The timing must be defined by trials. 后卡钳达到最小压力3bar所需时间与卡钳容量、油管长度、液压模块孔径大小有关，一般后轮加注要30到50秒，具体时间可通过调试确定。 |

## 6.6 Timing for Pressure Leak Checks泄漏压力测试

| **Timing for pressure leak check泄漏压力测试** |                                                                                                                                                                                                                                                                   |
|------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Maximum pressure level drop最大压降：          | Time for pressure leak check泄漏测试时间：                                                                                                                                                                                                                        |
| TBD bar                                        | The time for both pressure leak checks are set by customer specifications.  客户指定2次泄漏测试时间。 This step is optional and not ABS related. A typical time for a leak check is about 3 to 5 seconds. 这一步可选，且与ABS系统无关，典型泄漏测试时间为3到5秒。 |

**Remarks备注：**

For optimization, all diagnostic functions can be integrated within the pressure
leak check and/or the reservoir top off cycle.

为了优化整个流程，诊断服务可以集成进压力泄漏或者油壶复压操作中。

## 6.7 Timing for Reservoir Top Off (Scavenging)油壶复压时间

| **Timing for reservoir top off (scavenging)油壶复压时间** |                                                                        |
|-----------------------------------------------------------|------------------------------------------------------------------------|
| Set reservoir fluid level设置油壶制动液液位：             | Time for top off油壶复压时间：                                         |
| TBD ccm                                                   | Time for the top off set by the evac/fill unit. 抽真空加注油壶复压时间 |

**Remarks备注：**

For optimization, all diagnostic functions can be integrated within the pressure
leak check and/or the reservoir top off cycle.

为了优化整个流程，诊断服务可以集成进压力泄漏和（或）油壶复压操作中。

## 6.8 Timing for Operator Handling操作人员操作时间

| **Timing for operator handling操作人员操作时间**                                                                                   |                                                                                                                                                                                                                                                                                          |
|------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Fill head adaptation加注头连接：                                                                                                   | Electrical adaptations电气连接：                                                                                                                                                                                                                                                         |
| The time for adaptation and removing the fill head is identical to a non ABS system. 加注头连接和拔掉与非防抱死制动系统有所区别。  | The time for the electrical adaptation and disconnection is an additional operator handling. 电气接线和拔线时间另算。 The required timing depends onto the Principle of the adaptation and the accessibility of the electrical connections. 所需时间因接头形式和电气接线方式不同而不同。 |

# 7 Failure Handling故障处理

| **Failure Handling故障处理**                               |                                                                                                                                                                       |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Type of failure故障类型：                                  | Failure Indication , Failure Handling故障识别及处理：                                                                                                                 |
| Evac/fill equipment 加注设备 Diagnostic equipment 诊断设备 | Set failure indication, put tag on the vehicle -\>Repair 故障报警，车辆做标识-排气 Set failure indication, put tag on the vehicle -\>Repair 故障报警，车辆做标识-排气 |

**Remarks备注：**

In case of a failure at all diagnostic during the evac/fill process, the
standard evac/fill cycle can be continued. But the evac/fill equipment must set
a failure message to identify that the system needs to be repair bled.

如果抽真空加注过程中出现诊断故障，抽真空加注可以继续执行，但设备应提示错误报警，用以提示设备需要进行人工排气。

In case of a detected failure during the evacuation process it is also possible
to interrupt the on line evacuation process (dry system must be guaranteed). In
this case it is possible to repeat a complete second evacuation and fill process
off line. The foundation brake circuits will be filled with the exception of the
secondary circuits of the modulator. This makes it easier to repair bleed the
entire system.

线上抽真空过程出现故障时，可能会中断抽真空操作（保证系统是干燥的），此时可以在线下再次执行抽真空加注操作。基础制动回路会被加注制动液（二级回路仍为空），这样排气相对会容易些。

In case of a general failure of the system (i.e. leakage or machine failure) the
filling will not be successful and the cycle must be aborted and the process
failure must be indicated. In order to avoid any damages of the system, it is
recommended not to operate the system until it is bled at the repair area.

当系统出现错误时（如泄漏或机器故障），加注即失败，此时加注循环应中断，加注故障应该能被识别出来。为防止损坏系统，请将车辆移至人工排气处再进行相关操作。

# 8 Data Specifications数据指标

## 8.1 Hydraulic Data Specifications液压数据规范

| **Hydraulic data specifications液压数据规范**                                                                                             |                                                                                                                                                                                                                                                                    |
|-------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Measurement point测量点： -Evac/fill equipment (fill head)壶口抽真空压力  -Wheel Calipers轮缸卡钳  -Fill Pressure (Fill head)壶口加注压力 | Vacuum/Pressure Value真空度/压力值： ≤ 2 mbar  ≤ 10 mbar  3 bar ≤ P fill ≤ p max depend on brake fluid reservoir因制动液油壶来定                                                                                                                                   |
| Evacuation Time抽真空时间：   Fill Time加注时间：   Evac and fill equipment抽真空加注设备：                                               | Time to achieve minimum \<10 mbar at all calipers. 所有卡钳最小压力不高于10mbar所需时间。  Time to achieve fill pressure at all calipers. 卡钳达到加注压力所需时间。  Evacuation and fill times must be set as constant parameters. 抽真空加注时间必须标定为定值。 |

**Remarks备注:**

All brake components must be dry and capable to achieve the minimum specified
vacuum level in combination of the entire brake system. For vacuum filling the
brake fluid should be pre-treated, that means it should contain \< 10% of the
maximum soluble air at room temperature and standard atmospheric pressure.

干式状态下制动系统内的所有制动零件必须能够达到最小真空度。抽真空加注的制动液要经过预处理，使常温常压下可溶性气体小于10%。

## 8.2 Electrical Data Specification电气数据规范

| **Electrical data specifications电气数据规范** |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Power supply unit 供电单元：                   | Voltage电压[V]：11,5 V ≤ U supply ≤ 14 V (measured at the connector of the ECU with a sense wire to control the voltage! 端口检测电压)  It must be guaranteed that the voltage never drops off to less than 10 V ! To guarantee that the voltage never drops off to less than 10V, SFB recommended to use a additional car battery as a buffer. The car battery must be loaded by the power supply and checked periodical. All valve current values are calculated in case of if the valves are actuated with 100% duty cycle!!! 任何时候电压都不可低于10V，基于此宁波赛福建议外加一个车载电池（由外部电源供电）做备用电源，并适时监控。电磁阀的电流需要计算，以防电磁阀以100%占空比运行。 |
| Current consumption (at 12V) 电流消耗：        | ECU电子控制器：≤ TBD A  Solenoid NC valve常闭电磁阀线圈：2,8 A  ABS system (during evac/fill)ABS系统（在抽真空加注过程中）： 5,6 A (2 x 2,8 A; to the same time) (TBD)  Pump motor start up (peak for 20-50ms)电机启动： ≤ 50 A (depends on the used RP system specific) 视系统而定   Pump motor (during evac/fill)电机运转（抽真空加注过程中）：8 A (TBD)                                                                                                                                                                                                                                                                                                                                 |

**Connector design连接器设计：**

The fill equipment connector represents a very important function at this
process. That’s why following conditions must be absolute guaranteed to avoid
communication problems and damaged ECU’s.

加注设备电气接头在这一进程中起着非常重要的作用，为避免通信故障和损坏电子控制器，请务必满足以下条件：

The connector must be an industrial one, not a production level part in order to
allow a multiple use. The connector must be constructed in a way, where it is
not possible to damage (caused by scraping or bending) the Pin’s of the ECU.

连接器不能采用生产件，必须采用产品件，以具备多功能用途。连接器必须安装适当，保证在摩擦和弯曲情况下ECU针脚不被损坏。

Before the electrical contact is reached, the fill equipment connector must be
guided at the guide grooves at the ECU (details look in the attached
drawings-the original drawing can be demanded at SFB to get all important
detailed information of the ECU connector).

加注设备连接件头应沿着电子控制器的引槽走线，之后再进行电气连接（详见电子控制器连接器图纸，可得到电子控制器连接件所有重要信息）。

The Pin’s should be designed as spring loaded (e.g. company Ingun) or flat
socket (e.g. company Odu) parts to avoid any damages at the vehicle or ECU
connector.

针脚处需装有弹簧或者套头以防损坏车辆或者电子控制器连接器。

Connector design must be adapted onto system (ECU) connector design or
diagnostic connector design and may vary according to the configuration.

连接件设计要与电子控制器系统连接件和诊断连接件相匹配，根据不同结构和配置而改变。

A good access to the ECU connector is required. Following conditions must be
guaranteed连接器要可靠，需满足以下条件：

. contact resistance端子阻抗 ≤ 10 mΩ

. contact separation端子响应时间 ≤ 10 µs

. diagnostic line must shielded诊断线必须屏蔽

**Remarks备注：**

The equipment must be capable to meet the above requirements. The specified data
must be achieved at the ECU connector. The source must be strong enough to avoid
voltage drops across the wiring. The diagnostic link should not exceed a maximum
length of 10 meters.

设备连接件要满足以上要求，电子控制器连接件需满足以上数据指标。电源需提供足够功率用以补偿线路损耗产生的压降，诊断线束长度不可超过10米。

# 9 Electrical Adaptations电气连接

There are two different possibilities for the electrical adaptation onto the
system.系统电气连接有2种方式。

## 9.1 Adaptation onto the diagnostic link of the vehicle车辆诊断接口

| **Handling操作**                                                                                                  |                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
|-------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator 操作者                                                                                                   | Remarks 备注                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| Adapt diagnostic link连接诊断口  Adapt power supply (if necessary)供电（如果需要）         Turn Ignition ON点火开 |   Either in dashboard or engine compartment , external power supply (if necessary: in connection with a external car battery) is required either to support the vehicle battery or in case the battery is not already installed or connected(optional)  无论是仪表盘或者发动机舱，需要外部供电（如有可能：连接一个外部车载电池）来支持车载电池或者在没有安装或连接电池的时供电。  To power up the system and initialize the ECU. 给系统供电和初始化电子控制器。 |

## 9.2 Adaptation onto the ECU connector连接电子控制器接插件

| **Handling操作**                                                                                                                                                                                                                                                                                                                                                           |                                                                                                                                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator 操作者                                                                                                                                                                                                                                                                                                                                                            | Remarks 备注                                                                                                                                                                                                                |
| Adapt connector onto the ECU 连接ECU接插件                                                                                                                                                                                                                                                                                                                                 | Details about the connector design look above and below! The external power supply and the diagnostic link is included in the connector terminals. 接插件的设计细节请参照上下文。外部电源供电和诊断线已包含在接插件端子中。 |
| ABS Connector (18- PIN) 18针端子连接器： Terminals wiring required 端子接线要求： 1. power supply to the valves (PIN 9) 电磁阀供电 2. power supply to the pump motor (PIN 18) 电机供电 3. Ignition (PIN 14) 点火 4. ground connection of the ECU (PIN 1) 电子控制器接地 5. ground connection of the pump motor (PIN 10) 电机接地 6. diagnostic line: K-Line (PIN 7)诊断K线 |                                                                                                                                                                                                                             |

# 10 Equipment Information设备相关信息

**Evac/Fill Unit Design抽真空加注机设计：**

The process is designed to be performed on standard evac/fill equipment.

该流程用于标准抽真空加注设备。

**Diagnostic Information诊断信息：**

An additional diagnostic unit is required to run the ROM resident functions. The
diagnostic computer should be as close to the vehicle as possible to avoid
communication problems. The timing (time gaps between messages and bytes within
messages) should be set close to the minimum possible limits in order to
minimize the process time.

需要一台诊断设备来来运行程序，诊断电脑尽可能接近车辆，以防距离造成通信故障。通信时间间隔参数应与最小值接近，以缩短测试时间。

**Process Byte流程字节：**

The final definition of the process byte data must be taken from the customer
requests.

流程字节定义由客户决定。

**Editor menus编辑菜单：**

ECU Identification codes may change during production due to updates of software
revisions. It is important to set up the software program to add identification
numbers by using an editor menu. The timing of the ROM resident functions should
be designed to be modified within an editor menu.

电子控制器的身份标识信息会随生产软件的修改而发生变更。建议在测试软件中设置菜单编辑功能用于快捷更改身份标识信息。可通过菜单编辑电子控制器中相关服务执行时间。

**Test protocol测试准则：**

In case of an ok test result, a print out (“test passed”) is sufficient. In case
of a not ok test result, a failure protocol must be printed out. This protocol
must include all test data of the test step that failed in order to allow a
better failure analysis. An entire test protocol of all test results must be
available on request.

如果测试结果正确，需打印“测试通过”；如果测试结果不正确，错误信息必须打印出来。测试描述中必须包括错误测试步骤及其数据，方便故障分析。所有测试数据必须随时可视跟踪索引查阅。

**Vehicle conditions车辆条件：**

The battery must be charged properly in order to allow a sufficient power supply
to the system respectively the external power supply must ensure a stable
voltage level without insufficient voltage drops across wiring.

电池必须保证电量充足，如有外部供电设备，请确认电压电流能力能满足系统要求，以防使用过程中线束压降导致电压跌落，从而影响测试。

# 11 Attachments附件

## 11.1 Hydraulic Circuit Diagrams液压原理图

## 11.2 Electric Wiring Diagram Customer with ABS电气接线图纸

See Technical Customer Document.

参见客户技术文档。

## 11.3 ABS connector drawing (18-pin connector)端子连接器图纸

See Technical Customer Document.

参见客户技术文档。
