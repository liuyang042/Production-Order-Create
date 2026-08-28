# Production-Order-Create / Black-Over

**盖黑工单开单流程（Black-Over Production Order Creation）**

[![在线演示](https://img.shields.io/badge/在线演示-访问页面-brightgreen)](https://liuyang042.github.io/Production-Order-Create/Black-Over/)

## 📖 项目简介

本项目为**盖黑（及深色）工单开单流程**的操作指引与培训教材网站，系统化地展示了从启动前确认到工单投料结束的完整7步开单流程。内容涵盖SAP系统操作、功能代码调用、Excel工具使用及关键注意事项，旨在帮助生产、计划及相关部门人员规范、高效地完成盖黑工单的创建与跟进。

🔗 **在线演示**: [https://liuyang042.github.io/Production-Order-Create/Black-Over/](https://liuyang042.github.io/Production-Order-Create/Black-Over/)

## ✨ 核心流程（7步详解）

### 第一步：启动前确认收货
启动盖黑（或深色）流程前，须先确认该工单已完成收货。若尚未收货，需先行完成收货操作。[reference:0]
- **功能代码**：`ZSOHPP190`

### 第二步：提交盖黑需求申请
确认收货后，由需求部门填写盖黑需求表，并向 PPC 正式提交盖黑申请。[reference:1]
- **附件下载**：[盖黑需求表.xlsx](https://github.com/liuyang042/Production-Order-Create/blob/main/Black-Over/Black-Over_Request_Form.xlsx?raw=true)

### 第三步：获取黑色销售订单
PPC 提供黑色的销售订单号码，且确认是否需要补开单。[reference:2]

### 第四步：储存地点转销售订单
操作 TF 储存地点至销售订单（413 E 移动类型）[reference:3]
- **功能代码**：`ZSOHWM002`

### 第五步：APO 系统创建黑色工单
本步骤包含5个子操作：[reference:4]
- **5-1**：操作功能代码 `ZSOH_SE06`
- **5-2**：操作功能代码 `ZSOH_SE17`
  - ① 删除 SF0251（補布原因）特性值
  - ② 更改 PG0886（分紗ID）特性值为“F”开头
  - ③ 更改 PF0621（是否已鎖胚）特性值为“Z”
- **5-3**：操作功能代码 `ZTRIM_XS___START` — 操作：分缸
- **5-4**：操作功能代码 `ZSOH_SE17` — 更改 PF0621（是否已鎖胚）特性值为“Y”（锁胚）
- **5-5**：手动转工单：`/SAPAPO/RRP3`

### 第六步：锁胚 · 报工 · 发单
黑色工单锁胚-报工-发单[reference:5]
- **功能代码**：`ZSOHPP159`
- **注意事项**：
  - 抽胚异常栏位注明抽布缸号已染色布盖黑，责任部门
  - 抽已染色布盖色：Y
  - 差异原因：织厂-RDK1，染厂-RDD7，整理厂-RDF1，PPC-RDS1

### 第七步：工单投料 & 结束
工单投料[reference:6]
- **功能代码**：`MIGO`（收货批次在线边仓则直接投料，收货批次在成品仓则正常流程从成品仓提布）
- **最后确认**：新单补开或不需要补开后，盖黑流程结束。[reference:7]

## 🛠️ 技术工具

- **SAP系统**：多个定制功能代码（ZSOHPP190、ZSOHWM002、ZSOH_SE06、ZSOH_SE17、ZTRIM_XS___START、ZSOHPP159、MIGO、/SAPAPO/RRP3）
- **Excel工具**：盖黑需求申请表（.xlsx）
- **前端技术**：HTML/CSS/JavaScript 构建响应式操作指引页面

## 🚀 快速开始

直接访问在线演示地址即可浏览完整的盖黑工单开单流程：
[https://liuyang042.github.io/Production-Order-Create/Black-Over/](https://liuyang042.github.io/Production-Order-Create/Black-Over/)
