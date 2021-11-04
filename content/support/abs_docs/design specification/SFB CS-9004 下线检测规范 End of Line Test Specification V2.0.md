---
title: SFB CS-9004 下线检测规范
linktitle: SFB CS-9004 下线检测规范
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## 更新记录
|                      | 客户规范 CUSTOMER SPECIFICATION             |                 |
|----------------------|---------------------------------------------|-----------------|
| SPEC NO. SFB CS-9004 | End of Line Test Specification 下线检测规范 | SF10 ABS System |
| Version: V2.0        |                                             |                 |

**Project Information**

| Customer客户： Vehicle车型：                                |                                                                                                              |
|-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| System系统： Channel通道：                                  | ABS  2 Channel System两通道管路/1 Channel System单通道管路                                                   |
| Diagnosis诊断： Kind of communication通信： Equipment设备： | Based on Customer KWP2000基于KWP2000协议 K-Line K线 Test Bench or 2 Axle Brake Dynamometer诊断仪和两轴测功机 |

**Release Department**

| **Department** | **Date** | **Signature** |
|----------------|----------|---------------|
|                |          |               |

**History list:**

| **Version** | **Edit**    | **Date**   | **Descriptions**                                                                                                                                                                                                                         |
|-------------|-------------|------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.0         | Taylor Wang | 2015.08.10 | Draft                                                                                                                                                                                                                                    |
| 1.1         | Taylor Wang | 2015.11.02 | Release                                                                                                                                                                                                                                  |
| 1.2         | Taylor Wang | 2015.11.30 | Update ”Check Input-/ Output-Signals”; Update “Warning Light Test / End of Test”; Update “Check Process byte”; Update “Wheel Speed Sensor Test”; Update “Dynamic ABS test on a brake dynamometer with 2 independent rolls”.              |
| 1.3         | Taylor Wang | 2015.12.13 | Update “Wheel Speed Sensor Test”; Update “Dynamic ABS test on a brake dynamometer with 2 independent rolls”.                                                                                                                             |
| 1.4         | Rich Chen   | 2015.12.31 | Modify the maximum number of stored faults from 10 to 6 in the section “Read Fault Code Memory”. Modify the checking measures for the ABS off switch in section “Check Input-/ Output-Signals”.                                          |
| 1.5         | Rich Chen   | 2016.5.30  | 1- Add and change delivery stat of the EOL flag from 00H to FFH in the section 4.10.1. 2- Change delivery stat of the hydraulic filling indicator from 00H to FFH in the section 4.3.                                                    |
| 1.6         | Rich Chen   | 2017.5.22  | 1-chang the Status of DTC “00h” to “01h” in order to read present DTC in the section 4.4 2- Document standardization and “PS3004” to “SFB CS-9004”                                                                                       |
| 1.7         | Rich Chen   | 2017.5.24  | 1-Add the testing condition for the brake switch signals, delete the testings for the pump motor status and valve relay status in the section 4.5. 2-Modify the service identifier from 18h to 17h in order to reading DTC in section4.4 |
| 1.8         | Rich Chen   | 2017.7.26  | 1-change the request data for diagnostic function “Actuator Test” for the ABS brake test. 2-change the diagram in the section 7.1.1.                                                                                                     |
| 1.9         | Albert Ye   | 2019.11.26 | Change the recommend test process, amendment the Warning Lamp Test. Add new diagnostic function (Application software number) to chapter 4.2.                                                                                            |
| 1.10        | Matthew     | 2020.1.2   | Change fault simulation diagram of tooth ring missing tooth in section 4.6 and fault diagram in section 4.7.                                                                                                                             |

# 1 General Information总述

## 1.1 Abbreviations缩写

ABS antilock braking system防抱死制动系统

ABS-WL ABS warning lamp防抱死故障报警灯

NC Normal Close valve常闭电磁阀

BLS brake light switch刹车灯

DTC diagnostic trouble code故障代码

ECU electronic control unit电子控制单元

NO Normal Open valve常开电磁阀

FA front axle前轴

FCM fault code memory故障代码缓存

RA rear axle后轴

ACC accumulator蓄能器

RLI record local identifier本地身份标示

SV solenoid valve电磁阀

WSS wheel speed sensor轮速传感器

## 1.2 Diagnostic Document

| **NO**      | **Version** | **Description**                                               |
|-------------|-------------|---------------------------------------------------------------|
| SFB CS-9010 | V2.0        | 诊断功能描述文档 Diagnosis Function Description Specification |
|             |             |                                                               |

## 1.3 Attachments (Schematic Drawing)

| **NO** | **Version** | **Description** |
|--------|-------------|-----------------|
|        |             |                 |
|        |             |                 |

# 2 Application应用

This document describes test steps which are recommended to ensure the correct
function of the SFB ABS system and its interfaces after the vehicle assembly.
The tests consists of static- and dynamic function tests. The tests are based on
K -Line diagnosis. The dynamic tests are carried out using a 2-axle brake
dynamometer (low speed). All used tests are ROM resident functions. The
appropriate version of the customer/vehicle specific “diagnosis function
description” provides information on the handling and function of the diagnosis.

本文档用于描述安装完宁波赛福防抱死制动系统的车型在出厂前的下线检测过程及步骤，以保证其性能及接口正常，包括静态功能和动态功能测试两大模块。测试基于K线诊断协议，其中动态测试使用的是低速测功机，本文涉及的ECU端所有测试程序均已集成到ECU的程序存储器中。关于更详细的诊断操作和功能描述请参见“诊断功能描述文档”。

Requirements for the test facilities测试装置功能要求：

\-Communication with the SFB ECU能与宁波赛福电子控制器建立通信

\-Control of the test sequence控制测试序列

\-Control of the dynamometer控制测功机

\-Evaluation of the test data评估测试数据

\-Issue test protocol遵循测试协议

Requirements provided by SFB另需宁波赛福提供的资料：

\- Diagnosis function description诊断功能描述文档

The test steps and the test timing is optimized in order to meet a short cycle
time and to avoid double checks of the system.

为满足短周期和避免重复测试，我们优化了部分测试步骤及测试时间。

**Note注意：**

If dynamic functional tests other than the ABS end of line test are performed on
the vehicle the ABS could be activated or the system disabled due to error
detection.

如果在实车上进行动态测试（不是在下线检测模式下测试），防抱死系统可能会因检测到错误信号而导致误触发或关断。

**General Remark for Communication关于通信：**

If the executing time of a service or function is exceeding 50ms, the ECU will
send a message “Busy repeat request” (negative response). After each “Busy
repeat request” has the tester to repeat the request for starting the routine or
service. (Explanation: With the negative response “Busy Repeat Request” shows
the ECU, that the request is understood, but the previous request is still being
executed and its result might affect the response to the requested service. The
tester has to send the same request again, until it gets a final response
(positive or negative with LID different from 21)). For further information see
the functional description of diagnosis.

如果执行服务的时间超过50毫秒，电子控制器会回复“繁忙”（否定应答）给诊断仪。诊断仪每次收到电子控制器回复的“繁忙”应答时都应该重复发送当前命令，用以保持电子控制单元激活状态。（因为当电子控制器回复“繁忙”表明电子控制器已识别诊断仪的命令并开始执行相关操作，只是执行所需时间较长，故诊断仪需要继续重发当前命令直至电子控制器回复“肯定应答”。）详细描述请参见“诊断功能描述文档”。

