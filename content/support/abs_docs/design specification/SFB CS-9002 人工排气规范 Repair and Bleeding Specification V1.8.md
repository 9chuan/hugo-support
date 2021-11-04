---
title: SFB CS-9002 人工排气规范
linktitle: SFB CS-9002 人工排气规范
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---
## 更新记录
|                      | CUSTOMER SPECIFICATION 客户规范                |                 |
|----------------------|------------------------------------------------|-----------------|
| SPEC NO.SFB CS- 9002 | Repair and Bleeding Specification 人工排气规范 | SF10 ABS System |
| Version: V1.8        |                                                |                 |

**Project Information**

| Customer客户： Vehicle车型：                                |                                                                                                      |
|-------------------------------------------------------------|------------------------------------------------------------------------------------------------------|
| System系统： Channel通道：                                  | ABS  2 Channel System两通道管路/1 Channel System单通道管路                                           |
| Diagnosis诊断： Kind of communication通信： Equipment设备： | Based on Customer KWP2000基于KWP2000协议 K-Line K线 Off line Repair Bleeding Machine线下人工排气设备 |

**Release Department**

| **Department** | **Date** | **Signature** |
|----------------|----------|---------------|
|                |          |               |

**History list:**

| **Version** | **Edit**    | **Date**   | **Descriptions**                                             |
| ----------- | ----------- | ---------- | ------------------------------------------------------------ |
| 1.0         | Taylor Wang | 2015.04.09 | Draft                                                        |
| 1.1         | Taylor Wang | 2015.11.10 | Release                                                      |
| 1.2         | Taylor Wang | 2015.11.26 | Change Record Local Identifier “01h” to “04h” in chapter “Check System Status”. |
| 1.3         | Taylor Wang | 2016.01.12 | Update “Process Sequence”; Update “Diagnostic commands to bleed system”; |
| 1.4         | Rich Chen   | 2016.01.25 | Update “Schematically Repair Bleeding Diagram with all used ROM Resident Function” |
| 1.5         | Rich Chen   | 2016.03.30 | 1-Modify maximum allowed dry run time of the pump elements from 150ms to 60s 2-Modify the request message of repair bleeding: add the sixth reserved byte. |
| 1.6         | Rich Chen   | 2016.05.30 | Change delivery stat of the hydraulic filling indicator from 00H to FFH in the section 4.4.2. |
| 1.7         | Rich Chen   | 2016.12.01 | 修改第7章错误中文，“等待5秒钟”为“等待5分钟”                  |
| 1.8         | Rich Chen   | 2017.05.22 | 1-Document standardization and “PS3002” to “SFB CS-9002” 2-Modify some details in the section 8.2. |

# 1 General 总述

## 1.1Acronyms缩写

```
ABS antilock braking system防抱死制动系统
ABS-WL ABS warning lamp防抱死故障报警灯
NC Normally Close valve常闭电磁阀
BLS brake light switch刹车灯
DTC diagnostic trouble code故障代码
ECU electronic control unit电子控制单元
NO Normally Open valve常开电磁阀
FA front axle前轴
FCM fault code memory故障代码缓存
RA rear axle后轴
ACC accumulator蓄能器
RLI record local identifier本地身份标示
UM pump motor feedback电机反馈
WSS wheel speed sensor轮速传感器
```

## 1.2 Diagnostic Document

| **NO**      | **Version** | **Description**                                               |
|-------------|-------------|---------------------------------------------------------------|
| SFB CS-9010 | V1.8        | 诊断功能描述文档 Diagnosis Function Description Specification |
|             |             |                                                               |

## 1.3 Attachments (Schematic Drawing)

| **NO** | **Version** | **Description** |
|--------|-------------|-----------------|
|        |             |                 |
|        |             |                 |

# 2 Application应用

This document contains the procedure that has to be carried out to repair bleed
an ABS hydraulic off line which failed the on line evac/fill process or have
been replaced by dry units. The procedure must be performed by using a standard
bleeder unit and additional actuation units. The procedure is based on K-Line
diagnosis and the corresponding features. The appropriate version of the general
and project specific “Diagnosis function description” provides information on
the handling and function of the K-Line diagnosis and which features should be
used.All used diagnostic functions are ROM-resident routines.

本文档包括如下必须执行的进程：用现有设备和其他执行设备对干式防抱死制动系统进行抽真空和加注。此进程基于K线诊断及其相关说明。“诊断功能描述文档”细述诊断功能和响应参数设置，请参阅。所有诊断相关的功能已固化进电子控制器的存储器中，详见“诊断功能描述文档”。

## 2.1 Requirements要求

Requirements for the test facilities provided by the customer测试装置功能要求：

\-Communication with the SFB ECU能与宁波赛福电子控制器建立通信

\-Control of the test sequence控制测试序列

System Requirements系统要求：

All brake components must be capable to achieve a sufficient bleed
result所有制动零件应具备排气能力

The orifice sizes of the hydraulic modulator will define the required bleed time
and bleed pressure液压模块孔径大小决定排气时间和压力

This timing must be adapted onto the brake system and can only be determined by
running trials on line时间应根据制动系统确定，具体时间由调试确定

# 3 Procedure进程

