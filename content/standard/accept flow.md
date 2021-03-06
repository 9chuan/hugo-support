---
title: 车辆验收流程
linktitle: 车辆验收流程
toc: true
type: book
date: "2021-11-02T00:00:00+01:00"
authorsauthorsauthors: ["admin"]

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 1
---

## 版本

2021/11/01 V1.0 版本 起草 黄云龙



## 职责

* 项目主管负责发起车辆验收相关工作</br>
* 标定工程师负责对接车辆验收相关工作

## 流程

1. 项目经理发起验收，并向整车厂发布验收邀请函

1. 整车厂</br>
		✅ 确认验收日期，并填写验收登记表	      
		⬛ 准备本地车辆，赛福将进行远程刷程测试车辆（加快车辆验收确认速度）

1. 标定人员接收到信息</br>

	✅ 清理车辆油污、清洗卡钳、保证油量、保证电瓶电量</br>
	✅ 与验收人员沟通，协商验收具体事项</br>
	⬛ 采集<客户项目认证报告>[^1]</br>
	✅ 提交车辆参数，用于应用主管/研发主管审核，并进行集成远程刷程使用 
	
1. 系统工程师收到远程刷程请求</br>
		✅ 上传程序副本到COAS系统[^2]</br>
		✅ 指导对方工程师进行远程刷写操作
	
1. 整车厂测试流程（此阶段不应迟于场地验收阶段）</br>
		✅ 按照整车厂验收流程进行验收操作，并向系统工程师/标定工程师反馈验收结果</br>
		⬛ 按照赛福标准进行验收操作，并向系统工程师/标定工程师反馈验收结果</br>
		✅ 整车上依照反馈结果可以决定是否进行场地验收工作
	
1. 场地验收流程</br>
		✅ 标定工程师向整车厂介绍场地相关及流程</br>
		✅ 交流车辆问题</br>
		✅ 交流场地验收路线，驾驶安全准则</br>
		⬛ 展示<客户项目认证报告>
	
1. 实车验收阶段

   | 序号 |     路面     | 速度(km/h) |      ABS状态      |  测试方式  |     备注     |
   | :--: | :----------: | :--------: | :---------------: | :--------: | :----------: |
   |  1   |   高附路面   |     60     | ABS ON & ABS OFF  | FA/RA/FARA | 数据采集对比 |
   |  2   |   低附路面   |     60     | ABS ON  & ABS OFF | FA/RA/FARA | 数据采集对比 |
   |  3   |    高到低    |   50阶跃   |      ABS ON       | FA/RA/FARA | 数据采集对比 |
   |  4   |    低到高    |   50阶跃   |      ABS ON       | FA/RA/FARA | 数据采集对比 |
   |  5   |  非铺装路面  |     50     |      ABS ON       | FA/RA/FARA | 数据采集对比 |
   |  6   | 湿玄武岩路面 |     30     |      ABS ON       | FA/RA/FARA |   选做项目   |
   |  7   | 各种速度测试 |            |  ABS ON/ABS OFF   | FA/RA/FARA |   选做项目   |

1. 整车厂与赛福相互沟通</br>
		✅ 沟通交流场地试验车状态</br>
		⬛ 沟通交流整车厂试验车与场地试验车状态</br>
		⬛ 场地车辆再进行测试更改</br>
		✅ 标定工程师填写<摩托车ABS场地验收报告>[^3]，初步提交给应用主管审核</br>
		✅ 应用主管审核通过，双方进行会签。会签报告由标定工程师上传，并由系统工程师/项目工程师发送到整车厂相应管理人员</br>
		✅ 确认下一步动作



[^1]: 用于程序验证、客户验收凭证。仅最终验收提供，一轮验收不提供
[^2]: 一款赛福内部用于标定/系统/项目的简易管理软件
[^3]: 用于客户实地验收记录填写，及客户认可程序的凭证