# 3 Test Procedure测试步骤

## 3.1 Test Scope测试范围

All the SFB ABS components, such as ECU, hydraulic modulator, wheel speed
sensors, are checked individually in the SFB assembly line prior to shipment to
the customer assembly plants. The entire system including harnesses, dashboard
lights and power supply of the vehicle is assembled the first time at the
customer plant and must be checked for proper connections and functions.

宁波赛福的防抱死制动系统所有零部件，包括电子控制器、液压模块、轮速传感器，在装箱运送给客户前，宁波赛福生产线均已检测通过。关于线束，仪表板，和车辆电平由车辆制造商负责，因首次与防抱死制动系统集成，故相关电气连接和校验应由车辆制造商负责。

The ECU is capable to run a number of complexity self monitoring software
features, such as continuity and plausibility checks and in case of errors to
identify these faults and to store fault code numbers.

This feature is used at the end of line test by reading out the fault codes as
error identification as well as information for repair works.

基于此监控功能，在下线检测过程中检测到的故障，可通过相应服务读取出来，并作为维修的参考依据。防抱死制动系统的电子控制器软件会持续监控各类信号的有效性，一旦出现故障会立即报警并予以存储识别。

However, some of the failures cannot be detected by the ECU itself (such as
cross connections of hydraulic pipes or wheel speed sensors and correct
functioning of some input signals, i.e. brake light switch). In order to find
these failures static or dynamic tests should be performed while the vehicle is
at rest or during a dynamic test on a dynamometer.

但是，仍有部分错误是电子控制器不能识别的（例如液压模块安装错误，轮速传感器安装，刹车灯开关等）。为了检测出以上提及的错误，我们开发了下线检测，车辆在出厂前应在测功机上进行静态和动态测试。

The major items of this test steps is to check for下线检测主用用于以下目的：

\-correct functioning of all input and output signals of the
ECU纠正电子控制器的所有输入输出信号

\-correct functioning of all wheel speed sensors (signal quality and correlation)
纠正轮速传感器的安装及匹配（信号完整性和一致性）

\-correct functioning of all valves and hydraulic components (functioning and
correlation) 纠正电磁阀及液压模块的一一对应匹配（功能和一致性）

The ABS hydraulic modulator is shipped to the customer in a dry state (no brake
fluid). Therefore it needs to be evacuated and filled on line by using K-Line
diagnosis for valve and pump motor activation’s. To ensure the proper process, a
process byte can be stored in the EEPROM of the ECU. The value of the byte is
stored by the evac/fill or bleeds equipment and can be checked at the end of
line test to verify the previous processes. The entire test procedure is
designed to cover all the important items of the system and to minimize the
testing time.

宁波赛福的防抱死制动系统采用干式运输（液压模块没有制动液），整车厂在安装上车辆以后需要运行抽真空加注程序与电子控制器通信，来触发电磁阀和电机工作。为确保操作得当，电子控制器存储器中设立一标志位来跟踪加注状态，此标志可在抽真空加注或排气过程中进行擦写，在下线检测前读取出该标志，看加注或排气是否成功。本测试步骤旨在用最短时间来测试防抱死制动系统所有重要项目。

## 3.2 Process Sequence操作流程

| **Test Step测试步骤** | **Test Scope测试范围**                           |
|-----------------------|--------------------------------------------------|
| 1                     | Communication Set Up建立通信                     |
| 2                     | ECU - Identification读取电子控制器的身份标识     |
| 3                     | Check Process Byte检验过程标识                   |
| 4                     | Read Fault Code Memory读取故障记录               |
| 5                     | Check Input-/Output-Signals检验输入输出信号      |
| 6                     | Wheel Speed Sensor Test轮速传感器测试            |
| 7                     | Dynamic ABS-Actuator Test动态防抱死制动系统测试  |
| 8                     | Warning Light Test 报警灯测试                    |
| 9                     | Read and Clear Fault Code Memory读取清除故障记录 |
| 10                    | End of Test 结束测试                             |

# 4 Process Step Descriptions流程描述

## 4.1 Communication Setup建立通信

| **Diagnostic Function诊断功能：Start Diagnostic Session建立诊断会话**                                             |                               |
|-------------------------------------------------------------------------------------------------------------------|-------------------------------|
| Start Diagnostic Session (Request)开启会话请求                                                                    | 10h                           |
| Start Communication开始通信                                                                                       | 83h                           |
| Start Diagnostic Session (P. Response)电子控制器响应                                                              | 50h                           |
| Start Communication开始通信                                                                                       | 83h                           |
| Diagnostic Equipment诊断设备                                                                                      | ECU                           |
| Operator操作者                                                                                                    | Tester / ECU                  |
| Turn Ignition OFF 点火关 Adapt Diagnostic Link 连接 Turn Ignition ON点火开                                        |  Communication Set Up建立通信 |
| Initialization and communication set up see “diagnosis function description”.  初始化等信息详见“诊断功能描述文档” |                               |

**Remarks备注：**

Turn ignition OFF and ON prior to the test cycle to ensure that the system has
not been disabled by previous assembly processes. The communication set up
between the Tester and the ECU based on K-Line diagnosis according to the
corresponding specification. In case of a non successful communication set up
this step should be executed 3 times before the test interrupted.

为确保相关软件功能模块未被误关闭，在测试开始前，请将点火钥匙先“熄火”再“点火”。诊断仪和电子控制器间通信通过K线，请参考“诊断功能描述文档”。如果遇到通信失败，请多尝试几次，一般建议先通信3次，然后再检测连线等故障。

Communication not successful -\> stop通信失败，停止测试

Communication successful -\> continue通信成功，继续测试

## 4.2 ECU Identification电子控制器身份标识

| **Diagnostic Function诊断功能：Read ECU Identification读取电子控制器身份标识**                                                                                                           |                                                         |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------|
| Read ECU Identification (Request) 读取ECU标识符（请求）                                                                                                                                  | 1Ah                                                     |
| Record Local Identifier本地身份标识 Customer Part Number客户零件号 SFB Part Number赛福零件号 Application Software Number应用软件号 Project Name项目名称                                  |  91h 92h 98h 9Ah                                        |
| Service Code (Response)服务代码（应答） Record Local Identifier本地身份标识                                                                                                              | 5Ah  XXh                                                |
| Customer Part Number(13 bytes ASCII) 客户零件号 SFB Part Number(13 bytes ASCII) 赛福零件号 Application Software Number (13 bytes ASCII) 应用软件号 Project Name(13 bytes ASCII) 项目名称 | XXXXXXXXXXXXX XXXXXXXXXXXXX XXXXXXXXXXXXX XXXXXXXXXXXXX |

**Remarks备注：**

See ECU data in diagnostic specification for details of byte numbers, values and
ranges. The ECU data must be verified with the demand data of the tester
software.

(These data may change in case of revision changes and should be capable to be
edited and to add new numbers).

将电子控制器中的数据读取出来并进行解析，确保一致再进行测试。（遇有更改请做相应变更）

Unknown System -\> Abort Test系统不匹配，中断测试

System detected -\> Continue系统匹配，继续测试