## 3.1 Scope范围

All the SFB ABS components, such as hydraulic modulator is delivered to the
customers assembly plant in a dry state (free of brake fluid). Both, primary and
secondary circuits of the hydraulic modulator are dry.

In order to bleed the entire modulator, valves and pump motor must be energized
by using electrical adaptations and additional equipment’s to fire valves and
pump motors with a predefined ROM resident routine.

宁波赛福防抱死制动系统所有组件，如液压控制单元，交付给客户工厂时均为干式（没有制动液）。初级回路和二级回路均为干式。为了排空整个模块，需要通过加注设备来控制阀和电机得电来进行相应操作，阀和电机执行的操作已固化进电子控制器的存储器中。

All systems that failed the on line evac/fill process or might be replaced by
dry units, must be repair bled within a specific procedure as described in this
document. In order to achieve a sufficient pressure within the hydraulic
modulator, the brake pedal must be stroked during the entire bleed procedure.
The procedure will then be executed in a same way than a standard foundation
brake system with the exception of the extended timing that is required to bleed
the secondary sections of the hydraulic modulator. The electrical adaptation
will be done by connecting onto the diagnostic link of the vehicle (requires a
complete installation).

本文档描述在抽真空加注产线出错的系统或者干式系统在装车使用时必须进行的操作，用以确保防抱死制动系统可靠运行。为保证液压模块气体完全排空，在排气的全程中刹车踏板需一直踩下。排气的进程有别于没有安装防抱死制动系统的常规制动管路加注过程，这点请注意。诊断电气端可连接至车辆诊断接口（需全部连接），也可外供电源单独连接（赛福推荐）。

The data for pressure apply and pressure source are specified in the “Technical
Customer Documentation” of the hydraulic modulator as well as in this document.
The bleeder unit must be capable to meet the requirements as specified in this
document. In order to achieve a sufficient bleed result, all components, such as
master cylinder, wheel calipers must meet the minimum requirements as specified
in this document. The final timing of the production cycle can only be
determined by trials with production parts (or parts close to production level)
and off line equipment. Off Line Equipment may need to be modified onto the
requirements of the hydraulic configuration of the vehicle.

本文档和“客户技术文档”都描述了排气过程中所需压力等相关数据。排气设备应满足文档所列要求。为排空所有气体，所有零件，如主缸、轮缸卡钳等均要满足本文所列要求。本过程所需生产时间需经生产线调试确定，各部件、在线设备均处于生产状态（或近生产状态）。离线设备相关参数可能要根据车型配置信息加以修改。

## 3.2 Process Sequence过程顺序

| **Test Step:**           | **Scope:**                                                                                                                                                                                                                                                                                                   |
|--------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1                        | Handling操作                                                                                                                                                                                                                                                                                                 |
| 2                        | Diagnostics before bleeding排气前诊断                                                                                                                                                                                                                                                                        |
| 2.1 2.2 2.3              | - Communication Set Up建立通信 - ECU – Identification电子控制器身份标识 - Check System Status检查系统状态                                                                                                                                                                                                    |
| 3                        | General bleed process description valid for ABS防抱死制动系统通用排气流程                                                                                                                                                                                                                                    |
| 3.1  3.2 3.3 3.4 3.5 3.6 | Principle of brake system and modulator bleeding with ABS带防抱死制动系统的制动系统和液压模块排气准则 Details to bleeding of ABS防抱死制动系统排气细则 - Front Wheel; phase 1前轮排气，阶段1 - Front Wheel; phase 2前轮排气，阶段2 - Rear Wheel; phase 3后轮排气，阶段3 - Rear Wheel; phase 4后轮排气，阶段4 |
| 4                        | - Schematically repair bleeding diagram for ABS防抱死制动系统排气原理图                                                                                                                                                                                                                                      |
| 4.1 4.2 4.3              | - Diagnostic commands诊断命令 - Phase 1: Front Wheel阶段1：前轮 - Phase 2: Front Wheel阶段2：前轮 - Phase 3: Rear Wheel阶段3：后轮 - Phase 4: Rear Wheel阶段4：后轮                                                                                                                                          |
| 5                        | Diagnostics during and after repair bleeding排气过程中和结束后的诊断                                                                                                                                                                                                                                         |
| 5.1 5.2 5.3 5.4          | - Check System Status校验系统状态 - Write Process Byte (Test Result)写流程状态字节（测试结果） - Clear Fault Code Memory清除故障代码 - End of Diagnosis诊断结束                                                                                                                                              |
| 6                        | End of bleeding process排气流程结束                                                                                                                                                                                                                                                                          |
| 6.1 6.2                  | Top Off Reservoir移除排气油壶 Handling操作                                                                                                                                                                                                                                                                   |

# 4 Process Step Descriptions过程步骤描述

## 4.1 Handling操作

| **Handling操作：**                                                                                             |                                   |
|----------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Operator操作人员                                                                                               | Diagnostic Unit / ECU诊断单元/ECU |
| Adapt bleeder unit to the reservoir排气装置接至油壶 Adapt electrical connection电气连接 Turn Ignition ON点火开 |                                   |

**Remarks备注：**

