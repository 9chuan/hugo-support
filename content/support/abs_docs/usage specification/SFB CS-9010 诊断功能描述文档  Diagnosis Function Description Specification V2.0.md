---
title: SFB CS-9010 诊断功能描述文档
linktitle: SFB CS-9010 诊断功能描述文档
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

| ![](media/18adad495b7088a124cf37a2e88efbdd.png) | 客户规范 CUSTOMER SPECIFICATION                               |                 |
|-----------------------------------------------------|---------------------------------------------------------------|-----------------|
| SPEC NO. SFB CS- 9010                               | Diagnosis Function Description Specification 诊断功能描述文档 | SF10 ABS System |
| Version:V2.0                                        |                                                               |                 |

**Project Information**

| Customer客户： Vehicle车型：                                |                                                            |
|-------------------------------------------------------------|------------------------------------------------------------|
| System系统： Channel通道：                                  | ABS  2 Channel System两通道管路/1 Channel System单通道管路 |
| Diagnosis诊断： Kind of communication通信： Equipment设备： | Based on Customer KWP2000基于KWP2000协议 K-Line K线        |

**Release Department**

| **Department** | **Date** | **Signature** |
|----------------|----------|---------------|
|                |          |               |
|                |          |               |
|                |          |               |

**History List:**

| **Version** | **Edit**    | **Date**   | **Descriptions**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|-------------|-------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1.0         | Taylor Wang | 2015.05.24 | Draft                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| 1.1         | Rich Chen   | 2015.08.30 | Update “DTC list ”                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| 1.2         | Taylor Wang | 2015.11.30 | Update “Start Communication”; Update “Read Data By Local Identifier”; Update “Input Output Control By Local Identifier”; Update “Start Routine By Local Identifier”;Update “Request Routine Results By Local Identifier”.                                                                                                                                                                                                                                                                                    |
| 1.3         | Taylor Wang | 2015.12.12 | Update “Overview of Supported Services”; Delete “Supported Local Identifier (Start Routine By Local Identifier)”.                                                                                                                                                                                                                                                                                                                                                                                            |
| 1.4         | Rich Chen   | 2015.12.31 | Modify the number of DTC from ten to six in fault memories in the section “Read Status of Diagnostic Trouble Code”and “Read Diagnostic Trouble Code By Status”; Update “DTC list ”: add the DTC “Brake Diode Breakdown”; Add “If request all groups of DTC, DTC high byte is defined by “FFH”, DTC low byte is defined by “00H”.” in the section “Read Status of Diagnostic Trouble Code”; Modify the file name from “Function Description Specification to “Diagnosis Function Description Specification.”. |
| 1.5         | Rich Chen   | 2016.3.31  | update the services “Security Access”, add the calculation way of the key. Delete the routine control parameter “stop control(11H)” in single output control and “Speed limit disable” could only be stopped by sending a request of stop routine Modify the request message of vacuum filling：the sixth byte is used for channel selection.  Modify the request message of repair bleeding：add and reserve the sixth byte.                                                                                |
| 1.6         | Rich Chen   | 2016.5.30  | 1- Chapter 3.1: Add the negative responses33H and 24H  2- Chapter 2.5.2: Change ECU address from 0x35 to 0x28; Change tester address from 0xf1 to 0xf0. 3-Modify DTC list: change the DTC of “Warning Lamp output\_ Short to ground or open” from C0221 to C0213. 4- Change delivery state of the hydraulic filling indicator from 00H to FFH in chapter 3.2.11 5-Add delivery state of the EOL flag with FFH in chapter 3.2.11                                                                              |
| 1.7         | Rich Chen   | 2016.11.02 | 1-Modify some descriptive words or format.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| 1.8         | Rich Chen   | 2017.05.22 | Document standardization and “PS3010” to “SFB CS-9010”                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| 1.9         | Rich Chen   | 2017.05.24 | Mark C0060, C0061, C0062 with “ \* ” on the DTC list and make a annotation , it means “Whether the fault is detected depends on the software configuration and hardware interface”                                                                                                                                                                                                                                                                                                                           |
| 2.0         | Rich Chen   | 2018.07.20 | 1-DTC list add MCU DTC：C0024,C0032,C0033,C0040,C0041 2-Add warning light for the single output control, including the starting routine, stopping routine and requesting results. The routine local identifier is \$06.                                                                                                                                                                                                                                                                                      |

# 1 General Information总述

## 1.1Diagnostic Document诊断文档

| **NO**      | **Version** | **Description**                                                                           |
|-------------|-------------|-------------------------------------------------------------------------------------------|
| ISO 14230-3 | 1.5         | Road Vehicle Diagnostic System- Keyword Protocol 2000- Edition 1.5 Part 3: Implementation |
| SFB PS-4003 | V1.1        | 基于Kline KWP2000诊断规范                                                                 |

## 1.2Attachments(Schematic Drawing) 附件（示意图）

| **NO** | **Version** | **Description** |
|--------|-------------|-----------------|
|        |             |                 |
|        |             |                 |

# 2 Communication通信

## 2.1 Physical Layer物理层

The physical layer interface for keyword 2000 bus utilizes the single k line
communication. The keyword 2000 SFB10 ECU’s physical layer supports the 10.4kbps
bit rate for normal speed communication (TBD kbps for high speed communication).
For detail please reference the keyword protocol 2000-physical layer
iso-14230-1.

KWP2000协议物理层使用单根K线进行通信，宁波赛福K线正常通信支持10400比特每秒（高速通信待定），详见ISO14230-1，物理层协议国际规范。

## 2.2 Data Link Layer数据链接层

The SFB10 ECU supports only a Fast diagnosis initialization over the K-line. The
address information should be included in the message format. The length byte is
optional. The normal timing parameter set should be utilized. The supported key
bytes is ＄8FEA. For detail please refer to keyword protocol 2000 data link
layer recommended practice; ISO-14230-2

宁波赛福电子控制器仅支持基于K线的快速初始化，地址信息应包含在消息格式里。数据长度字节可选，常规通信时间参数已设定好，支持的关键字节是“8FEA”，详见ISO14230-2数据链接层。

## 2.3 Block Structure报文结构

The message structure consists of 3 parts: Header, Data bytes, Checksum.

消息结构包括3部分：消息头，数据字节，校验和。

**Header数据头**

The header part can have a maximum of 4 bytes depending on the initial Format
Byte.

数据头部分最大可以有4个字节，这取决于初始格式字节。

**Format byte格式字节**

The format byte (Fmt) contains 2-bit address mode information at bit 7 (A1) and
bit 6 (A0), and 6-bit length information at bits 5 - 0. The tester is informed
about use of header bytes by the key bytes. The ECU supports the following
values for the 2-bit address
mode格式字节在bit7（A1）位和bit6（A0）位包含2位地址模式信息，在bit5-0位包含6位长度信息。ECU通过关键字通知诊断仪是否使用头部信息，并支持以下2位的地址模式：

| **A1** | **A0** | **Mode**                                                           |
|--------|--------|--------------------------------------------------------------------|
| 0      | 0      | No address information 不带地址信息                                |
| 1      | 0      | With address information, physical addressing 带地址信息，物理地址 |

Note: A1, A0 = ‘0, 1’ for CARB mode are NOT supported在例外模式下不支持

A1, A0 = ‘1, 1’ for Functional addressing mode are NOT
supported在功能寻址模式下不支持

The 6-bit length information defines the length of a message from the beginning
of the data field (Service Identification byte included) to checksum byte (not
included). If these bits are set to zero, then an additional length byte is
required.

6位长度信息定义了从数据区开始（包括服务身份标识字节）到检验和字节（不包括）的信息长度。如果这些位都置0，则需附加长度字节。

**Target address byte目标地址字节**

The target address (TA) byte indicates the addressed node. In case of Request
blocks, the Target address should have the Physical address of the ECU. The
target address of the ECU Response blocks will be set with the same value as the
Source Address of the Request Block.

目标地址字节指明了地址节点。发送给ECU的请求信息中的目标地址应该是ECU的物理地址。ECU响应信息的目标地址与请求信息的源地址一样。

**Source address byte源地址字节**

The Source address (SA) byte indicates the address of the transmitting node. In
case of Request blocks, the Source address should have the address of the
Tester. In Response block from the ECU, this address will have the Physical
address of the ECU.

源地址字节指明了传输节点的地址。请求信息中的源地址应该是测试仪的地址。在ECU的响应信息中，源地址将包含ECU的物理地址。

**Length byte 长度字节**

This additional length byte is provided if the 6-bit length field of the the
Format byte is set to 0. This byte defines the length of a message from the
beginning of the data field (service identification byte included) to checksum
byte (not included). Though it is possible to use a data length of 1 to 255
bytes, the ECU can receive only a maximum data length of DBmax bytes. Thus the
longest message can have a maximum of (DBmax+5) bytes only.

如果格式字节中长度字节（L0到L5）被置0，则提供这个附加长度字节。这个字节定义了从数据区开始（包括服务身份标识字节）到校验和字节（不包括）的信息长度。尽管1至255字节的数据长度是可用的，但是ECU仅能接受数据字节中最大数据长度，因此最长的信息只能为最大数据字节DBmax+5。

**Data bytes数据字节**

The data field may contain up to 63 or up to 255 bytes of information, depending
on the use of length information. The first byte of the data field is the
service identification byte. It may be followed by parameters and data depending
on the selected service.

数据段可能包含63到255个字节数据，具体根据长度信息确定，第一个字节是服务身份标识字节，紧跟着的是参数还是数据由选择的服务来决定。

**Checksum校验和**

The checksum byte (cs) inserted at the end of the message block is defined as
the simple 8-bit sum series of all bytes in the message, excluding the checksum.

校验和字节，插在信息块末尾，定义为除校验和之外的信息中所有字节的8位简单求和。

## 2.4 Data Formats数据格式

### 2.4.1 Block Format报文格式

The ECU must be support two types of message block formats based on the message
Header part, as illustrated below
ECU需支持2种形式的以消息数据头部分为基础的消息报文格式，如下所示：

**FORMAT 1**-**Header with address information, no additional length byte**

格式1–消息头有地址信息，没有附加长度字节

| **Length**   |    |    |     |      |    |
|--------------|----|----|-----|------|----|
| Fmt          | TA | SA | SID | Data | CS |
| **Checksum** |    |    |     |      |    |