## 4.3 Check Process byte检验加注状态

| **Diagnostic Function诊断功能：Read Data By Local Identifier通过本地身份标识读取数据** |              |                                        |
|----------------------------------------------------------------------------------------|--------------|----------------------------------------|
| Service Code请求服务代码 Record Local Identifier本地身份标识                           | 21h 01h      |                                        |
| **Positive Response肯定应答**                                                          |              |                                        |
| Service Code请求服务代码 Routine Local Identifier本地例程标识 Status状态               | 61h 01h xxh  |   55h = ok.                            |
| **ECU Data can be send by ECU ECU发送的数据**                                          |              |                                        |
| Delivery State Filling Successfully Filling Not Successfully                           | FFh  55h AAh | 交付状态（初始状态） 加注成功 加注失败 |

**Remarks备注：**

The ECU data must be verified with the demand data of the tester software. The
demand data in the table above are only recommended values from SFB side. For no
communication it is useful to take the delivery state of the process byte (FF
Hex). The Process byte identifies whether the previous on line evacuate/fill
process or the off line repair bleed process has been executed correctly.
Precondition to evaluate this byte is, that both, the on line evacuate/fill
equipment as well as the off line repair bleed equipment have the capability to
write the process byte.

诊断仪软件发送请求到电子控制器，读取的加注标识需要得到校验，上表中所述的加注状态值由赛福提供，仅供参考。赛福出厂的值为默认值（FFH）。加注状态值用以指示，前一道工序是否正常完成（加注成功，或者排气成功）。加注设备和排气设备应具备写“加注状态标志”的能力，否则此状态值无意义。

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat request”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request (7Fh 21h 21h)” shows the ECU, that the request is understood, but
the previous request is still being executed and its result might affect the
response to the requested service. The tester has to send the same request
again, until it gets a final response (positive or negative with LID different
from 21)). For more details see diagnosis function description (chapter process
data).

如果服务执行时间超过50毫秒，电子控制器会回复“繁忙”应答，每收到一条“繁忙”应答，（繁忙说明电子控制器已响应诊断仪发送的服务请求，如“7F
21
21”）诊断仪应重复当前命令，直至电子控制器回复肯定应答（或者非“繁忙（21H）”应答）。详见“诊断功能描述文档”。

Process byte incorrect -\> Abort Test加注失败，中断测试

Process byte correct -\> Continue加注成功，继续测试

## 4.4 Read Fault Code Memory读取故障代码

| **Diagnostic Function诊断功能： Read Status of Diagnostic Trouble Code读取诊断故障代码状态** |                                                         |                         |                                      |
|----------------------------------------------------------------------------------------------|---------------------------------------------------------|-------------------------|--------------------------------------|
| Service Identifier (Request)服务标识请求                                                     | 17h                                                     |                         |                                      |
| Group of DTC high byte诊断故障码组（高位字节）                                               | FFh                                                     |                         |                                      |
| Group of DTC low byte诊断故障码组（低位字节）                                                | 00h                                                     |                         |                                      |
| **Complete Answer完整回复**                                                                  |                                                         |                         |                                      |
| Service Code (Response) 服务代码应答                                                         | 57h                                                     |                         |                                      |
| Number of DTC诊断故障代码数量                                                                | xxh                                                     |                         |                                      |
| DTC high byte诊断故障代码（高位字节）                                                        | xxh                                                     |                         |                                      |
| DTC low byte 诊断故障代码（低位字节）                                                        | xxh                                                     |                         |                                      |
| Status of DTC X诊断故障代码状态                                                              | xxh                                                     |                         |                                      |
| **Evaluation评估**                                                                           |                                                         |                         |                                      |
| ECU – Data ECU数据                                                                           | Number of stored fault codes (Hex) 存储的故障代码的数量 | DTC (Hex)  诊断故障代码 | Status of DTC (Hex) 诊断故障代码状态 |
|                                                                                              | xx                                                      | xx xx                   | xx                                   |

**Remarks备注：**

The ECU outputs the content of the entire fault code memory. This data includes
several information. The maximum number of stored faults is 6. The number of the
transmitted fault codes is equal to the number of stored fault codes (0 to 6).

电子控制器回复全部故障代码，包括总数，最大容量为6个故障（可以全部发送给诊断仪）。

Out of the transmitted data, the following must be
evaluated输出数据需评估以下参数：

\-number of DTC 故障总数

\-fault code number (DTC) 故障代码

\-the status of DTC 故障状态

The tester has to evaluate the fault code data, to transform the number into a
failure text and to issue a protocol. More information see the Functional
description of diagnosis. Only permanent faults (Status of DTC = 01HEX) will
lead to abort the test cycle. History faults must be ignored.

诊断仪必须评估故障代码，将故障代码转化为故障描述，并进行处理，故障代码描述请见“诊断功能描述文档”。若有当前故障（标志为01H），需中断测试，历史故障则可以忽略。

Current fault present -\> Abort test 当前有故障，中断测试

No current fault present -\> Continue (Ignore faults) 当前没有故障，继续测试

**Conditions: 条件**

wheel speed sensor faults that may have been stored in the ECU by previous
assembly equipment will stay stored as current faults. Therefore, all wheel
speed sensor (current and history) must be ignored during the evaluation. These
faults will be detected in test step “wheel speed sensor test”).

轮速传感器的错误可能是之前工序遗留下来并存储在电子控制器中的故障。所以，关于轮速传感器的故障可以忽略。轮速传感器错误检测会在“轮速传感器测试”步骤中进行。

**Example 1: No Fault Codes stored无故障代码存储**

| **Read Fault Code Memory读取故障代码内存**  |                                                                                |
|---------------------------------------------|--------------------------------------------------------------------------------|
| Diagnostic function诊断功能                 | Read Status of Diagnostic Trouble Code读取诊断故障代码状态（请求）             |
| Service Code请求服务代码 Data Bytes数据字节 | 17h FFh 00h                                                                    |
| **Evaluation评估**                          |                                                                                |
| Correct Conditions正确情况                  | No fault codes stored没有故障代码存储                                          |
| Diagnostic function诊断功能                 | Read Status of Diagnostic Trouble Code(P. Response) 读取诊断故障代码状态(响应) |
| Service Code应答服务代码                    | 57h                                                                            |
| Data Bytes数据字节                          | 00h                                                                            |

**Example 2: 3 Fault codes stored in the ECU ECU中存储了3个故障代码**