In the repair area, the vehicle is already completely installed. The electrical
connection is done via the diagnostic link of the vehicle. The operator must
turn the ignition ON.

排气前车辆已安装完整。电气线束通过车载诊断口接入。操作人员必须打开点火开关。

## 4.2 Diagnostics Prior and During Repair Bleeding排气前及排气过程中诊断

### 4.2.1 Communication Set Up建立通信

| **Diagnostic Function: Start Diagnostic Session开始诊断会话**                                            |                                         |
|----------------------------------------------------------------------------------------------------------|-----------------------------------------|
| Start Diagnostic Session (Request)开始诊断会话（请求）                                                   | 10h                                     |
| Start Communication开始通信                                                                              | 83h                                     |
| Start Diagnostic Session (P. Response)开始诊断会话（肯定应答）                                           | 50h                                     |
| Start Communication开始通信                                                                              | 83h                                     |
| Diagnostic Equipment诊断设备                                                                             | ECU                                     |
| Communication Set Up建立通信                                                                             | Enters into diagnostic mode进入诊断模式 |
| Initialization and communication set up see “functional description of diagnosis”.初始化见“诊断描述文档” |                                         |

**Remarks备注：**

The communication set up between the Tester and the ECU based on K-Line
diagnosis according to the corresponding specification. It can be started
immediately after the system is power up. In case of a non successful
communication set up repeat for about 3 times before the test is interrupted. In
case of a non successful communication, the process must be interrupted and the
vehicle be corrected.

诊断仪和电子控制器之间通信采用K线。系统上电后即可开始通信。通信失败时，先重复尝试3次，如果还是失败时应中断此流程，排除车辆故障。

Communication not successful -\> Set failure message,
continue通信失败，故障报警，继续

Communication successful -\> Continue通信成功，继续

### 4.2.2 ECU-Identification电子控制器身份标识

| **Diagnostic Function诊断功能： Read ECU Identification读取电子控制器身份标识**                                   |                                           |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------------------|
| Read ECU Identification (Request)读取ECU标识符（请求）                                                            | 1Ah                                       |
| Record Local Identifier本地身份标识 Customer Part Number客户零件号 SFB Part Number赛福零件号 Project Name项目名称 |  91h 92h 9Ah                              |
| Service Code (P. Response) 服务代码（肯定应答） Record Local Identifier本地身份标识                               | 5Ah  xxh                                  |
| Customer Part Number (13 bytes ASCII) SFB Part Number (13 bytes ASCII) Project Name (13 bytes ASCII)              | XXXXXXXXXXXXX XXXXXXXXXXXXX XXXXXXXXXXXXX |

**Remarks备注：**

See ECU data in diagnostic specification for details of byte numbers, values and
ranges. The ECU data must be verified with the demand data of the tester
software.(These data may change in case of revision changes and should be
capable to be edited and to add new numbers).

电子控制器数据数值、范围定义请参考诊断技术文档，诊断仪软件与电子控制器软件要相互校验（这些数据因项目而异）。

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat re-quest”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request (7Fh 1Ah 21h)” shows the ECU, that the request is understood, but
the previous request is still being executed and its result might affect the
response to the requested service. The tester has to send the same request
again, until it gets a final response (positive or negative with LID different
from 21)).

如果服务执行时间超过50毫秒，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断仪发送的服务请求，如“7F
1A
21”）诊断仪应重复当前命令，直至电子控制器回复肯定应答（或者非“繁忙（21H）”应答）。

Unknown System -\> Abort Test系统未知，中断测试

System detected -\> Continue系统已知，继续

### 4.2.3 Check System Status校验系统状态

| **Diagnostic Function诊断功能：Read Data By Local ldentifier通过本地身份标识读取数据** |                     |                                            |                          |            |
|----------------------------------------------------------------------------------------|---------------------|--------------------------------------------|--------------------------|------------|
| Read Data By Local Identifier (Request)通过本地身份标识读取数据（请求）                | 21h                 |                                            |                          |            |
| Record Local Identifier本地身份标识                                                    | 04h                 |                                            |                          |            |
| Read Data By Local Identifier (P. Response)通过本地身份标识读取数据（肯定应答）        | 61h                 |                                            |                          |            |
| Record Local Identifier本地身份标识                                                    | 04h                 |                                            |                          |            |
| ECU Data to be evaluated有待评估的ECU数据                                              |                     |                                            |                          |            |
| ECU-Data ECU数据：                                                                     | Byte / Bit字节/位： | Actual Data实际数据：                      | Demand Data 需求数据：   | System系统 |
| Valve relay status阀继电器状态                                                         | Byte 4/ Bit 6       | actuated (1h) 驱动 not actuated (0) 未驱动 | correct正确 failure 错误 | both       |

**Remarks备注：**

See ECU data in diagnostic specification for details of Byte numbers, values and
ranges. Prior, during and at the end of the repair bleed process, the diagnostic
equipment must identify whether the ECU is active or passive. In case the system
is disabled, no valves can be activated. While the repair bleed process was
running, the ECU monitors the internal failures. In case of any failure
detection, the ECU will have disabled the system and have aborted the valve and
pump motor activation’s to avoid any damage. The ECU data must be verified with
the limit data of the tester software.

