---
title: SFB CS-9012 SF10 ABS诊断工具使用说明
linktitle: SFB CS-9001 SF10 ABS诊断工具使用说明
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## 更新
|                       | **客户规范** **Customer Specification**                     |                 |               |
|-----------------------|-------------------------------------------------------------|-----------------|---------------|
| SPEC NO. :SFB CS-9012 | ABS诊断工具使用说明 Instructions of the ABS Diagnostic Tool | SF10 ABS System |               |
| Version: V1.4         |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
|                       |                                                             |                 |               |
| V1.4                  | Revise translation error in section 3.3                     | 2Jan20          | Matthew       |
| V1.3                  | Revise chapter 2                                            | 11Aug17         | Albert Ye     |
| V1.2                  | Rename document                                             | 22May17         | LiXin         |
| V1.1                  | Redefine the OBD-II ports in 1.1                            | 3Mar17          | LiXin         |
| V1.0                  | 起草 Draft                                                  | 18Feb17         | LiXin         |
| **版本/Ver.**         | **修改/Modification**                                       | **日期/Date**   | **作者/Name** |
| 发起 Prepared:        | 检查 Checked:                                               | 发布 Released： | Page:1 / 11   |

**  
**

# 缩写(Abbreviation)

**Abbreviation  Description**

ABS Anti-Block system

DTC Diagnostic Trouble Code

ECU Electronic controller unit (ABS-Controller)

EEPROM Electrical Erasable Read-Only-Memory

EOL End of Line

FW Front wheel

RW Rear wheel

NC Normal close

NO Normal open

# 1 准备(Preparation)

1.1 接上诊断仪线束。

Connect the diagnostic device to the vehicle.

| 针脚 Pin | 颜色 Color     | 定义 Definition |
|----------|----------------|-----------------|
| 4        | 黄色 Yellow    | GND             |
| 5        | 橙色 Orange    |                 |
| 7        | 深蓝 Dark blue | K_LINE          |
| 16       | 浅红 Light red | Battery(12V)    |

1.2 首次运行诊断仪软件需先安装驱动程序SAFE_DiagnosticTool_Drivers.exe

The SAFE_DiagnosticTool_Drivers.exe needs to be installed when you use the
diagnostic software for the first time.

# 2 连接(Connection)

1.
打开软件时它会自动选择编号最大的COM口，核对默认选择的COM口和设备管理器中诊断仪的COM口相同。

When you open the diagnostic software, it will choose the biggest available
serial port automatically, please confirm the port number is the same as the
diagnostic device’s port number in the Device Manager(port number in the Device
Manager must not bigger than 9,otherwise modified it to a small one).

软件界面：

software interface：

诊断仪在设备管理器中的串口号： diagnostic device’s port number in the Device
Manager:

2\. 默认的波特率，ECU地址，诊断仪地址都不用修改。

Keep the default Baud rate, ECU Addr, Tester Addr;

3\. 点击后显示栏出现“供应商模式”则连接成功。

Clickand if the textbox displays “Supplier Mode” then the connection is
successful.

# 3 操作(Operation)

双击诊断条目后就能在显示栏看到对应的返回信息。

Double click the diagnostic item and the result will be presented in the
textbox.

### 3.1 常用功能Commonly used functions

**当前故障代码：**当前点火周期内检测到的故障的代码；

Current DTC: The DTC detected during the current ignition cycle.

**历史故障代码：**本次点火之前发生过的故障的代码；

Historical DTC: The DTC that stored in the ECU’s EEPROM.

**诊断故障代码状态：**故障发生时车辆的状态（车速、刹车信号、点火次数）；

Status of DTC: The status of the vehicle(speed, brake signal, IGN times) when
the trouble occured.

**清除故障代码：**清除当前故障代码和历史故障代码；

Clear DTC: Clear the Current and the Historical DTC.

有故障代码返回时，可以点击主窗口右下角的根据故障代码查询故障原因。

When the DTC exists, you can click to find the cause of the trouble.

### 3.2 读取Read data

主要功能是返回ECU的基本信息和状态。

Get the information and status of ECU.

**客户零件号：**客户给该SF10-ABS定义的代号；

Customer Part Number: the part number that customer defined for this ABS;

**赛福零件号：**赛福给该ABS定义的代号；

SFB Part Number: the part number that SAFE-Brakes defined for this ABS;

**项目名称：**赛福给该ABS定义的项目代号；

Project Name: the project name that SAFE-Brakes defined for this ABS;

**生产日期：**产品生产日期；

Product Date: Product production date;

**液压加注标志：**液压加注是否完成；

Hydraulic Filling Indicator: hydraulic filling state;

**下线检测标志：**下线检测是否完成；

EOL Flag: end of line test state;

**模拟量信号：**电源电压、点火电压、电机电压、前后刹车信号电压、ABS开关电压；

Analog Signal: Supply voltage, IGN voltage, pump motor voltage, brake signal
voltage, ABS switch voltage;

下面的两个表是ECU各部分的正常电压：

The two tables below are the normal voltage of different part of ECU：

| 电源电压 Supply voltage                                            | 随电瓶电压变化 Change with the battery voltage  |
|--------------------------------------------------------------------|-------------------------------------------------|
| 点火电压 Ignition voltage                                          | 随电瓶电压变化 Change with the battery voltage  |
| 电机供电电压 The motor power supply voltage                        | 随电瓶电压变化 Change with the battery voltage  |
| 电机正端电压（无控制状态） Voltage of the motor(no control)        | 0-0.5V                                          |
| 电机诊断电压（无控制状态） Diagnosis voltage of motor(no control)  | 2-2.1V                                          |