| **Read Fault Code Memory读取故障代码内存**                                                                                                       |                                                                                |                               |
|--------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|-------------------------------|
| Diagnostic function诊断功能                                                                                                                      | Read Status of Diagnostic Trouble Code读取诊断故障代码状态（请求）             |                               |
| Service Code服务代码                                                                                                                             | 17h                                                                            |                               |
| Data Bytes数据字节                                                                                                                               | FFh 00h                                                                        |                               |
| **Evaluation评估**                                                                                                                               |                                                                                |                               |
| Incorrect Conditions错误情况                                                                                                                     | 3 Fault codes stored 3个错误代码存储                                           |                               |
| Diagnostic function诊断功能                                                                                                                      | Read Status of Diagnostic Trouble Code(P. Response) 读取诊断故障代码状态(响应) |                               |
| Service Code服务代码                                                                                                                             | 57h                                                                            |                               |
| Data Bytes数据字节                                                                                                                               | 03h                                                                            |                               |
| DTC \#1 High Byte诊断故障代码1（高位字节）                                                                                                       | 00h                                                                            |                               |
| DTC \#1 Low Byte诊断故障代码1（低位字节）                                                                                                        | 44h                                                                            |                               |
| Status of DTC \#1诊断故障代码状态1                                                                                                               | 00h                                                                            |                               |
| DTC \#2 High Byte诊断故障代码2（高位字节）                                                                                                       | 00h                                                                            |                               |
| DTC \#2 Low Byte 诊断故障代码2（低位字节）                                                                                                       | 45h                                                                            |                               |
| Status of DTC \#2诊断故障代码状态2                                                                                                               | 00h                                                                            |                               |
| DTC \#3 High Byte诊断故障代码3（高位字节）                                                                                                       | 00h                                                                            |                               |
| DTC \#3 Low Byte诊断故障代码3（低位字节）                                                                                                        | 46h                                                                            |                               |
| Status of DTC \#3诊断故障代码状态3                                                                                                               | 01h                                                                            |                               |
| Number of stored fault codes存储的故障代码 3 Faults stored 存储3个故障 (Max.: 6)  2 Faults not present 2个历史故障  1 Fault present 1个当前故障  |                                                                                |                               |
| DTC (Hex)诊断故障代码                                                                                                                            | Text of fault code故障代码目录                                                 | Status of DTC诊断故障代码状态 |
| C0044                                                                                                                                            | Solid State Relay_Relay over current固态继电器_继电器过流                      | i.e.: not present 历史        |
| C0045                                                                                                                                            | Solid State Relay_Relay shorted(Stuck on) 固态继电器_继电器短路（卡死）        | i.e.: not present 历史        |
| C0046                                                                                                                                            | Solid State Relay_Relay shorted to ground固态继电器_与地短接                   | i.e.: present 当前            |

## 4.5 Check Input-/ Output-Signals输入输出信号检测

| **Diagnostic Function诊断功能：Read Data By Local ldentifier根据本地身份标识读取数据**                                                       |                            |                                |                                                                                          |
|----------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|--------------------------------|------------------------------------------------------------------------------------------|
| Read Data By Local Identifier (Request)根据本地身份标识读取数据(请求) Record Local Identifier本地身份标识记录                                | 21h 04h                    |                                |                                                                                          |
| Read Data By Local Identifier (Response)根据本地身份标识读取数据(应答)                                                                       | 61h                        |                                |                                                                                          |
| Record Local Identifier本地身份标识记录                                                                                                      | 04h                        |                                |                                                                                          |
| **ECU Data to be evaluated待评估的ECU数据：**                                                                                                |                            |                                |                                                                                          |
| ECU-Data ECU数据                                                                                                                             | Byte / Bit 字节/位         | Actual Data 实际数据           | Operator 操作者                                                                          |
| Front Brake Light Switch (First request) 前刹车灯开关（第一次请求）\* Rear Brake Light Switch (First request) 后刹车灯开关（第一次请求）\*   | Byte 4/Bit 5  Byte 4/Bit 4 | 1-\>ON,0-\>OFF  1-\>ON,0-\>OFF | Actuate the front brake pedal踩下前刹车踏板 Actuate the rear brake pedal踩下后刹车踏板   |
| Front Brake Light Switch (Second request) 前刹车灯开关（第二次请求）\* Rear Brake Light Switch (Second request) 后刹车灯开关（第二次请求）\* | Byte 4/Bit 5  Byte 4/Bit 4 | 1-\>ON,0-\>OFF  1-\>ON,0-\>OFF | Release the front brake pedal 松开前刹车踏板 Release the rear brake pedal 松开后刹车踏板 |
| ABS OFF Switch  ABS状态切换开关（第一次请求）                                                                                                | Byte 4/Bit 3               | 1-\>ON,0-\>OFF                 | Press the off switch按下切换开关                                                         |
| ABS OFF Switch ABS  ABS状态切换开关（第二次请求）                                                                                            | Byte 4/Bit 3               | 1-\>ON,0-\>OFF                 | Release the off switch松开切换开关                                                       |

\* Whether the brake switch signals are tested depend on the software
configuration and hardware interface.

\* 根据软件配置和硬件接口决定是否检测刹车开关信号。

**Remarks备注：**

For details of byte numbers, values and ranges see diagnosis function
description. The ECU data must be verified with the limit data of the tester
software. The operator prompts (“release front/rear brake pedal”, “actuate
front/rear brake pedal”, “press/release ABS off switch”, etc.) must be
identified on display.

关于数据字节，数值和范围请参见“诊断功能描述文档”诊断仪请求的范围需在电子控制器限制范围内。操作人员的动作应显示在屏幕上（“松开前/后刹车踏板”，“踩下前/后刹车踏板”
，“按下/松开切换开关”等）

Data correct -\> Continue数据正确，继续测试

Data not correct -\> Failure message, continue排除故障信息，继续

## 4.6 Wheel Speed Sensor Test轮速传感器测试

| **Wheel speed sensor test (correlation and signal quality check) 轮速传感器测试（一致性和信号品质）** |                        |                        |                 |                                                       |
|-------------------------------------------------------------------------------------------------------|------------------------|------------------------|-----------------|-------------------------------------------------------|
| Test standard测试参考标准                                                                             | ECU data电子控制器回复 | Requested data请求数据 |                 |                                                       |
| Roll Front                                                                                            | On                     | Wheel F :              | xx km/h         | 4,0 km/h \< xx \< 5,0 km/h                            |
| Roll Rear                                                                                             | Off                    | Wheel R :              | xx km/h         | 0,0 km/h \< xx \< 2,75 km/h                           |
| Roll Front                                                                                            | On                     | Wheel F :              | xx km/h         | 4,0 km/h \< xx \< 5,0 km/h                            |
| Roll Rear                                                                                             | On                     | Wheel R :              | xx km/h         | 4,0 km/h \< xx \< 5,0 km/h                            |
| Roll Front                                                                                            | On                     | Wheel F min: max:      | xx km/h xx km/h | 4,0 km/h \< xx \< 5,0 km/h 4,0 km/h \< xx \< 5,0 km/h |
| Roll Rear                                                                                             | On                     | Wheel R min: max:      | xx km/h xx km/h | 4,0 km/h \< xx \< 5,0 km/h 4,0 km/h \< xx \< 5,0 km/h |

**Remarks备注：**

To check the correlation of the sensors (connection of sensor to the
corresponding wheel), the test rig turns on the individual rolls one after the
other. The test speed must be adapted to the dynamometer design. (e.g. test
speed = 4,5 km/h). The tester records the wheel speed data received from the ECU
and verifies the signals.

During the signal quality test, all rolls will be turned on (this step will be
executed immediately after the correlation test). The ECU runs an internal
routine that records all sensor data over at least one revolution, stores the
minimum and maximum speed data of each wheel during the test time and outputs
these data to the tester after the test has been finished. The allowed tolerance
amounts 5% of V rolls.(for details refer the next two pages). The test bench
computer evaluates these data and compares them with internal limit data.