数据数量和范围定义请参见“诊断描述文档”，在排气前、过程中及排气后，诊断仪应识别电子控制器处于激活还是休眠状态。一旦系统休眠，所有跟阀相关的操作都将失效。排气程序执行时，电子控制器内部会一直监控其是否有错误。遇有错误时，电子控制器会停止系统，关闭电磁阀和电机控制以保护相关器件不受损坏。诊断仪应将电子控制器数据与限制数据相互校验。

Data correct -\> Continue数据正确，继续测试

Data not correct -\> Failure message, continue 数据错误，报警，排除故障

## 4.3 Bleed Process Description排气流程描述

### 4.3.1 Principle of Brake System and Modulator Bleeding with ABS ABS制动系统和液压模块描述

| **Bleeding Procedure排气步骤：** |                                                                                                                                                 |                                                                    |
|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| Circuit回路                      | Operator操作人员                                                                                                                                | Diagnostic Unit / ECU诊断单元/ECU                                  |
|                                  | Stroke brake pedal during the entire bleed procedure!!!全程一直反复踩刹车踏板                                                                   |                                                                    |
| Primary circuit 一级回路         | Open bleed screw front拧开前轮放气螺栓 Start the routine and bleed the wheel front 开始运行前轮排气程序 Close bleed screw front拧紧前轮放气螺栓 | Execute ROM resident routine phase 1 执行电子控制器内排气阶段1程序 |
|                                  | Open bleed screw rear拧开后轮放气螺栓 Start the routine and bleed the wheel rear 开始运行后轮排气程序 Close bleed screw rear拧紧后轮放气螺栓    | Execute ROM resident routine phase 3 执行电子控制器内排气阶段3程序 |
| Secondary circuit 二级回路       | Open bleed screw front拧开前轮放气螺栓 Start the routine and bleed the wheel front 开始运行前轮排气程序 Close bleed screw front拧紧前轮放气螺栓 | Execute ROM resident routine phase 2 执行电子控制器内排气阶段2程序 |
|                                  | Open bleed screw rear拧开后轮放气螺栓 Start the routine and bleed the wheel rear 开始运行后轮排气程序 Close bleed screw rear拧紧后轮放气螺栓    | Execute ROM resident routine phase 4 执行电子控制器内排气阶段4程序 |

**Remarks备注：**

It is necessary to use a bleeding device with an overpressure of 2 bar. It is
absolute important for a sufficient bleeding result that the brake pedal is
alternate applied the entire process!!!! In case of repetition of a once phase
or the entire bleeding routine it is absolute necessary to wait a time of 5
minutes to cool the solenoid valves. Otherwise the solenoid valves could be
damaged by overheating.

排气过程要使用大于2bar的压力排气装置。为保证排空气体，在排气过程中，刹车踏板要一直反复踩下。在两次执行同一排气阶段程序时应间隔5分钟，使电磁阀冷却。否则电磁阀会过热损坏。

### 4.3.2 Diagnostic Commands to Bleed System排气系统诊断要求

#### 4.3.2.1 Schematically Repair Bleeding Diagram with all used ROM Resident Functions内部排气程序示意

**Remarks备注：**

The repair bleed process included the primary and secondary bleeding of the
hydraulic unit. After execution of the ROM resident routines the entire brake
system should be free of air.

排气流程包括液压模块的一级回路和二级回路两个部分，执行完电子控制器内部固化的程序后，制动系统内应无任何气体。

#### 4.3.2.2 Diagnostic Commands诊断命令

**Phase 1阶段1**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Request根据本地身份标识开始例程请求**                                                                                           |                            |                                                                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service Identifier服务身份标识 Routine Local Identifier例程本地身份标识Start the periodic control开始周期控制 Repair Bleed Phase Identifier排气阶段标识 Repetition times重复次数    Reserved保留 | 31h D1h 00h 01h 01h    xxh |     This value has no influence, but must be sent by the tester, otherwise the ECU sends a negative response.该参数由诊断仪设置，否则电子控制器会回复否定应答。 |

**Phase 2阶段2**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Request根据本地身份标识开始例程请求**                                                                                           |                            |                                                                                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service Identifier服务身份标识 Routine Local Identifier例程本地身份标识Start the periodic control开始周期控制 Repair Bleed Phase Identifier排气阶段标识 Repetition times重复次数    Reserved保留 | 31h D1h 00h 02h 05h    xxh |     This value has no influence, but must be sent by the tester, otherwise the ECU sends a negative response该参数由诊断仪设置，否则电子控制器会回复否定应答。 |

**Phase 3阶段3**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Request根据本地身份标识开始例程请求**                                                                                           |                            |                                                                                                                                                                |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service Identifier服务身份标识 Routine Local Identifier例程本地身份标识Start the periodic control开始周期控制 Repair Bleed Phase Identifier排气阶段标识 Repetition times重复次数    Reserved保留 | 31h D1h 00h 03h 01h    xxh |     This value has no influence, but must be sent by the tester, otherwise the ECU sends a negative response该参数由诊断仪设置，否则电子控制器会回复否定应答。 |