|                                | 无控制 No Control | 有控制 Controlled |
|--------------------------------|-------------------|-------------------|
| 前刹车电压 Front brake voltage | 2.5-2.6V          | 5.05-5.15V        |
| 后刹车电压 Rear brake voltage  | 2.5-2.6V          | 5.05-5.15V        |
| ABS OFF电压 Voltage of ABS OFF | 2.5-2.6V          | 1.25-1.35V        |

**数字量信号：**阀状态、电机MOSFET状态、阀MOSFET状态、前后刹车信号状态、ABS开关状态。

Digital Signal: valve state, motor MOSFET state, valve MOSFET state, brake
state, ABS switch state.

正常情况下的数字量信号：

the digital signal under normal circumstances:

| 阀状态 Valve state                      | 关 OFF                                                 |
|-----------------------------------------|--------------------------------------------------------|
| 电机MOSFET状态 Motor MOSFET state       | 关 OFF                                                 |
| 阀MOSFET状态 Valve MOSFET state         | 开 ON                                                  |
| 前刹车信号状态 Front brake signal state |   跟随实际的外部信号 Follow the actual external signal |
| 后刹车信号状态 Rear brake signal state  |                                                        |
| ABS开关状态 ABS switch state            |                                                        |

### 3.3 例程Routine

显示栏中出现“---------”时，表示例程正在执行，一段时间后会自动返回执行结果。

When "---------" appears in the textbox, it indicating that the routine is
executing and the result will be returned when the routine is completed.

**轮速传感器：**检测前后轮最大最小速度；

Wheel Speed Sensor: detecting the speed of front and rear wheel;

**液压泵电机：**泵电机动作；

Pump Motor: pump motor acting;

**前轮常开电磁阀：**前轮常开阀动作；

FW NO valve: FW NO valve acting;

**前轮常闭电磁阀：**前轮常闭阀动作；

FW NC valve**:** FW NC valve acting;

**后轮常开电磁阀：**后轮常开阀动作；

RW NO valve: RW NO valve acting;

**后轮常闭电磁阀：**后轮常闭阀动作；

RW NC valve: RW NC valve acting;

**关闭车速限制：**关闭车速10km/h以上时退出诊断的限制；

Speed Limit Disable: Close the limit that when the speed exceed 10km/h the
diagnostic will be quit automatically;

**前轴抽真空加注：**执行前轴抽真空加注控制序列，执行时间100s；

FW Vacuum Filling: draining the gas in the front axle pipe and filling brake
fluid;

**后轴抽真空加注：**执行后轴抽真空加注控制序列，执行时间100s；

RW Vacuum Filling: draining the gas in the rear axle pipe and filling brake
fluid;

**前后轴同时抽真空加注：**执行前后轴同时抽真空加注控制序列，执行时间100s；

FW & RW Vacuum Filling: draining the gas in the front and rear axle pipe and
filling brake fluid;

**前轮人工排气阶段1：**前轮一级回路排气；

FW exhaust stage 1: front wheel primary circuit manual exhaust;

**前轮人工排气阶段2：**前轮二级回路排气；

FW exhaust stage 2: front wheel secondary circuit manual exhaust;

**后轮人工排气阶段1：**后轮一级回路排气；

RW exhaust stage 1: rear wheel primary circuit manual exhaust;

**后轮人工排气阶段2：**后轮二级回路排气；

RW exhaust stage 2: rear wheel secondary circuit manual exhaust;

**另外(In addition)：**

耗时较长，如果有必要可以点击主窗口右下角的强行停止。

Will spent some time to complete, if necessary you can click to end it.

抽真空加注例程适用于专用设备，人工排气适用于手工排气。人工排气具体操作参考SF10_ABS产品售后说明书。

Vacuum filling routine suits for special equipment, exhaust routine suits for
manual exhaust. Manual exhaust specific operation references to ABS product
after-sales service.

**警告Warning：**

使用电子控制器内部排气程序时，所有电磁阀的动作时间会自动运行。宁波赛福建议使用存储器内部固化的排气程序，以防电磁阀过热导致系统损坏。严禁短时间内重复执行单个排气程序2次及以上。如需重复执行单次或全部排气程序，请先等待5分钟，冷却电磁阀，用以保护电磁阀因过热损坏。

All valve actuation times automatically done by the ECU with using of the ROM
resident routine “repair bleeding”. SFB recommends to use this ROM resident
function to avoid any damages at the valves caused by overheating. It is not
allowed to repeat the repair bleeding routines twice times within a short time!
In case of repetition of a once phase or the entire bleeding routine it is
absolute necessary to wait a time of 5 minutes to cool the solenoid valves.

### 3.4 写数据Write data

双击“安全访问”，当显示栏中出现“允许访问”后就可以双击写数据功能修改ECU的液压加注状态和下线检测状态。

Double click the “Security access” and if the textbox displays “Security
allowed” you can modify the hydraulic filling indicator and EOL Flag.

**注意 Note：**

请不要随意修改，保持出厂默认状态，若有问题，质询供应商。

Please do not modify arbitrarily, keep the factory default state, if there is a
problem, ask the supplier.