**FORMAT 2**-**Header with address information, with additional length byte**

格式2-消息头有地址信息，有附加长度字节

|  **Length**  |    |    |     |     |      |    |
|--------------|----|----|-----|-----|------|----|
| Fmt          | TA | SA | Len | SID | Data | CS |
| **Checksum** |    |    |     |     |      |    |

| Fmt -Format Byte格式字节            | Len -Additional Length Byte 附加长度字节 |
|-------------------------------------|------------------------------------------|
| TA -Target Address Byte目标地址字节 | SID -Service Identifier 服务身份标识     |
| S A -Source Address Byte源地址字节  | CS -Checksum 校验和                      |

### 2.4.2 Byte Format字节格式

The following format applies to the individual bytes of a block during a
diagnosis session下面的格式在诊断过程中应用于报文的独立字节：

![](media/94e91cec4af6a16b47cdac5eab234813.png)

| 1 Start bit (Logic 0)开始位（逻辑0）                               |
|--------------------------------------------------------------------|
| 8 Data bits without parity (LSB first)8位无奇偶数据位（从LSB开始） |
| 1 Stop bit (Logic 1)停止位（逻辑1）                                |

## 2.5 Communication Timing通信时间

### 2.5.1 Timing Overview时间概览

P2 max

| **Value** | **Description**                                                                                                                                                                                                                                                                                                                                                                                         |
|-----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| P1        | Inter byte time in ECU response. 电子控制器响应字节间时间。                                                                                                                                                                                                                                                                                                                                             |
| P2        | Time between end of tester request and start of ECU response, or time between end of ECU response and start of next ECU response. 诊断仪请求结束至电子控制器响应之间的时间间隔，或者电子控制器两条响应间的时间间隔。                                                                                                                                                                                    |
| P3        | Time between end of ECU response and start of new tester request, or time between end of tester request and start of new tester request if ECU fails to respond. P3 shall be measured from the last byte in the latest response message from any ECU responding. 电子控制器响应结束至诊断仪请求时间间隔，或者诊断仪之间2次请求的时间间隔（电子控制器响应失败）。从电子控制器响应的最后1个字节开始计时。 |
| P4        | Inter byte time in tester request. 诊断仪请求字节间隔时间。                                                                                                                                                                                                                                                                                                                                             |

### 2.5.2 Timing Parameters时间参数

The SFB10 ECU supports only a fast initialization over the K-line. The ECU shall
support 8 bits, no parity, 1 start bit, and 1 stop bit. Please note, the system
will internally convert the 1ms resolution for Pmin.

宁波赛福电子控制器仅支持基于K线的快速初始化方式，通信设置为数据8位，无奇偶位，初始1位，停止1位，系统内部识别精度为1毫秒。

**Normal Timing Parameter常规时间参数**

| **Timing Parameter** | **Minimum Values(ms)最小值（毫秒）** | **Maximum Values(ms)最大值（毫秒）** |                |             |                 |                |
|----------------------|--------------------------------------|--------------------------------------|----------------|-------------|-----------------|----------------|
|                      | **Lower limit**                      | **Default**                          | **Resolution** | **Default** | **Upper limit** | **Resolution** |
| P1                   | 0                                    | 0                                    | ---            | 20          | 20              | ---            |
| P2                   | 0                                    | 25                                   | 0.5            | 50          | 5000            | 25             |
| P3                   | 0                                    | 55                                   | 0.5            | 5000        | \$FF            | 250            |
| P4                   | 0                                    | 5                                    | 0.5            | 20          | 20              | ---            |

**Parameters参数**

| **Parameter**                                                         | **Name** | **Value**  |       |
|-----------------------------------------------------------------------|----------|------------|-------|
| Communication speed (Baud rate)通信速率（波特率）                     | BR       | 10400±1.7% |       |
| ECU Address电子控制器地址                                             | ADDRECU  | 0x28       |       |
| Tester Address诊断仪地址                                              | ADDRT    | 0xf0       |       |
| Key Byte 1关键字1                                                     | KB1      | EAH        |       |
| Key Byte 2关键字2                                                     | KB2      | 8FH        |       |
|                                                                       |          | Min        | Max   |
| Idle Line before Wake up Pattern唤醒前空闲时间                        | Tidle    | 300ms      | --    |
| Time of WUP ground keying唤醒时间                                     | TiniL    | 24 ms      | 26 ms |
| Time between start of WUP and STC request唤醒开始和通信请求的时间间隔 | TWup     | 49 ms      | 51 ms |
| Inter-byte time for ECU response电子控制器间隔字节                    | P1       | 0ms        | 20ms  |
| Inter-message time ECU电子控制器响应时间                              | P2       | 25ms       | 50ms  |
| Inter-message time tester诊断仪请求间隔                               | P3       | 55ms       | 5s    |
| Inter-byte time tester诊断仪字节间隔                                  | P4       | 0ms        | 20ms  |

## 2.6 Communication Safety通信安全

### 2.6.1 Checksum / Length Byte校验和/长度字节

The following is checked constantly by the ECU during
communication电子控制器通信过程中会一直检测：

\-Format byte for non-plausible information不确定消息的格式字节

\-Target Address byte in Tester Request 测试人员请求中的目标地址字节

\-Length byte for non-plausible information 不确定消息的长度字节

\- Checksum error in the case of requests请求的校验和错误

\-Inter-byte timing of Tester request诊断仪请求的内部字节时间

\-Byte Framing / Overrun errors字节帧/溢出错误

If the ECU detects an error during these checks, no response is sent to the
tester. The ECU then waits again for a request of the tester.

一旦电子控制器检测到错误，诊断仪将接受不到任何响应，电子控制器等待新的请求。

### 2.6.2 Timing Control 时间控制

The communication is stopped by the ECU if the time P3max is exceeded. The ECU
stops communication and waits for a new Wake-Up-Pattern.

如果P3超时，电子控制器会切断通信，等待新的唤醒信号。

### 2.6.3 Communication Setup建立通信

If the ECU detects an error or a "Start Communication" request not destined for
it on communication set up, it stops communication. The tester can start a retry
(starting with the Wake-Up-Pattern).

如果电子控制器检测到错误或者未收到“开始通信”请求，诊断仪应重复发送“唤醒”操作。

## 2.7 Conditions and Behavior of the ECU电子控制器的条件和动作

### 2.7.1 Exit Conditions退出条件

The ECU will terminate an active diagnostic session in the following
cases遇有以下情形电子控制器退出诊断：

\- IGN is switched off. 点火关。

\- The speed limit is reached. Note that this speed limit can be disabled by
using the Input Output Control by Local Identifier
service.超速，限速功能可以在根据本地身份标识的输入输出控制服务中关闭。

\- A Stop Communication request is received.收到停止通信请求。

\-The ECU does not receive any tester message for more than X seconds (P3max
timeout). 在P3时间内，ECU没有收到诊断仪发出的消息（P3超时）。

\-A diagnostic session is started using the Start Diagnostic Session service.
When a diagnostic session is aborted, all diagnostic actuations (e.g. lamps,
valves) will be switched
off.诊断层由“开始诊断层”服务指令开始，当诊断中断，所有诊断动作停止。

### 2.7.2 Speed Limit速度限制

The ECU monitors a speed limit during the entire diagnosis communication: 10
km/h in all modes (0km/h for upload/ download mode).

在诊断过程中，电子控制器一直监控车速：所有模式不超过10公里每小时（下载和上传模式为0公里每小时）

# 3 Services of Diagnostic Session诊断服务

## 3.1 Overview of Supported Services支持的服务总览

**Positive Response肯定应答**

| **Tester** | **ECU**                                                                                             |                      |                   |                                              |
|------------|-----------------------------------------------------------------------------------------------------|----------------------|-------------------|----------------------------------------------|
| **Code**   | **Request**                                                                                         | **Local Identifier** | **Response Code** | **Positive Response**                        |
| 10H        | Start Diagnostic Session 开始诊断                                                                   |                      | 50H               | Start Diagnostic Session                     |
| 14H        | Clear Diagnostic Information 清除诊断信息 Clear All Group of DTC 清除所有诊断故障代码               |                      | 54H               | Clear Diagnostic Information                 |
| 17H        | Read Status of DTC 读诊断故障代码的状态                                                             |                      | 57H               | Read Status of DTC                           |
| 18H        | Read Diagnostic Information by Status 根据状态读取诊断信息 Read All Group of DTC 读所有诊断故障代码 |                      | 58H               | Read Diagnostic Information by Status        |
| 1AH        | Read ECU Identifier 读取ECU标识                                                                     |                      | 5AH               | Read ECU Identifier                          |
| 21H        | Read Data by Local Identifier 根据本地身份标识读取数据                                              |                      | 61H               | Read Data by Local Identifier                |
| 30H        | IO Control by Local Identifier 本地标识符寻址的输入输出控制                                         |                      | 70H               | IO Control by Local Identifier               |
| 31H        | Start Routine by Local Identifier 根据本地身份标识启动例程                                          |                      | 71H               | Start Routine by Local Identifier            |
| 32H        | Stop Routine By Local Identifier 根据本地身份标识停止例程                                           |                      | 72H               | Stop Routine By Local Identifier             |
| 33H        | Request Routine Results By Local Identifier 根据本地身份标识请求例程结果                            |                      | 73H               | Request Routine Results By Local Identifier  |
| 3BH        | Write Data by Local Identifier 根据本地身份标识写数据                                               |                      | 7BH               | Write Data by Local Identifier               |
| 3EH        | Tester Present 诊断仪在线                                                                           |                      | 7EH               | Tester Present                               |
| 81H        | Start Communication 开始通信                                                                        |                      | C1H               | Start Communication                          |
| 82H        | Stop Communication 停止通信                                                                         |                      | C2H               | Stop Communication                           |
| 20H        | Stop Diagnostic Session 停止诊断                                                                    |                      | 60H               | Stop Diagnostic Session                      |
| 83H        | Access timing parameters 访问时间参数                                                               |                      | C3                | Access timing parameters                     |
| 11H        | ECU Reset ECU复位                                                                                   |                      | 51H               | ECU Reset                                    |
| 27H        | Security Access 安全访问                                                                            |                      | 67H               | Security Access                              |