**Phase 4阶段4**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Request根据本地身份标识开始例程请求**                                                                                           |                            |                                                                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Service Identifier服务身份标识 Routine Local Identifier例程本地身份标识Start the periodic control开始周期控制 Repair Bleed Phase Identifier排气阶段标识 Repetition times重复次数    Reserved保留 | 31h D1h 00h 04h 05h    xxh |     This value has no influence, but must be sent by the tester, otherwise the ECU sends a negative response该参数由诊断仪设置，否则电子控制器会回复否定应答。  |

**Negative Response否定应答：**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Response根据本地身份标识开始例程应答** |     |                         |
|---------------------------------------------------------------------------------------------------------|-----|-------------------------|
| Negative response data (Hex Codes)否定应答数据                                                          |     |                         |
| Service Identifier服务身份标识                                                                          | 7Fh |                         |
| Request Service Identifier服务身份标识请求                                                              | 31h |                         |
| Response Code应答代码                                                                                   | 21h | Busy Repeat Request繁忙 |

**Remarks备注：**

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat re-quest”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request” shows the ECU, that the request is understood, but the previous
request is still being executed and its result might affect the response to the
requested service. The tester has to send the same request again, until it gets
a final response (positive or negative with LID different from 21)).

如果服务执行时间超过50
ms，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断仪发送的服务请求）诊断仪应重复当前命令，直至电子控制器回复肯定应答（或者非“繁忙（21H）”应答）。

**Positive Response肯定应答：**

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Response根据本地身份标识开始例程应答** |     |   |
|---------------------------------------------------------------------------------------------------------|-----|---|
| Positive response data (Hex Codes)肯定应答数据                                                          |     |   |
| Service Identifier服务身份标识                                                                          | 71h |   |
| Routine Local Identifier例程本地身份标识                                                                | D1h |   |

#### 4.3.2.3 Stop Repair Bleed Process停止排气操作

| **Diagnostic Function诊断功能： Stop Routine By Local ldentifier根据本地身份标识停止例程** |     |   |
|--------------------------------------------------------------------------------------------|-----|---|
| Service Identifier (Request)服务身份标识(请求)                                             | 32h |   |
| Routine Local Identifier例程本地身份标识                                                   | D1h |   |
| Service Identifier (P. Response) 服务身份标识（肯定应答）                                  | 72h |   |
| Routine Local Identifier例程本地身份标识                                                   | D1h |   |

**Remark备注：**

The routine can be stopped at each time. If the system is stopped manual, the
vehicle must be repair bleed again.

每个排气过程均可通过命令来停止。如果人为停止排气操作，车辆应重新排气。

#### 4.3.2.4 Request Repair Routine Results请求排气例程结果

| **Diagnostic Function诊断功能：Request Routine Results By Local Identifier根据本地身份标识请求例程结果** |     |                     |
|----------------------------------------------------------------------------------------------------------|-----|---------------------|
| Service Identifier (Request)服务身份标识(请求)                                                           | 33h |                     |
| Routine Local Identifier例程本地身份标识                                                                 | D1h |                     |
| Service Identifier (P. Response) 服务身份标识（肯定应答）                                                | 73h |                     |
| Routine Local Identifier例程本地身份标识                                                                 | D1h |                     |
| Status Of the Request Question请求问题状态                                                               | xxh | Result Byte结果字节 |

**Remarks备注：**

Following results are possible可能会回复以下结果：

“02 Hex” means routine was correct finished. “02H”程序执行正确。

“00 Hex” means routine error during execution. To ensure a correct filled brake
system, the vehicle must be repair bleed again.
“00H”程序执行出错，车辆要重新排气。

## 4.4 Diagnostics After Repair Bleeding排气后诊断

### 4.4.1 Check System Status校验系统状态

Check System Status during and after the activation’s again. For more details
see also chapter 4.2.3! During diagnostics the internal ECU safety software is
active. In case of a detected failures the ECU shuts down the valve relay to
avoid any damages. The tester has to check the valve relay status at the end of
the repair bleeding process. The ECU data must be verified with the limit data
(valve relay status ok --\> system active) of the tester software.

在激活排气操作前后都要检验系统状态，具体操作请参见4.2.3节。在诊断模式下，电子控制器内部安全软件处于激活状态，一旦侦测到错误，电子控制器立即关断阀供电继电器，保护电磁阀免受损坏。在排气过程结束后，诊断仪应检测电磁阀状态。电子控制器返回的数据应符合诊断仪设定的状态值（供电继电器状态正常-\>系统激活）。

Data correct -\> Continue数据正确，继续测试

Data not correct -\> Failure message, continue数据错误，报警，排除故障

### 4.4.2 Write Process Control Byte写加注状态字节

| **Diagnostic Function诊断功能：Write Data By Local Identifier根据本地身份标识写数据** |                                                                                                  |   |
|---------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|---|
| Service Identifier(Request)服务身份代码（请求）                                       | 3Bh                                                                                              |   |
| Routine Local Identifier本地身份例程                                                  | 20h                                                                                              |   |
| Status状态                                                                            | XXh Status of Filling加注状态                                                                    |   |
| ECU Data to be written写入的ECU数据                                                   |                                                                                                  |   |
| FFh 55h AAh                                                                           | Delivery State交付状态（初始状态） Filling Successfully加注成功 Filling Not Successfully加注失败 |   |
| Service Identifier (P. Response) 服务身份标识（肯定应答）                             | 7Bh                                                                                              |   |
| Routine Local Identifier本地身份例程                                                  | 20h                                                                                              |   |