为检测传感器信号一致性（传感器和轮毂一一对应），需对轮子进行逐个测试。测试速度可根据测功机需求进行调整。诊断仪记录电子控制器回复的速度并将之与转鼓台数据进行校验。在信号品质测试中，所有轮速传感器需开启（这一步需紧跟信号一致性测试）。电子控制器运行内部程序，记录传感器的值，记录最小和最大值，并将之输出给诊断仪，参考误差是5%。测试台电脑评估这些数据，将之与内部数据进行比对。

Sensor failure detected -\> Failure message,
continue检测到传感器故障，排除故障信息，继续

No failures detected -\> Continue 未检测到故障，继续

**Start of the wheel speed sensor test开始轮速传感器测试**

| **Diagnostic Function诊断功能: Start WSS Test Routine By Local Identifier根据本地身份标识开始轮速传感器测试例程** |             |
|-------------------------------------------------------------------------------------------------------------------|-------------|
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识 Duration持续时间                              | 31h 12h xxh |
| **Positive Response肯定应答**                                                                                     |             |
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识                                               | 71h 12h     |

**Remarks批注：**

The byte for the execution time 1 is set to 100 milliseconds (signal correlation
check). The byte for the execution time 2 is set to about 3 seconds (one
revolution of the wheels).
1位表示100毫秒，测试时间可设为大约3秒（轮速分辨率的一种）。

Resolution分辨率：1 LSB = 100ms/Bit，1bit=100ms

**Evaluation of the wheel speed sensor test轮速传感器测试**

| **Diagnostic Function诊断功能: Request WSS Test routine results by local identifier根据本地身份标识请求轮速传感器测试例程结果** |     |
|---------------------------------------------------------------------------------------------------------------------------------|-----|
| Service Code (Request)服务代码（请求）                                                                                          | 33h |
| Routine Local Identifier本地例程标识符                                                                                          | 12h |
| Service Code (P. Response) 服务代码（应答）                                                                                     | 73h |
| Routine Local Identifier本地例程标识符                                                                                          | 12h |
| Status of requested question请求问题状态                                                                                        | 02h |
| Wheel speed of front wheel maximum (HB)                                                                                         | xxh |
| Wheel speed of front wheel maximum (LB)                                                                                         | xxh |
| Wheel speed of front wheel minimum (HB)                                                                                         | xxh |
| Wheel speed of front wheel minimum (LB)                                                                                         | xxh |
| Wheel speed of rear wheel maximum (HB)                                                                                          | xxh |
| Wheel speed of rear wheel maximum (LB)                                                                                          | xxh |
| Wheel speed of rear wheel minimum (HB)                                                                                          | xxh |
| Wheel speed of rear wheel minimum (LB)                                                                                          | xxh |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |
| Reserved                                                                                                                        | 00h |

**Remarks备注：**

All result data of the ECU (Min/Max values of each wheel) must be evaluated. If
the status of the routine is not 02 Hex, there was a problem during the
execution of the routine and the results of the routine are not valid. A
repetition of the test is necessary.

电子控制器回复的最大和最小值均要评估。如果电子控制器回复的不是02H，则此时收到的数据不作为参考，因为此时电子控制器可能发生故障，需要重新测试。

Resolution v速度分辨率：1 bit = 0.028km/h or 0.0078125m/s

Example for calculation of the allowed WSS tolerance轮速误差的计算举例：

V rolls’ 转毂台速度= 4.5km/h

WSS min轮速传感器最小值= 4.5km/h – 5% = 4.27 km/h

WSS max轮速传感器最大值= 4.5km/h + 5% = 4.73 km/h

Allowed WSS tolerance允许误差：0.225 km/h

The given tolerance is calculated without the influence of tire pressure,
tolerance of the test bench and the ECU electrical circuit tolerance. The valid
tolerance must be found and confirmed by trials at the customer.

本文档所述误差未考虑以下影响因数：轮胎压力、测试台误差、电子控制单元电路误差。至于采用多少误差由客户自己根据实验来确定。

**Stop and Clear buffer value of “WSS Test”停止轮速测试并清除缓存数据**

| **Diagnostic Function诊断功能: Stop WSS Test Routine By Local Identifier根据本地身份标识停止轮速传感器测试例程** |         |
|------------------------------------------------------------------------------------------------------------------|---------|
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识                                              | 32h 12h |
| **Positive Response肯定应答**                                                                                    |         |
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识                                              | 72h 12h |

| **Wheel speed sensor test (correlation and signal quality check) 轮速传感器测试（一致性和信号品质）** |
|-------------------------------------------------------------------------------------------------------|
|                                                                                                       |

**Remarks备注：**

The test rig turns on the individual rolls by external drives step by step while
the tester requests the speed data of the sensors and checks the correct
correlation. The tester then runs a function that checks the sensor quality over
a minimum of one revolution for all wheels and evaluates whether the speeds are
within a certain limit, The ECU internally picks up each sensor speed every 10
ms, stores and outputs the minimum and maximum speed data (within the test time)
in order to identify faults of the sensor, toothed wheels, air gaps or
eccentricities.

测试系统逐个打开转鼓台，同时发送轮速测试命令获取电子控制器输出的轮速信号，将之与转毂台数据进行比对，用以评价信号的一致性。诊断仪稍后测试信号质量，该测试过程需要2个轮速同时运行，一起测试。电子控制器每10ms为一个分辨率采集轮速信号，存储并输出其最小和最大值（在设定的测试时间内），用以识别轮速传感器安装错误、缺齿、间隙大、偏心等。

| **Signal quality test (example of one wheel)信号品质测试（以一个轮子为例）：** |
|--------------------------------------------------------------------------------|
|                                                                                |

**Remarks备注：**

After the routine has been started, the ECU will continuously sample all wheel
speed data and check for the minimum and the maximum value during the execution
time. This data (for each wheel) is transmitted to the test equipment. The test
equipment must evaluate this data and compare with given limits. The limits are
defined to meet the specified tolerances of the wheel speed signals. The
tolerance of the roller speed must be minimized. The test speed must be adapted
onto the minimum specified speed of the wheel speed sensors.

当诊断仪发送轮速测试请求并得到电子控制器的响应后，电子控制器就开始持续监测轮速信号并计算最小和最大值（在设定的时间范围内）。电子控制器会将每个轮速的数值发送给诊断仪，诊断仪需评估比对从电子控制器获取的数据。误差范围仅用于测试传感器的信号，转毂台的误差应做到最小。测试速度应以设定的能识别故障的最小轮速为测试轮速。

**Fault simulations故障仿真：**

| **Fault simulation故障仿真：missing tooth at tone wheel (damaged multipole)齿圈缺齿** |
|---------------------------------------------------------------------------------------|
|                                                                                       |

| **Fault simulation故障仿真：Air gap to big or eccentricity间隙过大或偏心** |
|----------------------------------------------------------------------------|
|                                                                            |

## 4.7 Dynamic ABS test on a brake dynamometer with 2 independent rolls通过2个带独立转鼓的测功机来动态测试防抱死制动系统