**Negative Response**否定应答

| Byte | Description                                                                                                                                                                                                                                                                                                                                    | Value                                    |
|------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------|
| 1    | Reply Byte应答字节                                                                                                                                                                                                                                                                                                                             | 7FH                                      |
| 2    | Service Identifier from Tester 诊断仪请求服务身份标识                                                                                                                                                                                                                                                                                          | XXH                                      |
| 3    | Negative Response Code否定应答代码： Request not supported请求不支持 Request invalid请求无效 Busy request忙-重复请求 Conditions not correct条件不满足 Routine not complete程序未完成 Request sequence error请求顺序错误 Request out of range请求超越权限 Security access Denied安全访问拒绝 Invalid key无效的按键输入 Response pending响应挂起 |  11H 12H 21H 22H 23H 24H 31H 33H 35H 78H |

**11H Request not supported请求不支持**

If there is an invalid Service Code in the Tester Request, that means the
service is not implemented in the ECU.

诊断仪请求服务代码无效，即电子控制器中没有执行请求的服务代码。

**12H Request invalid请求无效**

The requested service is supported by the ECU, however the service has been
badly formulated by the tool (wrong parameters).

电子控制器支持该项请求，但是诊断仪发送的格式不对（或参数有错误）。

**21H Busy Request忙-重复请求**

The ECU has understood the request, but the previous request is still being
executed and its result might affect the response to the requested service. The
tester has to send the same request again until it gets a final response (a
positive one or a negative one with local identifier different from 21H).

电子控制器已识别请求，但之前的请求正在执行，其运行结果可能会影响当前请求的服务，诊断仪此时应继续发送请求直到电子控制器回复最终应答（肯定应答或者本地身份标识不为21H的否定应答）。

**22H Conditions not correct条件不满足**

The current operating conditions do not allow the execution of the request, like
read/write Flash unpermitted, speed limit, or the service is protected by
present session.

当前运行状况不满足执行请求的条件，如读写存储器不允许，速度限制，或者当前会话层服务受到保护。

**23H Routine not complete程序未完成**

Mainly for “start routine by local identifier”.

主要用于“根据本地身份标识开启例程”

**24H Request sequence error请求顺序错误**

The sequence of request is error. For example, seeding key before requiring seed
is error sequence.

请求顺序发生错误。例如，在请求种子之前发送钥匙是错误的顺序。

**31H Request out of range请求超越权限**

Parameters are out of range, like activation time overflow, similar with
“Request Invalid”.

参数超出范围，如激活时间溢出，类似“请求无效”。

**33H Security access Denied安全访问拒绝**

The current operation does not have access to safe access permissions and have
been refused to access.

当前操作没有获得安全访问权限，访问被拒绝。

**78H Response Pending应答挂起**

This negative response is used for the processing of long requests (multiple
responses), like write Flash in progress.

该否定应答用于处理长请求（多重响应），如正在写存储器。

## 3.2 Service Details服务详细内容

### 3.2.1 Start Diagnostic Session开始诊断会话

This service is used by the tester to select a specific diagnostic mode. To exit
current mode, the ECU needs to be ignition off.

该服务用于诊断仪选择一个特定的诊断模式，如退出当前模式，请将电子控制器熄火。

| **Tester Request诊断仪请求** |                                                                         |           |
|------------------------------|-------------------------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                                             | **Value** |
| 1                            | Service Identifier服务身份标识                                          | 10H       |
| 2                            | Diagnostic Mode诊断模式： Standard Mode标准模式 End of Line下线检测模式 |  81H 83H  |

| **ECU Positive Response电子控制器肯定应答** |                                                                         |           |
|---------------------------------------------|-------------------------------------------------------------------------|-----------|
| **Byte**                                    | **Content**                                                             | **Value** |
| 1                                           | Service Identifier 服务身份标识                                         | 50H       |
| 2                                           | Diagnostic Mode诊断模式： Standard Mode标准模式 End of Line下线检测模式 |  81H 83H  |

### 3.2.2 Clear Diagnostic Information清除诊断信息