**Remarks备注：**

The ECU is shipped to the customer assembly line with a predefined process byte:
“FF Hex”. This number is reserved by SFB. In case of a non successful
communication this data will still stay in the EEPROM of the ECU (“incorrect”).
The EEPROM location is defined by SFB.

电子控制器由宁波赛福运至客户工厂时，加注状态初始值为“FFH”，这个值是宁波赛福设定的初始值，在没有通信（写加注状态值）之前，这个初始值始终在电子控制器的存储器中，其具体地址由宁波赛福定义。

### 4.4.3 Clear Fault Code Memory清除故障代码

| **Diagnostic Function诊断功能：Clear Diagnostic Information清除诊断信息** |      |
|---------------------------------------------------------------------------|------|
| Service Code (Request)服务代码（请求）                                    | 14h  |
| Group Of DTC High Byte高字节诊断故障码组                                  | FFh  |
| Group Of DTC Low Byte低字节诊断故障码组                                   | 00h  |
| Service Code (P.Response)服务代码（肯定应答）                             | 54h  |
| Group Of DTC High Byte高字节诊断故障码组                                  | FFh  |
| Group Of DTC Low Byte低字节诊断故障码组                                   | 00h  |
| ECU Data to be evaluated待评估的ECU数据                                   | none |

**Remarks备注：**

See ECU data in diagnostic specification for details. This step allows to erase
the entire content of the fault code memory of the ECU. This step is only
optional. In case of cycle time conflicts, this step can also be integrated into
the system end of line test or at another diagnostic station on line. The
diagnostic equipment can erase the fault code memory of the ECU.

故障列表详细内容请参见“诊断描述文档”。此步骤允许擦除电子控制器中存储的所有故障代码内容。此步骤为可选操作，如果与排气循环时间冲突，这一步可以集成进下线检测或者生产线诊断工位上，诊断设备需具备擦除电子控制器故障内容的能力。

### 4.4.4 End of Diagnosis诊断结束

| **Diagnostic Function诊断功能：Stop Communication Session停止通信** |      |
|---------------------------------------------------------------------|------|
| Service Identifier(Request)服务身份标识（请求）                     | 82h  |
| Service Code (P. Response)服务代码（肯定应答）                      | C2h  |
| ECU Data to be evaluated待评估的ECU数据                             | none |

**Remarks备注：**

Ends extended diagnostic mode and returns to normal/default diagnostic session.

退出下线检测模式，恢复至标准/默认诊断模式。

## 4.5 End of Bleeding Process结束排气操作

### 4.5.1 Top Off Reservoir (Scavenging) 油壶复压（清除壶口污渍）

| **Top Off Reservoir (Scavenging)油壶复压（清除壶口污渍）** |                                                                                         |           |
|------------------------------------------------------------|-----------------------------------------------------------------------------------------|-----------|
| Repair bleeding unit人工排气单元                           | Conditions情况                                                                          | Value值   |
| Top off reservoir (Scavenging) 油壶复压（清除壶口污渍）    | Set reservoir level to correct limits 将油壶油液置于合适的液位 Time for top off复压时间 |   tbd sec |

**Remarks备注：**

The reservoir must be filled to a certain level. The timing of this test step
must be set to customer related requirements.

油壶应加注至指定液位，本步骤时间由客户文档规定。

Level ok. -\> Continue 液位正常，继续测试

Level not ok -\> Continue, set failure message 液位不正常，故障报警，继续测试

### 4.5.2 End of Cycle/ Handling排气循环结束/操作

| **End of Cycle / Handling排气循环结束/操作**                                                                            |                                   |
|-------------------------------------------------------------------------------------------------------------------------|-----------------------------------|
| Operator操作人员                                                                                                        | Diagnostic Unit / ECU诊断单元/ECU |
| Turn Ignition (Power supply) OFF点火关（断电） Remove electrical connection Remove fill head 移除电气连接，拔除加注接头 |                                   |

**Remarks备注：**

The operator has to turn off the ignition prior to disconnect the harness from
diagnostic connector.

操作者在移除电气连接前必须先断电。

# 5 Process Timing排气流程时间

## 5.1 Timing for Valve and Pump Motor Activation 阀和电机激活时间

| **Repair Bleed Cycle人工排气循环**              |                                                                                                                                                     |
|-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Valve Cycling:阀循环  Pump Motor Delay:电机延时 | Automatically done from the ECU (ROM resident routine) 电子控制器自动运行 Automatically done from the ECU (ROM resident routine) 电子控制器自动运行 |

**Remarks备注：**

The pump motor must run after the bleed cycle with a delay of a few second to
release the accumulators of the hydraulic modulator. This delay is automatically
done from the ECU (ROM resident routine). The pressure source to feed the pump
must be minimum 2 bar. The source must be hooked up and apply the pressure to
the pump before the pump its started. Details about the pump motor and valve
actuation’s please refer chapter 7.