| **ABS Test ASB测试** **Solenoid valve functional test and valve correlation test电磁阀功能及一致性测试** |                                                 |                  |         |                     |
|----------------------------------------------------------------------------------------------------------|-------------------------------------------------|------------------|---------|---------------------|
| Operator操作者                                                                                           | Test Rig测试装置                                | BrakeWheel制动轮 | Force力 | Demand Data要求数据 |
| Apply Front Brake Pedal 踩下前刹车踏板                                                                   | Pressure Apply F增压 Measure Brake Forces测压   |  Wheel F         |  xx N   |  F1\< FF\< F2       |
| Apply Rear Brake Pedal 踩下后刹车踏板                                                                    | Pressure Apply R增压 Measure Brake Forces测压   |  Wheel R         |  xx N   |  F3\< FR \< F4      |
| Keep Front Brake Pedal Constant保持前刹车踏板                                                            | Pressure Release F减压 Measure Brake Forces测压 |  Wheel F         |  xx N   |  FF \< F5           |
| Keep Rear Front Pedal Constant保持后刹车踏板                                                             | Pressure Release R减压 Measure Brake Forces测压 |  Wheel R         |  xx N   |  FR \< F5           |
| Keep Front Brake Pedal Constant保持前刹车踏板                                                            | Pressure Apply F增压 Measure Brake Forces测压   |  Wheel F         |  xx N   |  FF\> F6            |
| Keep Rear Brake Pedal Constant保持后刹车踏板                                                             | Pressure Apply R增压 Measure Brake Forces测压   |  Wheel R         |  xx N   |  FR \> F7           |
| Release Front Brake Pedal 松开前刹车踏板                                                                 | Deactivate valves电磁阀断电                     |  Wheel F         |  xx N   |  FF \< F8           |
| Release Front Brake Pedal 松开后刹车踏板                                                                 | Deactivate valves电磁阀断电                     |  Wheel R         |  xx N   |  FR \< F9           |

**Remarks备注：**

While all rolls are running, the operator applies the brake force, the test rig
measures the brake forces, runs individual pressure release and recovery cycles.
In addition the test rig measures and evaluates the brake forces in order to
check the proper function and the correlation of the hydraulics. This test is
performed as correlation test for vehicles with ABS. During the test the
operator shall keep the brake pedal constant. The timing of valve actuation and
brake force measuring times must be adapted onto the dynamics of the

dynamometer and the vehicle configuration. All mentioned force values are TBD
and must be confirmed by trials.

当转毂台开始转动时，操作人员踩下刹车踏板，测试设备采集压力，发送减压增压和循环命令。测试设备检测和评估制动压力，用以检验增减压功能执行后，制动液压管路压力一致性情况。该测试用于装有防抱死制动系统车辆的制动一致性测试。在测试过程中，操作人员需要一直踩下刹车踏板。电磁阀工作时间和压力采集时间需要根据测功机和车辆状况来设定。本文档所列压力参数值均有待确定，需根据实际情况进行测试后再做定夺。

Dynamic ABS Test ok. -\> Continue ABS动态测试通过，继续

Dynamic ABS Test not ok. -\> Set failure message, abort test
ABS动态测试失败，发送故障消息，停止测试

### 4.7.1 Deactivation of the safety software关闭安全软件模块

| **Diagnostic Function诊断功能：Single Output Control– Speed Limit Disable单独输出控制-关闭限速功能** |     |
|------------------------------------------------------------------------------------------------------|-----|
| Service Identifier (Request) 服务身份标识（请求）                                                    | 31h |
| Input Output Local Identifier本地身份标识输入输出                                                    | 1Eh |
| Start The Permanent Control开始永久控制                                                              | 20h |

**Important重要提示：**

The deactivation of the safety switches is necessary before Input output by
Local Identifier – “Actuator Test”. Before the vehicle can be accelerated to the
start speed between, the diagnostic speed limit function must be disabled at a
vehicle speed \< 10 km/h. For more please refer also the diagnosis
specification.

请在根据本地身份标识进行输入输出控制-执行器测试前关掉安全软件模块。请在速度达到10公里每小时前，关闭安全软件模块，详见“诊断功能描述文档”。

### 4.7.2 Diagnostic function “Actuator Test” for the ABS brake test “执行器测试”诊断功能测试ABS制动

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Request根据本地身份标识开始例程请求** |                                                        |
|--------------------------------------------------------------------------------------------------------|--------------------------------------------------------|
| Start Routine By Local Identifier根据本地身份标识开始例程                                              | 31h                                                    |
| Local Identifier (system supplier specific)本地身份标识                                                | D5h                                                    |
| Start control开始控制                                                                                  | 00h                                                    |
| Without results无结果                                                                                  | 00h                                                    |
| 1.Actuation value驱动值 1. Actuation number驱动数                                                      | xxh xxh xxh xxh                                        |
| 2.Actuation value驱动值 2. Actuation number驱动数                                                      | xxh xxh xxh xxh                                        |
| Waiting time (HB)等待时间（高字节） Waiting time (LB)等待时间（低字节）                                | xxh xxh                                                |
| 3. Actuation value驱动值 3. Actuation number驱动数                                                     | xxh xxh xxh xxh                                        |
| 4. Actuation value驱动值 4. Actuation number驱动数                                                     | xxh xxh xxh xxh                                        |
| **Request data (only data bytes, Hex code)请求数据（只有数据字节）**                                   |                                                        |
| Start message 1(all inlet valves on)所有常开电磁阀得电                                                 | FF FF 00 30 00 00 00 00 00 01 FF FF 00 38 00 00 00 00  |
| Start message 2 (pump motor on)电机开始转动                                                            | FF FF 00 22 00 00 00 00 00 01 00 00 00 00 00 00 00 00  |
| Start message 3 (pressure release F)前轮减压                                                           | FF FF 00 32 00 00 00 00 t1 t1 00 00 00 32 00 00 00 00  |
| Start message 4 (pressure increase F)前轮增压                                                          | 00 00 00 30 00 00 00 00 t2 t2 FF FF 00 30 00 00 00 00  |
| Start message 5 (pressure release R)后轮减压                                                           | FF FF 00 3A 00 00 00 00 t1 t1 00 00 00 3A 00 00 00 00  |
| Start message 6 (pressure increase R)后轮增压                                                          | 00 00 00 38 00 00 00 00 t3 t3 FF FF 00 38 00 00 00 00  |
| Start message 7(all inlet valves off)所有常开电磁阀断电                                                | 00 00 00 30 00 00 00 00 00 01 00 00 00 38 00 00 00 00  |
| Start message 8 (after 2000ms pump motor off)电机转动2秒后关闭                                         | 00 00 00 00 00 00 00 00 t4 t4 00 00 00 22 00 00 00 00  |

**Remarks备注：**

The operator has to achieve a sufficient brake force, than the tester set all
inlet valves to pressure hold (start message 1). The pump motor runs from the
beginning to the end of the cycle of each axle (start message 2). Start messages
3 to 6 are used to run the pressure release/ -increase cycles of the wheels. In
order to minimize the test time, the wheel cycles of both axles are overlapped.
Start message 7 and 8 switch all valves and the pump motor after 2000 ms off.
Between the pressure increases and pressure releases must be a stabilization
time before the force values are evaluated.

操作人员先踩下刹车踏板，提供一定的制动压力，然后诊断仪再给常开电磁阀供电。从开始到结束电机需一直转动。为缩短测试时间，两轴测试可重叠测试，3-6命令用于对单个轮进行测试。命令7-8是关闭所有电磁阀，并驱动电机转动2秒。在增压和减压切换的过程中，压力需保持稳定，以便压力评估准确。