The contents of the fault memory in the EEPROM of the ECU are deleted with the
"Clear Diagnostic Information" request. The tester must check whether the fault
memory has actually been deleted (by re-sending the "Read Diagnostic Trouble
Codes By Status" request).

电子控制器内的电擦除存储器中存储的故障代码可通过“清除诊断信息”命令来擦除，诊断仪在发送完“擦除”命令后，再发送“根据状态读取诊断故障代码”命令来检验故障代码是否被擦除。

| **Tester Request诊断仪请求** |                                                |           |
|------------------------------|------------------------------------------------|-----------|
| **Byte**                     | **Content**                                    | **Value** |
| 1                            | Service Identifier 服务身份标识                | 14H       |
| 2                            | Group of DTC High Byte故障诊断码组（高位字节） | FFH       |
| 3                            | Group of DTC Low Byte故障诊断码组（低位字节）  | 00H       |

| **ECU Positive Response电子控制器肯定应答** |                                              |           |
|---------------------------------------------|----------------------------------------------|-----------|
| **Byte**                                    | **Content**                                  | **Value** |
| 1                                           | Service Identifier 服务身份标识              | 54H       |
| 2                                           | Group of DTC High Byte故障诊断码组（高字节） | FFH       |
| 3                                           | Group of DTC Low Byte故障诊断码组（低字节）  | 00H       |

If the writing of the EEPROM needs more than P2max, the ECU will send a negative
response 21H (Busy Repeat Request) until the reading has been finished.

如果写存储器所需时间超过P2最大值，电子控制器会回复“忙-重复请求”的否定应答直到读操作完成。

### 3.2.3 Read Status of Diagnostic Trouble Code读取诊断故障代码状态

This service sends to the tester the environment data corresponding to a
particular DTC.

此服务会把诊断故障代码发生时的环境数据返回给诊断仪。

| **Tester Request诊断仪请求** |                                                |             |
|------------------------------|------------------------------------------------|-------------|
| **Byte**                     | **Content**                                    | **Value**   |
| 1                            | Service Identifier 服务身份标识                | 17H         |
| 2                            | Request by DTC High Byte诊断故障代码高字节请求 | XXH ( FFH)  |
| 3                            | Request by DTC Low Byte诊断故障代码低字节请求  | XXH ( 00H ) |

If request all groups of DTC, DTC high byte is defined by “FFH”, DTC low byte is
defined by “00H”.

如果请求所有的DTC，那么DTC高字节设为FFH，低字节设为00H。

| **ECU Positive Response电子控制器肯定应答** |                                 |           |
|---------------------------------------------|---------------------------------|-----------|
| **Byte**                                    | **Content**                     | **Value** |
| 1                                           | Service Identifier服务身份标识  | 57H       |
| 2                                           | Number of DTC诊断故障代码数量   | XXH       |
| 3                                           | DTC High Byte诊断故障代码高字节 | XXH       |
| 4                                           | DTC Low Byte诊断故障代码低字节  | XXH       |
| 5                                           | Status of DTC诊断故障代码状态   | XXH       |

**Definition of the Diagnostic Trouble Codes诊断故障代码定义：**

The fault path is indicated by the stored "Diagnostic Trouble Code" (DTC). When
saving a new fault, a check is first conducted in order to establish whether the
same DTC has already been saved at any point in the overall fault memory. If
this is the case, the DTC is entered at the same position. Otherwise, it is
entered at the next free position in the fault memory. If all six fault memories
are occupied, the least recent fault is overwritten by the new DTC.

存储的“诊断故障代码”指示错误存储路径，当要存储新故障时，会先检查同样的故障代码是否已存储过。如果已存储，该故障代码会存储在相同的位置；如果没有存储记录，此故障代码会在后续存储单元中存储，如果6个存储单元已存满，新故障代码将覆盖最先存储的故障代码。

**Definition of Status Of DTC故障代码状态定义：**

Bit 7 - 1: free未使用

Bit 0 = 1: the fault is present当前故障

Bit 0 = 0: the fault is absent but memorized历史故障

**Definition of the Number of Fault Detections故障识别数量定义：**

At the first detection, the number will be set to 01. And it will incremented
each time the fault is actualized into the EEPROM. If the reading of the EEPROM
is needing more than P2max, the ECU will send a negative response 21H (Busy
Repeat Request) until the reading has been finished.

第一次侦测到错误时，故障代码数量为1，以后遇有新故障代码时该数字逐次增加。如果读取存储器时间超过P2最大值，电子控制器会回复“忙-重复请求”否定应答直至读取完成。

### 3.2.4 Read Diagnostic Trouble Code By Status根据状态来读取故障代码

This service sends to the tester the fault memory (present or absent). The
entire fault memory of the ECU can accommodate up to six different errors
simultaneously.

这个服务将存储的故障发送给测试仪(当前或历史)。ECU整个故障内存可以同时存储6个不同的故障。

| **Tester Request诊断仪请求** |                                                        |           |
|------------------------------|--------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                            | **Value** |
| 1                            | Service Identifier服务身份标识                         | 18H       |
| 2                            | Status of DTC诊断故障代码状态： Present当前 Stored存储 |  01H 00H  |
| 3                            | Request by DTC High Byte诊断故障代码高字节请求         | FFH       |
| 4                            | Request by DTC Low Byte诊断故障代码高字节请求          | 00H       |

| **ECU Positive Response电子控制器肯定应答** |                                 |           |
|---------------------------------------------|---------------------------------|-----------|
| **Byte**                                    | **Content**                     | **Value** |
| 1                                           | Service Identifier 服务身份标识 | 58H       |
| 2                                           | Number of DTC诊断故障代码数量   | XXH       |
| 3                                           | DTC High Byte诊断故障代码高字节 | XXH       |
| 4                                           | DTC Low Byte诊断故障代码低字节  | XXH       |
| 5                                           | Status of DTC诊断故障代码状态   | XXH       |

If the reading of the EEPROM is needing more than P2Max, the ECU will send a
negative response 21H (Busy Repeat Request) until the reading has been finished.

如果读取存储器时间超过P2最大值，电子控制器会回复“忙-重复请求”负面响应直至读取完成。

### 3.2.5 Read ECU Identification读取电子控制器身份标识

ECU Identification allows the tester to identify it with precision.

诊断仪通过此服务可准确识别电子控制器型号。

| **Tester Request诊断仪请求** |                                                                                                                  |              |
|------------------------------|------------------------------------------------------------------------------------------------------------------|--------------|
| Byte                         | Content                                                                                                          | Value        |
| 1                            | Service Identifier服务身份标识                                                                                   | 1AH          |
| 2                            | Local Identifier本地身份标识： Customer Part Number客户零件号 SFB Part Number宁波赛福零件号 Project Name项目名称 |  91H 92H 9AH |

| ECU Positive Response**电子控制器肯定应答** |                                |           |
|---------------------------------------------|--------------------------------|-----------|
| Byte                                        | Content                        | Value     |
| 1                                           | Service Identifier服务身份标识 | 5AH       |
| 2                                           | Local Identifier本地身份标识   | XXH       |
| 3 to 15                                     | Data数据                       | 13 ASCII  |

If the reading of the EEPROM is needing more than P2max, the ECU will send a
negative response 21H (Busy Repeat Request) until the reading has been finished.

如果读取存储器时间超过P2最大值，电子控制器会回复“忙-重复请求”否定应答直至读取完成。

### 3.2.6 Read Data By Local Identifier根据本地身份标识读取数据

System information (wheel speeds, status information) is transferred to the
tester with the service "Read Data By Local Identifier".

通过此服务诊断仪可以获取系统信息（状态信息等）。

| **Tester Request诊断仪请求** |                                                                                                      |           |
|------------------------------|------------------------------------------------------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                                                                          | **Value** |
| 1                            | Service Identifier服务身份标识                                                                       | 21H       |
| 2                            | Local Identifier本地身份标识： Hydraulic Filling Indicator液压加注标志 Read EOL Flag读取下线检测标志 |  01H 06H  |

| **ECU Positive Response电子控制器肯定应答** |                                |           |
|---------------------------------------------|--------------------------------|-----------|
| **Byte**                                    | **Content**                    | **Value** |
| 1                                           | Service Identifier服务身份标识 | 61H       |
| 2                                           | Local Identifier本地身份标识   | XXH       |
| 3                                           | Status状态                     | XXH       |

**Status状态：**

**Hydraulic Filling Indicator液压加注标志**

55H-\> Filling Successfully加注成功

AAH-\>Filling Not Successfully加注失败

FFH-\>Delivery State交付状态（初始状态）

**Read EOL Flag读取下线检测标志**

55H-\>EOL CONFIG DONE下线检测完成

AAH-\> EOL CONFIG NOT DONE下线检测未完成

FFH-\>Delivery State交付状态（初始状态）

| **Tester Request诊断仪请求** |                                                        |           |
|------------------------------|--------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                            | **Value** |
| 1                            | Service Identifier服务身份标识                         | 21H       |
| 2                            | Local Identifier{digital signal}本地身份标识(数字信号) | 04H       |

| **ECU Positive Response电子控制器肯定应答** |                                                        |                                                  |            |
|---------------------------------------------|--------------------------------------------------------|--------------------------------------------------|------------|
| **Byte**                                    | **Content**                                            | **Value**                                        |            |
| 1                                           | Service Identifier服务身份标识                         | 61H                                              |            |
| 2                                           | Local Identifier{digital signal}本地身份标识(数字信号) | 04H                                              |            |
| 3                                           | Bit\#7                                                 | State of Front normal open valve前轮常开阀状态   | 1=ON,0=OFF |
|                                             | Bit\#6                                                 | State of Front normal closed valve前轮常闭阀状态 | 1=ON,0=OFF |
|                                             | Bit\#5                                                 | State of Rear normal open valve后轮常开阀状态    | 1=ON,0=OFF |
|                                             | Bit\#4                                                 | State of Rear normal closed valve后轮常闭阀状态  | 1=ON,0=OFF |
|                                             | Bit\#3                                                 | reserved                                         | reserved   |
|                                             | Bit\#2                                                 | reserved                                         | reserved   |
|                                             | Bit\#1                                                 | reserved                                         | reserved   |
|                                             | Bit\#0                                                 | reserved                                         | reserved   |
| 4                                           | Bit\#7                                                 | State of motor relay电机继电器状态               | 1=ON,0=OFF |
|                                             | Bit\#6                                                 | State of coils relay阀继电器状态                 | 1=ON,0=OFF |
|                                             | Bit\#5                                                 | State of front brake switch前刹车开关            | 1=ON,0=OFF |
|                                             | Bit\#4                                                 | State of rear brake switch后刹车开关             | 1=ON,0=OFF |
|                                             | Bit\#3                                                 | State of ABS off switch ABS状态切换开关          | 1=ON,0=OFF |
|                                             | Bit\#2                                                 | reserved                                         | reserved   |
|                                             | Bit\#1                                                 | reserved                                         | reserved   |
|                                             | Bit\#0                                                 | reserved                                         | reserved   |
| 5                                           | reserved                                               | reserved                                         |            |
| 6                                           | reserved                                               | reserved                                         |            |

### 3.2.7 Input Output Control By Local Identifier根据本地身份标识进行输入输出控制

This service supports several different local identifiers that use different
request and response definitions. The following common request format is
used该服务支持多个不同身份标识，不同请求对应不同响应；一般常用格式定义如下：

| **Tester to ECU诊断仪至ECU：IO Control by Local Identifier Request根据本地身份标识进行输入输出控制请求** |                                                                                                                                        |                  |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------------|
| **Byte**                                                                                                 | **Content**                                                                                                                            | **Value**        |
| 1                                                                                                        | Input output control by Local identifier request service identifier 根据本地身份标识进行输入输出控制请求服务身份标识                   | 30H              |
| 2                                                                                                        | Input output local identifier输入输出本地身份标识                                                                                      | XXH              |
| 3 to m                                                                                                   | Control status控制状态： IO Control Parameter输入输出控制参数 Control State1控制状态1 Control State2控制状态2 Control State m控制状态m |  XXH XXH XXH XXH |

| **ECU to Tester ECU至诊断仪：IO Control by Local Identifier Positive Response根据本地身份标识进行输入输出控制肯定应答** |                                                                                                                                        |                  |
|-------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|------------------|
| **Byte**                                                                                                                | **Content**                                                                                                                            | **Value**        |
| 1                                                                                                                       | Input output control by local identifier positive response service identifier根据本地身份标识进行输入输出控制肯定应答服务身份标识      | 70H              |
| 2                                                                                                                       | Input output local identifier输入输出本地身份标识                                                                                      | XXH              |
| 3 to m                                                                                                                  | Control status控制状态： IO Control Parameter输入输出控制参数 Control State1控制状态1 Control State2控制状态2 Control State m控制状态m |  XXH XXH XXH XXH |

### 3.2.8 Start Routine By Local Identifier根据本地身份标识开始例程

Start routine by local identifier request actuator
diagnosis.根据本地身份标识开始例程的诊断。

| **Tester to ECU诊断仪至ECU：Start Routine By Local Identifier Request根据本地身份标识开始运行例程请求** |                                          |           |
|---------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                                | **Content**                              | **Value** |
| 1                                                                                                       | Service Identifier 服务身份标识          | 31H       |
| 2                                                                                                       | Routine Local Identifier例程本地身份标识 | XXH       |
| 3                                                                                                       | Routine Entry Status 1例程进入状态1      | XXH       |
| …                                                                                                       | …                                        | …         |
| m                                                                                                       | Routine Entry Status m例程进入状态m      | XXH       |

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                          |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                              | **Value** |
| 1                                                                                                                  | Service Code服务代码                     | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识 | XXH       |
| 3                                                                                                                  | Routine Entry Status 1例程进入状态1      | XXH       |
| …                                                                                                                  | …                                        | …         |
| m                                                                                                                  | Routine Entry Status m例程进入状态m      | XXH       |

The number and content of the optional parameter bytes depends on the started
function.

可选参数的数量和内容字节数由选择的服务确定。

**Remark备注**

If the tester is trying to start a new control while a previous action is still
being executed, the ECU has to respond with a positive response (failure).

如果当前有服务正在执行，诊断仪试图发送新请求，电子控制器会回复肯定应答（失败）。

**List of Routine Local Identifiers例程本地身份标识列表**

| **Value** | **Signal group**                                                   |
|-----------|--------------------------------------------------------------------|
| \$12      | Test of the wheel speed sensors.轮速传感器测试                     |
| \$01      | Pump电机泵                                                         |
| \$02      | NO valve F前轮常开电磁阀                                           |
| \$03      | NC valve F前轮常闭电磁阀                                           |
| \$04      | NO valve R后轮常开电磁阀                                           |
| \$05      | NC valve R后轮常闭电磁阀                                           |
| \$06      | Warning light 报警灯                                               |
| \$1E      | Speed limit disable (for Vveh≥ 10km/h)（车速≥ 10km/h）关闭车速限制 |
| \$D0      | Delayed Actuator Control延时执行器控制                             |
| \$D1      | Periodic Actuator Control间隔执行器控制                            |
| \$D5      | Actuator Test执行器测试                                            |
| \$D6      | Dynamic Test动态测试                                               |

#### 3.2.8.1 Test of the Wheel Speed Sensors轮速传感器测试

| **Tester to ECU诊断仪至ECU： Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                          |           |
|------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                             | **Content**                              | **Value** |
| 1                                                                                                    | Service Identifier 服务身份标识          | 31H       |
| 2                                                                                                    | Routine Local Identifier例程本地身份标识 | 12H       |
| 3                                                                                                    | Duration持续时间1 bit = 100ms            | XXH       |

The maximum duration of this test is equal to 25,5s (= 255 \* 0.1s). If the
executing time is exceeding P2max, the ECU will send a negative response 21H
(Busy Repeat Request) until the control has been finished.

持续时间最大值为25.5秒（=255\*0.1秒），如果程序执行超过P2最大值，电子控制器会回复“忙-重复请求”应答直至控制完成。

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                          |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                              | **Value** |
| 1                                                                                                                  | Service Code服务代码                     | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识 | 12H       |

#### 3.2.8.2 Single Output Control单独输出控制

The local identifiers for single output control can be used to drive one single
actuator for a default time or permanently. They are also used to change
internal security settings.

单独输出控制的本地身份标识用以驱动单个执行器执行一段默认时间或永久执行，也用于更改内部安全模块设置值。

| **Tester to ECU诊断仪至ECU：Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                                                       |             |
|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|-------------|
| **Byte**                                                                                            | **Content**                                                                                           | **Value**   |
| 1                                                                                                   | Service Identifier 服务身份标识                                                                       | 31H         |
| 2                                                                                                   | Routine Local Identifier例程本地身份标识                                                              | XXH         |
| 3                                                                                                   | Routine Control Parameter例程控制参数 Start temporary control临时控制 Start permanent control永久控制 | XXH 00H 20H |

**Supported Local Identifiers for Single Output Control(Start Routine By Local
Identifier)单独输出控制支持的本地身份标识（开始例程本地身份标识）**

| **ID** | **Actuator执行器件**                                                  | **Available in temporary control** **临时控制模式** | **Available in permanent control** **永久控制模式** |
|--------|-----------------------------------------------------------------------|-----------------------------------------------------|-----------------------------------------------------|
| \$01   | Pump泵电机                                                            | YES                                                 |                                                     |
| \$02   | NO valve F前轮常开电磁阀                                              | YES                                                 |                                                     |
| \$03   | NC valve F前轮常闭电磁阀                                              | YES                                                 |                                                     |
| \$04   | NO valve R后轮常开电磁阀                                              | YES                                                 |                                                     |
| \$05   | NC valve R后轮常闭电磁阀                                              | YES                                                 |                                                     |
| \$06   | Warning light 报警灯                                                  | YES                                                 |                                                     |
| \$07   | unused                                                                |                                                     |                                                     |
| \$08   | unused                                                                |                                                     |                                                     |
| \$09   | unused                                                                |                                                     |                                                     |
| \$1E   | Speed limit disable(for Vveh\>=10km/h) 关闭“车速超过10公里每小时限制” |                                                     | YES                                                 |

**Supported commands (Routine Control Parameter)支持的命令（例程控制参数）**

Two ways of control can be distinguished能识别的2种控制模式：

\- Temporary临时控制：the output is on during 2s持续2秒钟

\- Permanent永久控制：the output is on and could only be stopped by sending a
request of stop routine永久执行，直至发送停止例程命令。

**Response应答**

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                          |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                              | **Value** |
| 1                                                                                                                  | Service Code服务代码                     | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识 | XXH       |

**Remarks备注：**

\- **Local Identifiers \$1E should be used with care, these Local Identifiers
will disable parts of the safety software.** Therefore, the ECU may be damaged
or the vehicle may not be safe to drive (e.g. if the speed limit during
diagnostics is disabled and then the valves are activated while driving the
car).

本地身份标识0x1E需谨慎使用，这些标识将使部分安全软件禁止使能，ECU会因此受到损坏，车辆将不能安全行驶。（例如：如果诊断过载中速度限制功能禁止使能，阀将在车辆行驶过程中被激活。）

\- **If the valves are activated for too long the ECU can be damaged**. The
maximum activation time of the valves must not exceed 30 seconds at an ambient
temperature of 30°C. Using the ‘Single output control’ service repeatedly can
damage the valves or pump. Please keep this information in mind when using this
service.

如果阀动作时间过长，ECU将受损。当环境温度为30℃时，阀的最大激活时间不能超过30秒，重复使用单独输出控制会损坏阀和泵。在使用服务时，请牢记上述内容。

**- For temporary control, the executing time is exceeding P2max.** During
actuation time, the ECU will send a negative response 21H (Busy Repeat Request)
until the control has been finished.

临时控制模式下，如果执行时间超过P2最大值，在执行时，电子控制器会回复21H“忙-重复请求”否定应答直至控制完成。

#### 3.2.8.3 Delayed Actuator Control延时执行器控制

This service allows to control multiple drivers/electrovalves simultaneously.
For each component to be controlled, two states are defined: state 1 and state
2\. As soon as the first request has been received, the actuators are configured
in their states 1 (defined by bytes 4 and 5 of the request). After the
activation time, the actuators are placed in their states 2 (defined by bytes 7
and 8).

此服务允许同时控制多个电磁阀和电机，每个执行器件可以设定2种控制状态，“状态1”和“状态2”。一旦初始请求被收到，执行器被配置为“状态1”（字节4和5定义），经过“激活时间”后恢复至“状态2”（字节7和8定义）。

| **Tester to ECU诊断仪至ECU： Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                               |           |
|------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------|-----------|
| **Byte**                                                                                             | **Content**                                                                   | **Value** |
| 1                                                                                                    | Service Identifier服务身份标识                                                | 31H       |
| 2                                                                                                    | Routine Local Identifier例程本地身份标识                                      | D0H       |
| 3                                                                                                    | Routine Control Parameter例程控制参数： Start the delayed control开始延时控制 |  00H      |
| 4                                                                                                    | Electrovalves to be commanded (state 1)电磁阀命令（状态1）                    | XXH       |
| 5                                                                                                    | Drivers to be commanded (state 1)电机命令（状态1）                            | XXH       |
| 6                                                                                                    | Activation time激活时间                                                       | XXH       |
| 7                                                                                                    | Electrovalves to be commanded (state 2)电磁阀命令（状态2）                    | XXH       |
| 8                                                                                                    | Drivers to be commanded (state 2)电机命令（状态2）                            | XXH       |

**Activation Time 激活时间**

Concerning the activation time, one bit corresponds to 20ms. That means that the
possible range for activation time is between 20 ms and 5,10s. If the executing
time is exceeding P2max, the ECU will send a negative response 21H (Busy Repeat
Request) until the control has been finished.

激活时间设定，1位表示20毫秒，有效时间范围是20毫秒到5.1秒之间；如果执行时间超过P2最大值，电子控制器会回复21H“忙-重复请求”负面响应直至控制完成。

**Bit Field for Electrovalves电磁阀位域**

| **Bit** | **Electrovalve**                    |
|---------|-------------------------------------|
| Bit 0   | NO electrovalve Front前轮常开电磁阀 |
| Bit 1   | NC electrovalve Front前轮常闭电磁阀 |
| Bit 2   | NO electrovalve Rear后轮常开电磁阀  |
| Bit 3   | NC electrovalve Rear后轮常闭电磁阀  |
| Bit 4   | unused未使用                        |
| Bit 5   | unused未使用                        |
| Bit 6   | unused未使用                        |
| Bit 7   | unused未使用                        |

For each selected electrovalve, the corresponding bit has to be set to 1 to
switch the valve on. Using a bit value of 0 switches the valve off. Several
electrovalves can be controlled simultaneously.

要控制电磁阀，必须将相应的位置为1，用以给电磁阀供电；置为0则该电磁阀失去电；多个电磁阀可以同时控制。

**Bit Field for Drivers驱动器位域**

| **Bit** | **Electrovalve** |
|---------|------------------|
| Bit 0   | unused未使用     |
| Bit 1   | unused未使用     |
| Bit 2   | unused未使用     |
| Bit 3   | unused未使用     |
| Bit 4   | unused未使用     |
| Bit 5   | unused未使用     |
| Bit 6   | pump motor电机泵 |
| Bit 7   | unused未使用     |

For each selected driver, the corresponding bit has to be set to 1 to switch the
driver on. Using a bit value of 0 switches the driver off. Several drivers can
be controlled simultaneously.

要控制驱动器，必须将相应的位置1，置为0则关断驱动器，可以同时控制多个驱动器。

**Response应答**

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                          |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                              | **Value** |
| 1                                                                                                                  | Service Code服务代码                     | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识 | D0H       |

**Remarks备注**

A control that has been started by a delay actuator control request, can be
stopped using the “Stop Routine By Local Identifier” function.

由延时驱动控制请求开始的控制，能够运用“根据本地身份标识停止例程”中断；

At each end of this service, a new control has to be sent to place the
drivers/electrovalves in their OFF states. To achieve this, the tester has to
send the following request: 30 D0 00 00 00 00 00 00.

每次执行完后诊断仪应发送“30 D0 00 00 00 00 00 00”恢复电磁阀和电机的初始状态。

#### 3.2.8.4 Periodic Actuator Control间隔执行器控制

This service allows to fill in and to drain off the hydraulic bloc. The control
sequences are programmed in the ECU.

此服务用于加注液压模块，抽空蓄能器单元，控制程序已固化进电子控制器内。

**Vacuum Filling抽真空加注**

| **Tester to ECU诊断仪至ECU：Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                                                 |              |
|-----------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------|--------------|
| **Byte**                                                                                            | **Content**                                                                                     | **Value**    |
| 1                                                                                                   | Service Identifier 服务身份标识                                                                 | 31H          |
| 2                                                                                                   | Routine Local Identifier例程本地身份标识                                                        | D1H          |
| 3                                                                                                   | Routine Control Parameter例程控制参数： Start Control 开始控制                                  |  00H         |
| 4                                                                                                   | Type of the control控制类型： Vacuum Filling抽真空加注                                          |  00H         |
| 5                                                                                                   | Duration T (for Evac& Fill) 抽真空加注时间 1 bit = 1s，Min: 1s，Max: 150s                       | XXH          |
| 6                                                                                                   | Chanel selection通道选择： Front Axle前轴 Rear Axle后轴 Both Front Axle and Rear Axle前后轴同时 |  01H 02H 03H |

For the specified time range, T has to be between 1 and 150s. If T exceeds this
limit, the ECU uses the maximum allowed value.

该段时间范围为1到150秒，如果时间设置超出范围，电子控制器会使用最大值。

**Repair Bleeding 人工排气**

The repair bleeding is split in 4 different phases. In phase 2 and 4 there is a
loop counter, SFB recommends a number of 5 loops for a good bleeding result.

人工排气过程分为4个阶段，阶段2和阶段4需重复执行，宁波赛福建议执行5次，这样有助于充分排气。

| **Tester to ECU诊断仪至ECU： Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                                                       |                  |
|------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------|------------------|
| **Byte**                                                                                             | **Content**                                                                                           | **Value**        |
| 1                                                                                                    | Service Identifier 服务身份标识                                                                       | 31H              |
| 2                                                                                                    | Routine Local Identifier例程本地身份标识                                                              | D1H              |
| 3                                                                                                    | Routine Control Parameter例程控制参数： Start periodic control开始控制                                |  00H             |
| 4                                                                                                    | Repair Bleed Phase Identifier人工排气阶段身份标识 Phase 1阶段1 Phase 2阶段2 Phase 3阶段3 Phase 4阶段4 |  01H 02H 03H 04H |
| 5                                                                                                    | Number of loops循环次数 1 bit = 1 loop                                                                | XXH              |
| 6                                                                                                    | Reserved保留                                                                                          | reserved         |

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                                                                    |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                                                                        | **Value** |
| 1                                                                                                                  | Service Code服务代码                                                               | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识： Periodic actuator control间隔执行器控制 |  D1H      |

#### 3.2.8.5 Actuator Test执行器控制

| **Tester to ECU诊断仪至ECU： Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                           |           |
|------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------|-----------|
| **Byte**                                                                                             | **Content**                                                               | **Value** |
| 1                                                                                                    | Service Identifier 服务身份标识                                           | 31H       |
| 2                                                                                                    | Routine Local Identifier例程本地身份标识                                  | D5H       |
| 3                                                                                                    | Routine Control Parameter例程控制参数： Start control开始控制             |  00H      |
| 4                                                                                                    | Result Selection结果选择： Without result 不返回结果 With result 返回结果 |  00H FFH  |
| 5                                                                                                    | 1. Actuation Value (HB)执行器值（高位）                                   | XXH       |
| 6                                                                                                    | 1. Actuation Value (LB)执行器值（低位）                                   | XXH       |
| 7                                                                                                    | 1. Actuator Number (HB)执行器号（高位）                                   | XXH       |
| 8                                                                                                    | 1. Actuator Number (LB)执行器号（低位）                                   | XXH       |
| 9                                                                                                    | 2. Actuation Value (HB)执行器值（高位）                                   | XXH       |
| 10                                                                                                   | 2. Actuation Value (LB)执行器值（低位）                                   | XXH       |
| 11                                                                                                   | 2. Actuator Number (HB)执行器号（高位）                                   | XXH       |
| 12                                                                                                   | 2. Actuator Number (LB)执行器号（低位）                                   | XXH       |
| 13                                                                                                   | Actuation Time (HB)执行时间（高位）                                       | XXH       |
| 14                                                                                                   | Actuation Time (LB)执行时间（低位）                                       | XXH       |
| 15                                                                                                   | 3. Actuation Value (HB)执行器值（高位）                                   | XXH       |
| 16                                                                                                   | 3. Actuation Value (LB)执行器值（低位）                                   | XXH       |
| 17                                                                                                   | 3. Actuator Number (HB)执行器号（高位）                                   | XXH       |
| 18                                                                                                   | 3. Actuator Number (LB)执行器号（低位）                                   | XXH       |
| 19                                                                                                   | 4. Actuation Value (HB)执行器值（高位）                                   | XXH       |
| 20                                                                                                   | 4. Actuation Value (LB)执行器值（低位）                                   | XXH       |
| 21                                                                                                   | 4. Actuator Number (HB)执行器号（高位）                                   | XXH       |
| 22                                                                                                   | 4. Actuator Number (LB)执行器号（低位）                                   | XXH       |

**Actuation Time执行时间**

This parameter specifies the time between the first and second actuation.

该参数表示第一次和第二次执行之间时间

Resolution分辨率：1 bit = 10ms

A**ctuation Value执行器值**

This parameter specifies the amount of actuation.

此参数表示执行器参数值

Resolution分辨率：1 bit = 1%

**Actuator Numbers执行器号**

| **Actuator Numbers for Actuator and Dynamic test执行器和动态测试时使用的执行器号** |        |
|------------------------------------------------------------------------------------|--------|
| Normal Open valve F前轮常开电磁阀                                                  | 00 30H |
| Normal Close valve F前轮常闭电磁阀                                                 | 00 32H |
| Normal Open valve R后轮常开电磁阀                                                  | 00 38H |
| Normal Close valve R后轮常闭电磁阀                                                 | 00 3AH |
| Pump motor relay泵电机继电器                                                       | 00 22H |

The actuator number high byte is generally 00H.

执行器号高字节一般为00H。

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                                                    |           |
|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                                                        | **Value** |
| 1                                                                                                                  | Service Code服务代码                                               | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识： Actuator test执行器测试 |  D5H      |

**Remarks备注**

\- The pump motor relay must not be actuated for times shorter than 20ms. Shorter
actuations could damage the motor relay due to very high current during the
starting phase of the motor.

电机泵继电器执行时间不应小于20毫秒，由于电机的启动电流很大，执行时间过短可能会损坏电机的继电器。

\- SFB strongly recommends only to use actuation values of 0% and 100%.

宁波赛福建议只使用0%或者100%占空比驱动。

#### 3.2.8.6 Dynamic Test动态测试

| **Tester to ECU诊断仪至ECU：Start Routine By Local Identifier Request根据本地身份标识开始例程请求** |                                                                |           |
|-----------------------------------------------------------------------------------------------------|----------------------------------------------------------------|-----------|
| **Byte**                                                                                            | **Content**                                                    | **Value** |
| 1                                                                                                   | Service Identifier 服务身份标识                                | 31H       |
| 2                                                                                                   | Routine Local Identifier例程本地身份标识                       | D6H       |
| 3                                                                                                   | Routine Control Parameter例程控制参数： Start control 开始控制 |  00H      |
| 4                                                                                                   | 1. Actuation Value (HB)执行器值（高位）                        | XXH       |
| 5                                                                                                   | 1. Actuation Value (LB)执行器值（低位）                        | XXH       |
| 6                                                                                                   | 1. Actuator Number (HB)执行器号（高位）                        | XXH       |
| 7                                                                                                   | 1. Actuator Number (LB)执行器号（低位）                        | XXH       |
| 8                                                                                                   | 2. Actuation Value (HB)执行器值（高位）                        | XXH       |
| 9                                                                                                   | 2. Actuation Value (LB)执行器值（低位）                        | XXH       |
| 10                                                                                                  | 2. Actuator Number (HB)执行器号（高位）                        | XXH       |
| 11                                                                                                  | 2. Actuator Number (LB)执行器号（低位）                        | XXH       |
| 12                                                                                                  | Actuation Time (HB)执行时间（高位）                            | XXH       |
| 13                                                                                                  | Actuation time (LB)执行时间（低位）                            | XXH       |
| 14                                                                                                  | 3. Actuation Value (HB)执行器值（高位）                        | XXH       |
| 15                                                                                                  | 3. Actuation Value (LB)执行器值（低位）                        | XXH       |
| 16                                                                                                  | 3. Actuator Number (HB)执行器号（高位）                        | XXH       |
| 17                                                                                                  | 3. Actuator Number (LB)执行器号（低位）                        | XXH       |
| 18                                                                                                  | 4. Actuation Value (HB)执行器值（高位）                        | XXH       |
| 19                                                                                                  | 4. Actuation Value (LB)执行器值（低位）                        | XXH       |
| 20                                                                                                  | 4. Actuator Number (HB)执行器号（高位）                        | XXH       |
| 21                                                                                                  | 4. Actuator Number (LB)执行器号（低位）                        | XXH       |
| 22                                                                                                  | Wait time(HB)等待时间（高位）                                  | XXH       |
| 23                                                                                                  | Wait time(LB)等待时间（低位）                                  | XXH       |

| **ECU to Tester ECU至诊断仪：Start Routine By Local Identifier Positive Response根据本地身份标识开始例程肯定应答** |                                                                  |           |
|--------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------|-----------|
| **Byte**                                                                                                           | **Content**                                                      | **Value** |
| 1                                                                                                                  | Service Code服务代码                                             | 71H       |
| 2                                                                                                                  | Routine Local Identifier例程本地身份标识： Dynamic test 动态测试 |  D6H      |

**Remarks 备注**

\- If the executing time is exceeding P2max, the ECU will send a negative
response 21H (BusyRepeatRequest) until the control has been finished.

如果程序执行超过P2最大值，电子控制器会回复“忙-重复请求”响应直至控制完成。

### 3.2.9 Stop Routine By Local Identifier根据本地身份标识停止例程

This Routine is used to stop and clear buffer value of “Start Routine By Local
Identifier”.

该服务用于停止并清除“根据本地身份例程”所执行的程序及其预留在内存中的结果。

| **Tester Request诊断仪请求** |                                                                                                                                                                                                                                                                                                                                                                                            |                                                  |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| **Byte**                     | **Content**                                                                                                                                                                                                                                                                                                                                                                                | **Value**                                        |
| 1                            | Service Identifier 服务身份标识                                                                                                                                                                                                                                                                                                                                                            | 32H                                              |
| 2                            | Local Identifier本地身份标识： WSS Test轮速传感器测试 Pump泵电机 NO valve F前轮常开电磁阀 NC valve F前轮常闭电磁阀 NO valve R后轮常开电磁阀 NC valve R后轮常闭电磁阀 Warning light 报警灯 Speed limit disable(for Vveh\>=10km/h)关闭“车速超过10公里每小时限制” Delayed Actuator Control延时执行器控制 Periodic Actuator Control间隔执行器控制 Actuator Test执行器测试 Dynamic Test动态测试 |  12H 01H 02H 03H 04H 05H 06H 1EH D0H D1H D5H D6H |

| **ECU Positive Response ECU肯定应答** |                                 |           |
|---------------------------------------|---------------------------------|-----------|
| **Byte**                              | **Content**                     | **Value** |
| 1                                     | Service Identifier 服务身份标识 | 72H       |
| 2                                     | Local Identifier本地身份标识    | XXH       |

### 3.2.10 Request Routine Results By Local Identifier根据本地身份标识请求例程结果

This Routine is used to stop and clear buffer value of “Start Routine By Local
Identifier”.

该服务用于请求所执行的程序及其预留在内存中的结果。

| **Tester Request诊断仪请求** |                                                                                                                                                                                                                                                                                                                                                                                            |                                                  |
|------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------|
| **Byte**                     | **Content**                                                                                                                                                                                                                                                                                                                                                                                | **Value**                                        |
| 1                            | Service Identifier 服务身份标识                                                                                                                                                                                                                                                                                                                                                            | 33H                                              |
| 2                            | Local Identifier本地身份标识： WSS Test轮速传感器测试 Pump泵电机 NO valve F前轮常开电磁阀 NC valve F前轮常闭电磁阀 NO valve R后轮常开电磁阀 NC valve R后轮常闭电磁阀 Warning light 报警灯 Speed limit disable(for Vveh\>=10km/h)关闭“车速超过10公里每小时限制” Delayed Actuator Control延时执行器控制 Periodic Actuator Control间隔执行器控制 Actuator Test执行器测试 Dynamic Test动态测试 |  12H 01H 02H 03H 04H 05H 06H 1EH D0H D1H D5H D6H |

#### 3.2.10.1 Test of the Wheel Speed Sensors轮速传感器测试

| **ECU to Tester ECU至诊断仪：Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                                                                  |           |
|----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------|-----------|
| **Byte**                                                                                                                         | **Content**                                                                                      | **Value** |
| 1                                                                                                                                | Service Code服务代码                                                                             | 73H       |
| 2                                                                                                                                | Routine Local Identifier程序本地身份标识                                                         | 12H       |
| 3                                                                                                                                | Status of the requested question请求问题状态： Failure失败 Test completed and OK测试完成结果正常 |  00H 02H  |
|  4 5                                                                                                                             | Maximum speed of the Front wheel 前轮最大速度： High高字节 Low低字节                             |  XXH XXH  |
|  6 7                                                                                                                             | Minimum speed of the Front wheel前轮最小速度： High高字节 Low低字节                              |  XXH XXH  |
|  8 9                                                                                                                             | Maximum speed of the Rear wheel后轮最大速度： High高字节 Low低字节                               |  XXH XXH  |
|  10 11                                                                                                                           | Minimum speed of the Rear wheel后轮最小速度： High高字节 Low低字节                               |  XXH XXH  |
| 12 13                                                                                                                            | unused unused                                                                                    | XXH XXH   |
| 14 15                                                                                                                            | unused unused                                                                                    | XXH XXH   |
| 16 17                                                                                                                            | unused unused                                                                                    | XXH XXH   |
| 18 19                                                                                                                            | unused unused                                                                                    | XXH XXH   |

**Remarks备注**

\- Bytes 4 to 11 are only sent if the response is “Test completed and OK”.

字节4到11，仅当应答为“测试完成且正常”时才发送。

\- Resolution for the wheel speed: 1 bit = 0.0078125m/s.

轮速分辨率：1位=0.0078125米每秒。

\- To be sufficient the test should be executed during at least one complete
wheel rotation.

为保证测试结果可靠，应确保测试时间内轮子转动超过1圈。

If the test fails (i.e. sensors is open circuit), then the minimum and maximum
wheel speeds for the faulty wheel(s) is set to FFFFH.

如果测试失败（例如，传感器开路），错误轮子的轮速的最大和最小值均为0xFFFF。

#### 3.2.10.2 Single Output Control单独输出控制

| **ECU to Tester ECU至诊断仪：Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                    |           |
|----------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|-----------|
| **Byte**                                                                                                                         | **Content**                                        | **Value** |
| 1                                                                                                                                | Service Code服务代码                               | 73H       |
| 2                                                                                                                                | Routine Local Identifier例程本地身份标识           | XXH       |
| 3                                                                                                                                | Status状态： Failure失败 Control completed控制完成 |  00H  02H |

#### 3.2.10.3 Delayed Actuator Control延时执行器控制

| **ECU to Tester ECU至诊断仪：Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                    |            |
|----------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|------------|
| **Byte**                                                                                                                         | **Content**                                        | **Value**  |
| 1                                                                                                                                | Service Code服务代码                               | 73H        |
| 2                                                                                                                                | Routine Local Identifier例程本地身份标识           | D0H        |
| 3                                                                                                                                | Status状态： Failure失败 Control completed控制完成 |  00H  02H  |

**Remarks备注**

A “Failure” response has one of the following reasons发生“错误”的可能原因：

\- at least one electrovalve or one driver doesn’t exist or the control is not
possible at this time for safety’s
reasons.电磁阀或电机不存在或出于安全原因此时不能进行控制。

#### 3.2.10.4 Periodic Actuator Control间隔执行器控制

| **ECU to Tester ECU至诊断仪： Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                       |           |
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|-----------|
| **Byte**                                                                                                                          | **Content**                                           | **Value** |
| 1                                                                                                                                 | Service Code服务代码                                  | 73H       |
| 2                                                                                                                                 | Routine Local Identifier例程本地身份标识              | D1H       |
| 3                                                                                                                                 | Status 状态： Failure 失败 Control completed 控制完成 |  00H 02H  |

#### 3.2.10.5 Actuator Test执行器控制

**Response Without Results 无返回结果响应**

The following response will be returned, when no results are requested (“Result
Selection” = 00H).

不附带返回结果设置的响应如下：

| **ECU to Tester ECU至诊断仪：Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                      |           |
|----------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------|-----------|
| **Byte**                                                                                                                         | **Content**                                          | **Value** |
| 1                                                                                                                                | Service Code服务代码                                 | 73H       |
| 2                                                                                                                                | Routine Local Identifier例程本地身份标识             | D5H       |
| 3                                                                                                                                | Status 状态： Failure失败 Control completed 控制完成 |  00H 02H  |

**Response With Results返回结果响应**

The following response will be returned, when results are requested (“Result
Selection” = FFH).

附带返回结果设置的响应如下：

| **ECU to Tester ECU至诊断仪：Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                       |           |
|----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------|-----------|
| **Byte**                                                                                                                         | **Content**                                           | **Value** |
| 1                                                                                                                                | Service Code服务代码                                  | 73H       |
| 2                                                                                                                                | Routine Local Identifier例程本地身份标识              | D5H       |
| 3                                                                                                                                | Status 状态： Failure 错误 Control completed 控制完成 |  00H 02H  |
| 4                                                                                                                                | 1. Result (HB)结果（高字节）                          | XXH       |
| 5                                                                                                                                | 1. Result (LB)结果（低字节）                          | XXH       |
| 6                                                                                                                                | 2. Result (HB)结果（高字节）                          | XXH       |
| 7                                                                                                                                | 2. Result (LB)结果（低字节）                          | XXH       |
| 8                                                                                                                                | 3. Result (HB)结果（高字节）                          | XXH       |
| 9                                                                                                                                | 3. Result (LB)结果（低字节）                          | XXH       |
| 10                                                                                                                               | 4. Result (HB)结果（高字节）                          | XXH       |
| 11                                                                                                                               | 4. Result (LB)结果（低字节）                          | XXH       |

**Remarks备注**

A “Failure” response has one of the following reasons致“失败”的可能原因：

\- At least one electrovalve or one driver doesn’t exist or the control is not
possible at this time for safety’s reasons.
电磁阀或电机不存在，或者出于安全原因，控制不能执行。

\- If the valve relay is out of order, the routine will be aborted.

阀继电器失控，程序将中断。

#### 3.2.10.6 Dynamic Test动态测试

| **ECU to Tester ECU至诊断仪： Request Routine Results By Local Identifier Positive Response根据本地身份标识请求例程结果肯定应答** |                                                        |           |
|-----------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------|-----------|
| **Byte**                                                                                                                          | **Content**                                            | **Value** |
| 1                                                                                                                                 | Service Code服务代码                                   | 73H       |
| 2                                                                                                                                 | Routine Local Identifier例程本地身份标识               | D6H       |
| 3                                                                                                                                 | Status 状态： Failure 错误 Control completed 控制完成  |  00H 02H  |
| 4                                                                                                                                 | 1. Result Byte: delta v F (HB)结果：前轮差值（高字节） | XXH       |
| 5                                                                                                                                 | 2. Result Byte: delta v F (LB)结果：前轮差值（低字节） | XXH       |
| 6                                                                                                                                 | 3. Result Byte: delta v R (HB)结果：后轮差值（高字节） | XXH       |
| 7                                                                                                                                 | 4. Result Byte: delta v R(LB)结果：后轮差值（低字节）  | XXH       |
| 8                                                                                                                                 | reserved                                               | XXH       |
| 9                                                                                                                                 | reserved                                               | XXH       |
| 10                                                                                                                                | reserved                                               | XXH       |
| 11                                                                                                                                | reserved                                               | XXH       |

**Result Bytes结果字节**

Resolution of delta v差值分辨率：1 LSB = 0.0078125m/s

Range范围： -100 m/s … x … 100 m/s

Result is a signed word.

结果为一个有符号的字符。

### 3.2.11 Write Data By Local Identifier根据本地身份标识写数据

This services is used to set flags (specially for the assembly line).

此服务用于写相关标志值（专用于生产线）。

| **Tester Request诊断仪请求** |                                                                                             |           |
|------------------------------|---------------------------------------------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                                                                 | **Value** |
| 1                            | Service Identifier 服务身份标识                                                             | 3BH       |
| 2                            | Local Identifier本地身份标识： Hydraulic Filling Indicator液压加注指示 EOL Flag下线检测标志 |  20H 45H  |
| 3                            | Value待写数值                                                                               | XXH       |

| **ECU Positive Response ECU肯定应答** |                                 |           |
|---------------------------------------|---------------------------------|-----------|
| **Byte**                              | **Content**                     | **Value** |
| 1                                     | Service Identifier 服务身份标识 | 7BH       |
| 2                                     | Local Identifier本地身份标识    | XXH       |

**Status状态：**

**Hydraulic Filling Indicator液压加注指示**

55H-\> Filling Successfully加注成功

AAH-\>Filling Not Successfully加注失败

FFH-\>Delivery State交付状态（初始状态）

**EOL Flag下线检测标志**

55H-\>EOL CONFIG DONE下线检测完成

AAH-\>EOL CONFIG NOT DONE下线检测未完成

FFH-\>Delivery State交付状态（初始状态）

### 3.2.12 Tester Present诊断仪在线

The tester sends Tester Present messages to maintain the communication.

此服务用于保持诊断仪与电子控制器间通信。

**Tester present request message 诊断仪在线请求消息**

| **Byte**  | **Parameter Name**                                                  | **Hex Value** |
|-----------|---------------------------------------------------------------------|---------------|
| 1         | Tester present request service identifier诊断仪在线请求服务身份标识 | 3EH           |

**Tester present positive response message诊断仪在线肯定应答消息**

| **Byte**  | **Parameter Name**                                                                | **Hex Value** |
|-----------|-----------------------------------------------------------------------------------|---------------|
| 1         | Tester present positive response service identifier诊断仪在线肯定应答服务身份标识 | 7EH           |

### 3.2.13 Start Communication开始通信

This tester request is allowed only once during communication set-up.

建立通信过程中此服务仅需执行一次。

**Start Communication Request 开始通信请求**

| **Byte**  | **Parameter name**                                                     | **Hex Value** |
|-----------|------------------------------------------------------------------------|---------------|
| 1         | Start communication request service identifier开始通信请求服务身份标识 | 81H           |

**Start Communication Positive Response开始通信肯定应答**

| **Byte** | **Parameter name**                                                                   | **Hex Value** |
|----------|--------------------------------------------------------------------------------------|---------------|
| 1        | Start Communication Positive Response service identifier开始通信肯定应答服务身份标识 | C1H           |
| 2        | Key Byte 1关键字节1                                                                  | EAH           |
| 3        | Key Byte 2关键字节2                                                                  | 8FH           |

### 3.2.14 Stop Communication停止通信

After a correct reception of the "Stop Communication" Request and transmission
of the positive response, the ECU terminates the communication.

电子控制器接受到诊断仪发送的“停止通信”请求并返回肯定应答后，电子控制器即中断通信。

**Stop communication request message“停止通信”请求消息**

| **Byte** | **Parameter Name**                                                    | **Hex Value** |
|----------|-----------------------------------------------------------------------|---------------|
| 1        | Stop communication request service identifier停止通信请求服务身份标识 | 82H           |

**Stop communication positive response message “停止通信”正面响应消息**

| **Byte**  | **Parameter name**                                                                  | **Hex Value** |
|-----------|-------------------------------------------------------------------------------------|---------------|
| 1         | Stop communication positive response service identifier停止通信肯定应答服务身份标识 | C2H           |

### 3.2.15 Stop Diagnostic Session停止诊断

**Stop diagnostic session request message“停止诊断”请求消息**

| **Byte** | **Parameter Name**                                                 | **Hex Value** |
|----------|--------------------------------------------------------------------|---------------|
| 1        | Stop diagnostic session service identifier停止诊断请求服务身份标识 | 20H           |

**Stop diagnostic session response message “停止诊断”正面响应消息**

| **Byte**  | **Parameter name**                                                                       | **Hex Value** |
|-----------|------------------------------------------------------------------------------------------|---------------|
| 1         | Stop diagnostic session positive response service identifier停止诊断肯定应答服务身份标识 | 60H           |

### 3.2.16 Access Timing Parameters访问时间参数

This service is implemented to allow the improvement of the timing of the
communication in different case.

该服务用于完善不同情况下的通信时间。

| **Tester Request诊断仪请求** |                                                                                                                                                                        |              |
|------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| **Byte**                     | **Content**                                                                                                                                                            | **Value**    |
| 1                            | Service Identifier 服务身份标识                                                                                                                                        | 83H          |
| 2                            | Timing parameter identifier时间参数识别： Read limits of possible values 读取可能的极限值 Set parameter to default 设置参数为默认 Read active parameters读取激活的参数 |  00H 01H 02H |

| **ECU Positive Response电子控制器肯定应答** |                                                                                                                                                                        |              |
|---------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------|
| **Byte**                                    | **Content**                                                                                                                                                            | **Value**    |
| 1                                           | Service Identifier 服务身份标识                                                                                                                                        | C3H          |
| 2                                           | Timing parameter identifier时间参数识别： Read limits of possible values 读取可能的极限值 Set parameter to default 设置参数为默认 Read active parameters读取激活的参数 |  00H 01H 02H |

### 3.2.17 ECU Reset ECU复位

| **Tester Request诊断仪请求** |                                                            |           |
|------------------------------|------------------------------------------------------------|-----------|
| **Byte**                     | **Content**                                                | **Value** |
| 1                            | Service Identifier 服务身份标识                            | 11H       |
| 2                            | Reset Mode复位模式： Hard Reset硬件复位 Soft Reset软件复位 |  01H 03H  |

| **ECU Positive Response电子控制器肯定应答** |                                                            |           |
|---------------------------------------------|------------------------------------------------------------|-----------|
| **Byte**                                    | **Content**                                                | **Value** |
| 1                                           | Service Identifier 服务身份标识                            | 51H       |
| 2                                           | Reset Mode复位模式： Hard Reset硬件复位 Soft Reset软件复位 |  01H 03H  |

### 3.2.18 Security Access安全访问

The purpose of this service is to provide a means to access data and/or
diagnostic services which have restricted access for security, emissions or
safety reasons. The security concept uses a seed and key relationship. Before
the service of writing data by local identifier, the security access must be
done firstly.

此服务的目的是提供一种得到数据和因为安全原因限制访问的诊断服务的方法。在根据本地身份标识写数据前，必须先获得安全访问权限。

This service must follow a Start Diagnostic Session service. Between seed and
key no other message (except tester present) is allowed.

这个服务必须在开始诊断会话后。在种子与钥匙之间，除了测试仪在线请求外，不允许任何消息。

| **Tester Request诊断仪请求** |                                                 |           |
|------------------------------|-------------------------------------------------|-----------|
| **Byte**                     | **Content**                                     | **Value** |
| 1                            | Service Identifier 服务身份标识                 | 27H       |
| 2                            | Security Access Type安全访问形式： Request Seed |  01H      |

| **ECU Positive Response电子控制器肯定应答** |                                                 |           |
|---------------------------------------------|-------------------------------------------------|-----------|
| **Byte**                                    | **Content**                                     | **Value** |
| 1                                           | Service Identifier 服务身份标识                 | 67H       |
| 2                                           | Security Access Type安全访问形式： Request Seed |  01H      |
| 3                                           | Seed –High Byte 种子-高字节                     | xxH       |
| 4                                           | Seed –Low Byte 种子-低字节                      | xxH       |

| **Tester Request诊断仪请求** |                                             |           |
|------------------------------|---------------------------------------------|-----------|
| **Byte**                     | **Content**                                 | **Value** |
| 1                            | Service Identifier 服务身份标识             | 27H       |
| 2                            | Security Access Type安全访问形式： Seed Key |  02H      |
| 3                            | Key -High Byte 钥匙 –高字节                 | xxH       |
| 4                            | Key -Low Byte 钥匙 -低字节                  | xxH       |

The key is calculated as follows钥匙计算如下：

Key=（65521\*（seed+1501））XOR seed.

| **ECU Positive Response电子控制器肯定应答** |                                             |           |
|---------------------------------------------|---------------------------------------------|-----------|
| **Byte**                                    | **Content**                                 | **Value** |
| 1                                           | Service Identifier 服务身份标识             | 67H       |
| 2                                           | Security Access Type安全访问形式： Seed Key |  02H      |
| 3                                           | Security Access Status = Allowed            | 34H       |

# 4 DTC List:故障代码列表

| **DTC** | **Failure Description**                                                                                   |
|---------|-----------------------------------------------------------------------------------------------------------|
| C0024   | MCU_MU_CLK_Monitor_Failed 芯片时钟检测错误                                                                |
| C0032   | MCU_MC_ROM_Failed 芯片ROM错误                                                                             |
| C0033   | MCU_MC_RAM_Failed 芯片RAM错误                                                                             |
| C0040   | MCU RAM Stack Overflow Fault 芯片RAM堆栈错误                                                              |
| C0041   | MCU Hardware Reset 芯片硬件复位                                                                           |
| C0044   | Solid State Relay\_ Relay over current 固态继电器_过流                                                    |
| C0045   | Solid State Relay\_ Relay shorted (Stuck on) 固态继电器_继电器短路（卡死）                                |
| C0046   | Solid State Relay\_ shorted to ground 固态继电器_与地短接                                                 |
| C0051   | Battery Voltage \_Battery under-voltage 1 (7V \< Voltage \< 9V)  电池电压过低1，（大于7伏小于9伏）        |
| C0052   | Battery Voltage \_Battery under-voltage 2 (Voltage \<= 7V)  电池电压过低2，（小于等于7伏）                |
| C0053   | Battery Voltage \_Battery over-voltage 电池电压过高                                                       |
| C0060\* | Brake Pedal Not Applied with Decel不踩刹车有减速度                                                        |
| C0061\* | Brake Pedal Always Applied Without Decel Fault 踩下刹车时没有减速度                                       |
| C0062\* | Brake Diode Breakdown 刹车二极管击穿                                                                      |
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
| C0104   | Rear\_ WSS_Plausibility01 后轮轮速传感器信号失真等级01                                                    |
| C0105   | Rear\_ WSS \_Plausibility02后轮轮速传感器信号失真等级02                                                   |
| C0106   | Rear\_ WSS \_Plausibility03后轮轮速传感器信号失真等级03                                                   |
| C0107   | Rear\_ WSS \_ Plausibility04后轮轮速传感器信号失真等级04                                                  |
| C0108   | Rear\_ WSS \_ Plausibility05后轮轮速传感器信号失真等级05                                                  |
| C0120   | Front \_NO Coils_Short to battery 前轮常开线圈接电源                                                      |
| C0121   | Front\_ NO Coils_Short to ground or Open solenoid 前轮常开线圈接地或开路                                  |
| C0130   | Front\_ NCCoils_Short to battery 前轮常闭线圈接电源                                                       |
| C0131   | Front\_ NC Coils_Short to ground or Open solenoid 前轮常闭线圈接地或开路                                  |
| C0160   | Rear\_ NO Coils_Short to battery 后轮常开线圈接电源                                                       |
| C0161   | Rear\_ NO Coils_Short to ground or Open solenoid后轮常开线圈接地或开路                                    |
| C0170   | Rear\_ NC Coils_Short to battery后轮常闭线圈接电源                                                        |
| C0171   | Rear\_ NC Coils_Short to ground or Open solenoid后轮常闭线圈接地或开路                                    |
| C0210   | Warning Lamp output\_ Short to battery 报警灯输出与电源短路                                               |
| C0213   | Warning Lamp output\_ Short to ground or open报警灯输出与地短路或开路                                     |
| C0230   | Vehicle speed output\_ Short to ground 车速输出口与地短路                                                 |
| C0231   | Vehicle speed output\_ Short to battery 车速输出口与电源短路                                              |

\* Whether the fault is detected depends on the software configuration and
hardware interface.

\*根据软件配置和硬件接口决定是否检测该故障