排气循环结束后应驱动泵电机运行2s，用以抽空蓄能器腔室。这个时间由电子控制器设定。泵压力源最小压力为2bar，在电机泵运转之前应确保制动液壶口连接完好并已加上2
bar压力，电机和阀驱动操作详细内容请参见第7章。

## 5.2 Timing for Bleed Cycle排气循环时间

| **Timing for bleed cycle排气循环时间**                                  |                                                                                                                                                                                        |                                                                                                                                                                                                                                                                                               |                                                                                            |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| Minimum pressure level at the master cylinder reservoir主缸壶口最小压力 | Minimum system pressure level to be achieved in the hydraulic modulator液压模块完成排气所需最小系统压力                                                                                | General remarks for the bleeding time of the entire brake system: 整个制动系统排气时间的批注                                                                                                                                                                                                  | Time for primary and secondary circuit bleeding per wheel每个轮子的一二级回路排气时间      |
| ≥ 2 bar                                                                 | ≥ 15 bar The system pressure must be achieved by stroking the brake lever or pedal continuously during the entire bleed procedure. 整个排气过程中的系统压力通过捏手刹或踩制动踏板获取  | The timing per wheel depends onto the foundation brake system and the hydraulic modulator.Bleeding must be done until there is foamless and bubble free brake fluid seen at the calipers bleed screws. 轮缸所需时间由基础制动和液压模块决定，当轮缸放气阀处没有气泡和泡沫时才能视为排气完成。 | ABS systems: Wheel front前轮 122 seconds + time Xs  Wheel rear后轮 122 seconds + time Xs   |

## 5.3 Timing for Operator Handling操作人员操作时间

| **Timing for operator handling操作人员操作时间**                                                                    |                                                                                                                                 |
|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| Fill head adaptation连接相关器件                                                                                    | Electrical adaptations电气连接                                                                                                  |
| The time for adaptation and removing the fill head is identical to a non ABS system. 与未安装防抱死制动系统操作一样 | The time for the electrical adaptation and disconnection is an additional operator handling. 需考虑操作人员电气连接和拔除时间。 |

# 6 Failure Handling故障处理

| **Failure Handling故障处理：**                                                    |                                                                                                                                                |
|-----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Type of failure故障类型： Failure Indication , Failure Handling故障提示，故障操作 |                                                                                                                                                |
| Bleed unit排气单元 Diagnostic equipment诊断设备                                   | repair / replace bleed unit -\> repeat repair procedure维修更换，重复排气 set failure indication -\> repeat repair procedure故障报警，继续排气 |

**Remarks备注：**

In case of a failure of the repair bleed process, the brake system must be
corrected and the procedure must be repeated from the beginning.

在排气过程中出现故障时，应排除执行系统故障，然后从头开始排气操作。

# 7 Maximum Allowed Valve Actuation Times阀激活最长时间

| **Valves:** | **ABS**                                                            |                                            |                                            |                                            |
|-------------|--------------------------------------------------------------------|--------------------------------------------|--------------------------------------------|--------------------------------------------|
|             | **Repair bleed routine (diagnostic mode)人工排气例程（诊断模式）** |                                            |                                            |                                            |
|             | **Internal routine Phase 1** **内部阶段1**                         | **Internal routine Phase 2** **内部阶段2** | **Internal routine Phase 3** **内部阶段3** | **Internal routine Phase 4** **内部阶段4** |
| NO F4,06 Ω  | -----                                                              | -----                                      | -----                                      | -----                                      |
| NO R4, 06Ω  | -----                                                              | -----                                      | -----                                      | -----                                      |
| NC F4, 06 Ω | 1 \*5s on                                                          | 5 \*5s on                                  | -----                                      | -----                                      |
| NC R4, 06 Ω | -----                                                              | -----                                      | 1 \*5s on                                  | 5 \*5s on                                  |

**Remarks备注：**

All valve actuation times automatically done by the ECU with using of the ROM
resident routine “repair bleeding”. SFB recommends to use this ROM resident
function to avoid any damages at the valves caused by overheating. It is not
allowed to repeat the repair bleeding routines twice times within a short time!
In case of repetition of a once phase or the entire bleeding routine it is
absolute necessary to wait a time of 5 minutes to cool the solenoid valves.

使用电子控制器内部排气程序时，所有电磁阀的动作时间会自动运行。宁波赛福建议使用存储器内部固化的排气程序，以防电磁阀过热导致系统损坏。严禁短时间内重复执行单个排气程序2次及以上。如需重复执行单次或全部排气程序，请先等待5分钟，冷却电磁阀，用以保护电磁阀因过热损坏。

# 8 Data Specifications数据规范

## 8.1 Hydraulic Data Specifications液压数据规范

| **Hydraulic data specifications液压数据规范**                                        |                              |
|--------------------------------------------------------------------------------------|------------------------------|
| Measurement point测试点                                                              | Pressure / Force Value压力值 |
| Bleed pressure (bleed unit at the master cylinder reservoir)排气压力（主缸壶口压力） | 2 bar ≤ P unit ≤ 10 bar      |
| System pressure系统压力                                                              | 15 bar ≤ P system            |
| Brake lever force刹车手柄力                                                          | tbd                          |
| Brake pedal force刹车踏板力                                                          | tbd                          |