**Timing proposals建议时间：**

|     | **Time**   | **HB (Hex)** | **LB (Hex)** |
|-----|------------|--------------|--------------|
| t1: | 250 ms     | 00           | 19           |
| t2: | 50 ms      | 00           | 05           |
| t3: | 30 ms      | 00           | 03           |
| t4: | 10-2000 ms | 00           | 01-C8        |

Resolution分辨率：10ms/bit

t1, t2 and t3 are the activation times for the pressure release and increase
pulses. T4 is the time to discharge the accumulator chamber. (The timing is set
within the messages). The stabilization time to measure the brake forces must be
set by the test rig. The data beside are proposed timings. The final setting
must be done by

trails.

上表t1，t2，t3是常开和常闭电磁阀工作时间，t4是驱动电机抽空蓄能器时间。稳压时间需根据测试系统来确定。本文档所提供数据仅供参考，准确时间由设备测试确定。

| **Diagnostic Function诊断功能：Start Routine By Local ldentifier Response根据本地身份标识开始例程应答** |     |                             |
|---------------------------------------------------------------------------------------------------------|-----|-----------------------------|
| Negative response data (Hex Codes)否定应答数据：                                                        |     |                             |
| Service Identifier服务身份标识                                                                          | 7Fh |                             |
| Request Service Identifier请求服务身份标识                                                              | 31h |                             |
| Response Code应答代码                                                                                   | 21h | Busy Repeat Request繁忙请求 |

**Remarks备注：**

If the executing time is exceeding 50ms, the ECU will send a message “Busy
repeat re-quest”. After each “Busy repeat request” has the tester to repeat the
request for starting the routine. (Explanation: With the negative response “Busy
Repeat Request” shows the ECU, that the request is understood, but the previous
request is still being executed and its result might affect the response to the
requested service. The tester has to send the same request again, until it gets
a final response (positive or negative with LID different from 21)).

如果服务执行超过50毫秒，电子控制器会回复“繁忙”应答。每次收到“繁忙”应答（电子控制器已响应诊断仪的命令，并开始执行相关服务，只是执行所需时间较长），诊断仪应重复发送当前命令请求，直至电子控制器回复肯定应答（或者非“繁忙”应答）。

| **Diagnostic Function诊断功能： Start Routine By Local ldentifier Response根据本地身份标识开始例程应答** |     |   |
|----------------------------------------------------------------------------------------------------------|-----|---|
| Positive response data (Hex Codes)肯定应答数据：                                                         |     |   |
| Service Identifier服务身份标识                                                                           | 71h |   |
| Local Identifier (system supplier specific)本地身份标识                                                  | D5h |   |

### 4.7.3 Request “Actuator Test” Routine Results请求执行器测试例程结果

**Response Without Results 无返回结果响应**

| **Diagnostic Function诊断功能:Request Actuator Test Routine Results By Local Identifier根据本地身份标识请求执行器测试例程结果** |             |
|---------------------------------------------------------------------------------------------------------------------------------|-------------|
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识                                                             | 33h D5h     |
| **Positive Response肯定应答**                                                                                                   |             |
| Service Identifier服务身份标识 Routine Local Identifier本地例程标识 Status Of the Request Question请求问题状态                  | 73h D5h XXh |

**Following results are possible结果解释：**

“02 Hex” means routine was correct finished. “00 Hex” means routine error during
execution. To ensure a correct filled brake system, the vehicle must be repair
bleed.

“02H”表明服务已成功执行完成。“00H”表明服务执行过程中出错，为确保制动管路加注完好，管路必须可靠排气。

**Graphical presentation of the brake test cycle（example at one
wheel）**制动管路测试图示(单轮示例)

## 4.8 Warning Light Test 报警灯测试

| **Diagnostic Function诊断功能：Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |         |   |
|--------------------------------------------------------------------------------------------------------|---------|---|
| Service Code请求服务代码 Record Local Identifier本地身份标识                                           | 31h 06h |   |
| Routine Control Parameter例程控制参数 Start temporary control临时控制                                  |  00h    |   |
| **Positive Response肯定应答**                                                                          |         |   |
| Service Code请求服务代码 Routine Local Identifier本地例程标识                                          | 71h 06h |   |

**Remarks备注：**

During diagnostic mode, ABS warning lamp is always illuminated. After sending
orders and the ECU answers positively, the lamp will turn off 2 seconds and then
return to the state of illuminated.

在下线检测模式下，ABS报警灯常亮。发送指令且ECU肯定应答后，报警灯熄灭2s，然后后恢复到常亮状态。

Test correct -\> Continue测试通过，继续测试

Test not correct -\> Failure message, continue测试失败，排除故障信息，继续

## 4.9 Read Fault Code Memory读取故障代码

**For details look in chapter 4.4详见4.4节**

**Important Remark重要备注：**

After the end of line tests none present failure should be stored. In case of
present stored faults, eliminate the cause of the faults and repeat the EOL
tests until the vehicle is faultless.

下线检测之后不会存储当前故障，如果有当前故障，请排除故障后再重复进行下线检测直至车辆没有错误。

## 4.10 Clear Fault Code Memory清除故障代码

| **Diagnostic Function诊断功能：Clear Diagnostic Information Request清除诊断信息请求** |      |
|---------------------------------------------------------------------------------------|------|
| Service Code (request)服务代码（请求）                                                | 14h  |
| Group Of DTC High Byte诊断故障码组（高字节）                                          | FFh  |
| Group Of DTC Low Byte诊断故障码组（低字节）                                           | 00h  |
| Service Code (response) 服务代码（应答）                                              | 54h  |
| Group Of DTC High Byte诊断故障码组（高字节）                                          | FFh  |
| Group Of DTC Low Byte诊断故障码组（低字节）                                           | 00h  |
| ECU Data to be evaluated待评估的ECU数据                                               | none |

**Remarks备注：**

At the end of the test the fault codes are erased to ensure that there is no
code stored in the ECU after the vehicle leaves the assembly plant. The ECU
erases the entire data of the fault code memory. This will take about 1 second
execution time. The tester repeats the function “Read Fault Code Memory” again
for verification of the correct function of clearing the memory.

下线检测完成后需清除故障代码，这样就可以确保电子控制器在车辆出厂前将没有故障记录。电子控制器擦除故障记录单元所有数据。大概需要1秒钟来执行这项服务。清除故障代码后，诊断仪需要再发送“读取故障”命令，用以校验故障已清除。

“Fault still present” -\> Failure message,
continue故障依然存在，排除故障信息，继续

“No faults present” -\> Continue没有故障，结束

## 4.11 Diagnostics at the end of the End of line process下线检测结束的诊断

### 4.11.1 Step 1: Writing of EOL test status byte写下线检测标志

