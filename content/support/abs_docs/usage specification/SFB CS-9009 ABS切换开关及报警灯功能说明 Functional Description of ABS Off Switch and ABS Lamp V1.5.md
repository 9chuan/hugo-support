---
title: SFB CS-9009 ABS切换开关及报警灯功能说明
linktitle: SFB CS-9009 ABS切换开关及报警灯功能说明
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## 更新记录
| ![123123](18adad495b7088a124cf37a2e88efbdd.png "23323") | **客户规范** **Customer Specification**                                           |                 |               |
|-------------------------------------------------|-----------------------------------------------------------------------------------|-----------------|---------------|
| SPEC NO. :SFB CS-9009                           | ABS切换开关和报警灯功能说明 Functional Description of ABS Off Switch and ABS Lamp | SF10 ABS System |               |
| Version: V1.5                                   |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
|                                                 |                                                                                   |                 |               |
| V1.5                                            | Disable State 3(6)；Self-checking speed 3(1)                                      | 2/Jan/20        | Matthew       |
| V1.4                                            | Revise Chapter 3(1)                                                               | 27/Oct/18       | Albert Ye     |
| V1.3                                            | SPEC No. Change to SFB CS-9009                                                    | 22/May/17       | Albert Ye     |
| V1.2                                            | Diagram Change                                                                    | 26/Apr/16       | Albert Ye     |
| V1.1                                            | Modify “3 ABS Lamp Behavior”, “2.3 Specific behavior during ABS OFF modeABS”      | 26/Nov/15       | Rich Chen     |
| V1.0                                            | 起草 Draft                                                                        | 7/Apr/15        | Taylor Wang   |
| **版本/Ver.**                                   | **修改/Modification**                                                             | **日期/Date**   | **作者/Name** |
| 发起 Prepared:                                  | 检查 Checked:                                                                     | 发布 Released： | Page:1 / 6    |


# 1Reference documents参考文档

## 1.1 Customer reference documents客户参考文档

No customer specific documents无客户详细文档

# 2 ABS OFF functionABS关闭功能

## 2.1 ABS Enable/Disable state transition ABS使能/禁用状态切换

ABS Enable/Disable transition is possible under below
ConditionsABS使能/禁用在以下条件下可以切换：

(a)Front and Rear Wheel Speed less than Vmin前后轮速小于最低速度

(b)Vehicle is NOT in Test Mode (Diag Mode)车辆不在测试模式（诊断模式）下

For entry to ABS Enable/Disable mode, press Off switch more than 3 s, ABS Lamp
starts blinking @400ms and then release Off Switch within 5 s, which results in
state transition from ABS Enable toDisable or vice versa. If ABS is disabled ABS
Lamp blinks @ 1200ms, and if ABS isenabled ABS Lampwill be OFF for a fault free
system.

进入ABS使能/禁用模式条件：按下开关，3秒后ABS报警灯开始以400ms的频率闪烁，如果在5s内松开开关，那么ABS从使能转为禁用模式，反之亦然。当ABS处于禁用模式时，ABS报警灯以1200ms的频率闪烁，当ABS处于使能模式，ABS报警灯会因无故障自动关闭。

![](media/e3a0076aa5f344fbbb639973c373a916.png)

## 2.2 Exit Conditions: 退出条件

a. When either of the wheel speed is found greater than Vmin, the mode change
request isignored and ABS ECU continues to remain in the existingmode.

当任何一个轮子轮速大于最小速度值，模式切换请求被忽略，ABS ECU始终保持当前模式。

![](media/50e3adfda4046d29c1e5dbf9d43370d5.png)

b. When switch “Pressed” for more than 3 Sec and not released within 5 Seconds,
the modechange request is ignored and ABS ECU continues to remain in the
existing mode.

当开关被按下超过3秒，并在5秒内未松开时，模式切换请求被忽略，ABS
ECU始终保持当前模式。

![](media/874c125f3bc91b7b52131a09d045aa6e.png)

c. When switch is found stuck in “Pressed” state for more than 30 Sec ABS ECU
treats theswitchsignal as faulty, and enters to “ABS Available” state. (Only if
system is found fault free).Only if ignited again, the ABS off function would be
done.

当开关被按下状态超过30秒时，ABS
ECU将开关信号作为故障，进入ABS使能模式（只有在系统被认定为无其他故障时）。只有重新点火，ABS关闭功能才能使用。

![](media/803d9a025bed429bf043683677522f74.png)

## 2.3Specific behavior during ABS OFF modeABS关闭时的具体动作

Partial failure Monitors are DISABLED during ABS OFF mode. Refer to Fail safe
specification for further details about the monitor function.

在ABS关闭模式下部分故障监控无法运行，关于监控功能的更多说明，参考故障安全规范。

# 3 ABS Lamp Behavior报警灯动作

ABS Lamp is controlled by following conditions.

ABS 报警灯受以下条件控制。

(1)ABS Lamp during Failure State ABS报警灯在故障状态下：

—If any type of ABS failure is detected and stored, ABS Lamp is Turned ON.

如果检测并存储到任何形式的ABS故障，ABS报警灯点亮。

—If the failure is eliminated, ABS Lamp is Turned OFF at the curent IGN CYCLE,
at the next IGN CYCLE, or after vehiclespeed exceeds 5kphat the next IGN CYCLE.

如果故障被消除，ABS报警灯将在当前点火周期，下一个点火周期，或下一个点火周期车速达到5kph后熄灭。

—After IGN, the self-test is not completed or the self-test is not passed, ABS
Lamp is ON.

IGN上电后，自检未完成或自检未通过，ABS报警灯点亮。

—When the low speed wheel speed difference fault occurs, ABS Lamp flashes at
200ms frequency.

低速轮速差故障时，报警灯以200ms的频率闪烁。

(2)ABS Lamp during Disabled State报警灯在ABS禁用状态下：

—During ABS Off function is activated ABS Lamp Blinks at 1200ms.

在ABS 禁用被激活时，ABS报警灯以1200ms的频率闪烁。

(3)ABS Lamp during Switch Pressed State ABS报警灯在开关按下状态下：

—During switch pressed state ABS Lamp Blinks at 400ms.

在开关被按下时，ABS报警灯以400ms的频率闪烁。

(4)ABS Lamp during Available State ABS报警灯在ABS使能状态下：

—During ABS is active, ABS Lamp is Turned OFF.But if switch is found stuck in
“Pressed” state for more than 30 Sec, ABS Lamp is Turned ON.

当ABS使能时，ABS报警灯熄灭。但如果开关在按下状态超过30秒时，ABS报警灯常亮。

(5)ABS Lamp during Diagnostic mode ABS报警灯在诊断模式下：

—During ECU is in Diag mode, ABS Lamp is Turned ON.

ECU在诊断模式下时，ABS报警灯点亮。

(6) ABS Lamp during rear wheel ABS Disabled State ABS
报警灯在后轮ABS禁用状态下：

—In some software configurations, rear wheel ABS can be disabled, and the lamp
flashes at the frequency of 2S when disabled.

在部分软件配置下，可以禁用后轮ABS，禁用后报警灯以2S的频率闪烁。