**Remarks备注：**

The system pressure must be achieved by lever or pedal stroking. The brake lever
or pedal force must be measured in order to achieve the system pressure.

通过制动手刹或踏板达到系统所需压力。通过传感器采集手刹或踏板压力来达到系统所需压力值。

## 8.2 Hydraulic Volume Data of the ABS Modulator液压单元数据

| **Specific hydraulic data:  ABS**                           |        |
|-------------------------------------------------------------|--------|
| Volume of primary circuit per circuit基础回路容量：         | TBD    |
| Volume of secondary circuit per circuit二回路容量：         | TBD    |
| Dead space volume of one pump element泵死腔容积：           | TBD    |
| NO valve orifice size (front axle)前轴常开阀孔径：          | TBD    |
| NO valve orifice size (rear axle)后轴常开阀孔径：           | TBD    |
| NC valve orifice size (front axle)前轴常闭阀孔径：          | TBD    |
| NC valve orifice size (rear axle)后轴常闭阀孔径：           | TBD    |
| Maximum allowed dry run time of the pump elements泵空转时间 | \< 60s |

**Remarks备注：**

All volume values are rounded. 所有容积值均圆整。

## 8.3 Electrical Data Specification电气数据规范

| **Electrical data specifications:**                                       |                                                                                                                                                                                                                                                                                                                                                                                                                       |
|---------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Power supply unit (to supply the car battery)供电模块（给车载电池供电）   | Voltage / Current电压/电流：11.5 V ≤ U supply ≤ 14 V (measured at the connector of the ECU! 端口检测电压)  All valve current values are calculated in case of if the valves are actuated with100% duty cycle!!! 阀电流为100%占空比时的电流值                                                                                                                                                                          |
| Current consumption (at 12V)电流消耗                                      | ECU电子控制器≤ TBD A  Solenoid valves电磁阀：2,8 A  Pump motor start up (peak for 20-50ms) 电机启动： ≤ 50 A (depends on the used RP system specific) 视系统而定   Pump motor (during repair bleed )电机运转（排气过程中）：8 A (TBD)                                                                                                                                                                                 |
| Connector连接器                                                           | The connector must be an industrial one, not a production level part in order to allow a multiple use. Terminals should be designed as spring loaded parts to avoid any damages of the vehicle or system connectors. Connector design must be adapted onto the diagnostic connector design and may vary according to the customers design. 采用工业标准接头，多功能用途，防止在插拔过程中损坏端子排，具体由用户定义。 |

**Remarks备注：**

The diagnostic link must not extend a maximum length of 10 meters.

诊断线束最长不得超过10米。

# 9 Electrical Adaptation电气连接

**Adaptation onto the diagnostic link of the vehicle连接车辆诊断接口**

| **Handling操作：**                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                                                      |
|--------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator 操作者                                                                                                          | Remarks备注                                                                                                                                                                                                                                                                                                                                                                                          |
| Adapt diagnostic link连接诊断接口 Adapt power supply (if necessary) 供电（如果需要）        Turn Ignition ON打开点火开关 |  Either in dashboard or engine compartment，external power supply is required either to support the vehicle battery or in case the battery is not already installed or connected (optional). 无论是仪表盘或者发动机舱，需要外部供电（如有可能：连接一个外部车载电池）来支持车载电池或者在没有安装或连接电池的时供电。  To power up the system and initialize the ECU. 给系统供电和初始化电子控制器。 |

# 10 Equipment Information设备信息

**Bleed Unit Design排气设备设计：**

The process is designed to be performed on standard bleeder unit equipment.

本文档描述的排气操作适合标准排气装置。

**Diagnostic Information诊断信息：**

An additional diagnostic unit is required to run the ROM resident routines
functions to actuate valves and pump motor. The diagnostic computer should be as
close to the vehicle as possible to avoid communication problems. The timing
(time gaps between messages and bytes within messages) should be set close to
the minimum possible limits in order to minimize the process time.

诊断仪应具备使电子控制器中程序来驱动电机和阀动作的通信能力。诊断电脑应靠近车辆，减少通信故障，通信格式中的时间（消息字节间时间间隔）应配置为最小值，这样可以减少整个流程所需时间。

**Process Byte流程字节：**

The final definition of the process byte data must be taken from the customer
requests.

最终流程字节定义由客户确定。

**Editor menus编辑菜单：**

ECU Identification codes may change during production due to updates of software
revisions. It is important to set up the software program to add identification
numbers by using an editor menu.

The timing of the valve activation’s should be designed to be modified within an
editor menu.

电子控制器身份标识码可能随项目软件改变而改变，诊断仪软件应具备可编辑功能，方便更改；阀驱动时间在菜单命令中也应可更改。

**Test result测试结果：**

In case of an ok or not ok. Test result, the diagnostic tool must identify this
on display.

诊断仪应识别并显示测试结果，包括成功和失败信息。

**Vehicle conditions车辆条件：**

The battery must be charged properly in order to allow a sufficient power supply
to the system must ensure a stable voltage level without insufficient voltage
drops across the wiring.

电池充满，避免在使用过程中因线束压降导致系统不正常。