| **Diagnostic Function诊断功能：Write Data By Local Identifier根据本地身份标识写数据** |                                                                                                   |                    |
|---------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|--------------------|
| Service Identifier服务身份标识                                                        | 3Bh                                                                                               |                    |
| Routine Local Identifier例程本地身份标识                                              | 45h                                                                                               |                    |
| Status状态                                                                            | XXh                                                                                               | Status of EOL test |
| ECU Data to be written待写的ECU数据                                                   |                                                                                                   |                    |
| FFH 55H AAH                                                                           | Delivery State 交付状态（初始状态） EOL CONFIG DONE下线检测完成 EOL CONFIG NOT DONE下线检测未完成 |                    |
| **Positive Response肯定响应**                                                         |                                                                                                   |                    |
| Service Code服务身份标识                                                              | 7Bh                                                                                               |                    |
| Routine Local Identifier例程本地身份标识                                              | 45h                                                                                               |                    |

**Remarks备注：**

The ECU is shipped to the customers assembly line with a predefined EOL test
status byte: “FF Hex”. This number is reserved by SFB. In case of a non
successful communication this data will still stay in the EEPROM of the ECU
(“incorrect”). The EEPROM location is defined by SFB.

电子控制器到达客户工厂时应该是初始值“FF
Hex”，这个值是由宁波赛福写的初始值。在没有成功通信之前，这个初始值始终在电子控制器的存储器中，其具体地址由宁波赛福定义。

EOL test status byte writing correct -\> Continue状态写成功，继续

EOL test status byte writing not correct -\> Failure message,
continue状态写出错，排除故障信息，继续

### 4.11.2 Step 2: Verification of written EOL status byte/ End of Test下线检测状态校验/结束测试

| **Diagnostic Function诊断功能：Read Data By Local Identifier根据本地身份标识读取数据**    |                                                               |                                    |                              |
|-------------------------------------------------------------------------------------------|---------------------------------------------------------------|------------------------------------|------------------------------|
| Service Identifier (Request)服务身份标识（请求） Routine Local Identifier例程本地身份标识 | 21h 06h                                                       |                                    |                              |
| Status状态                                                                                | xxh                                                           |                                    |                              |
| 55H AAH                                                                                   | EOL CONFIG DONE下线检测完成 EOL CONFIG NOT DONE下线检测未完成 |                                    |                              |
| **ECU Data to be evaluated待评估的ECU数据：**                                             |                                                               |                                    |                              |
| ECU-Data ECU数据： EOL status byte 下线检测状态字节                                       | Conditions情况： EOL status byte下线检测状态字节              | Demanded data (hex)需求数据： xxH  | Evaluation评估： Correct正确 |

**Remarks备注：**

To be sure that the written EOL status byte was successful done by the ABS ECU,
the described byte should be evaluated.

为确保下线状态写入正确，诊断仪需要从电子控制器中读出该状态进行评估。

Written EOL test status byte incorrect -\> Set failure message; abort EOL
process写入失败，中断测试

**结束测试：**

| **Diagnostic Function诊断功能：Stop Communication Request 停止通信请求** |      |
|--------------------------------------------------------------------------|------|
| Stop Communication (Request)停止通信（请求）                             | 82h  |
| Stop Communication (P.Response)停止通信（应答）                          | C2h  |

# 5 Valve protective measures电磁阀保护措施

|          | **ABS**                                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------------------|
| Valves阀 | EOL routines (diagnostic mode) 下线检测程序（诊断模式）                                                                                 |
| NO 4,06Ω | The voltage is limited internal to 12V 内部限压12V Up and down counter with a ratio up/down = 2/1; limited to 30s单独控制电磁阀最长30秒 |
| NC 4,06Ω | Up and down counter with a ratio up/down = 2/1; limited to 30s单独控制电磁阀最长30秒                                                    |

**Remarks备注：**

All valve protective measures automatically active with using of the ROM
resident routines to avoid damages by overheating. These protective measures
cannot be disabled.

当运行下线检测程序时，为防止过热损坏电磁阀，该保护措施自动执行，这些保护措施不可关闭或禁止。

# 6 Test Rig Information测试操作信息

**Dynamometer design测功机选择：**

The test is designed to be performed on a 2-axle brake dynamometer (low speed).
To allow individual wheel test cycles the rolls of each wheel should be
independently driven by the test rig drives.

选择2轴制动的低速度测功机。可以单独控制每个轮毂进行旋转。

**Diagnostic Information诊断信息：**

The diagnostic computer should be as close as possible near the vehicle to avoid
communication problems. The timing (time gaps between messages and bytes within
messages) should be set close to the minimum possible limits in order to reduce
the test time. All other additional diagnostic information and functions are
customer specific.

诊断仪尽可能接近车辆，以防距离造成通信故障。通信时间间隔参数应与最小值接近，以缩短测试时间。其他信息遵循客户要求。

**Process Byte流程状态字节:**

The final definition of the process byte data must be taken from the supplier of
the evac/fill- and repair bleed equipment or the customer.

抽真空加注状态字节数值的定义遵循客户定义或者供应商定义的参数。

**Wheel Speed Sensor Test轮速传感器测试：**

The correlation check is executed by starting the individual rolls with a delay
between each wheel if possible.

一致性检测时，最好在每个轮毂测试之间做一点延时。

**Editor menus编辑菜单：**

ECU Identification codes may change during production due to updates of software
revisions. It is important to set up the software program to modify
identification numbers easily by using an editor menu.

电子控制器的身份标识信息会随生产软件的修改而发生变更。建议在测试软件中设置菜单编辑功能用于快速更改身份标识信息。

The timing of the dynamic valve test must be found during test trials. Timing of
valve actuation cycles, such as actuation times and stabilization times should
be included in an editor menu.

电磁阀动态测试时间应通过实验来确定。电磁阀得电时间，运行周期，稳压时间也应包含在菜单编辑窗口中。

Upper and lower limit values for evaluation should also be included in an editor
menu for simple adaptation or modifications. Due to the various vehicle types
and configurations, different actuation times for the valves cycles of the
dynamic ABS test might be required. These data should be available in separate
parameter file within the test equipment software and also easily be modified by
using an editor menu. The selection of the vehicle type should be done by either
a bar code reading or an operator selection when driving into the test
rig.菜单上还需有数值上限和下限值编辑窗口，用以修改以适应不同状况下的车辆信息。因不同车型和配置，阀和电机的执行时间有所区别，所有这些数据应有各自独立文件加以区分，同时也可通过编辑窗口进行修改。车型选择可通过条形码或者操作人员手动选择。

**Test protocol测试协议：**

In case of an ok test result, a print out (“test passed”) is made. In case of a
not ok test result, a failure protocol must be printed out. This protocol must
include all test data of the test step that failed in order to allow a better
failure analysis. An entire test protocol of all test results must be available
on request.

当测试通过时，需要打印“测试通过”；而测试失败时，也需打印失败信息。测试过程中的错误应记录下来，用以分析处理，方便以后翻阅测试结果时，随时可以看到测试数据。

**Vehicle conditions车辆状况：**

The battery must be charged properly in order to allow a sufficient power supply
to the system. The engine should be running in order to apply a sufficient power
supply.

为保证电量正常，请将电平充满。当下线检测运行时请保证发动机正常运转，用以提供足够动力。

# 7 Attachments附件

### 7.1.1 Attachment 1: Hydraulic circuit diagram for ABS diagonal brake split液压单元布局图

### 7.1.2 Attachment 2: Electric wiring diagram for Customer Car with ABS电气连接图

See Technical Customer Document.

参见客户技术文档。
