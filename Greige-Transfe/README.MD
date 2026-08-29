# Production-Order-Create / Greige-Transfe

**胚布抽用工单开单流程（Greige Transfer Production Order Creation）**

[![在线演示](https://img.shields.io/badge/在线演示-访问页面-brightgreen)](https://liuyang042.github.io/Production-Order-Create/Greige-Transfe/)

## 📖 项目简介

本项目为**胚布抽用工单开单流程**的操作指引与培训教材网站，系统化地展示了从胚布抽用通知到工单投料结束的完整7步开单流程。内容涵盖SAP系统操作、功能代码调用及关键注意事项，旨在帮助生产、计划及相关部门人员规范、高效地完成胚布抽用工单的创建与跟进。

🔗 **在线演示**: [https://liuyang042.github.io/Production-Order-Create/Greige-Transfe/](https://liuyang042.github.io/Production-Order-Create/Greige-Transfe/)

## ✨ 核心流程（7步详解）[reference:0]

### 第一步：胚布抽用通知

生产部门通过邮件发出胚布抽用通知。[reference:1]

### 第二步：确认收货

先确认该工单已完成收货。若尚未收货，需先行完成收货操作。[reference:2]
- **功能代码**：`ZSOHPP190`

### 第三步：储存地点转销售订单

操作 TF 储存地点至销售订单（413 E 移动类型）[reference:3]
- **功能代码**：`ZSOHWM002`

### 第四步：APO 系统创建工单（方法1——适用于大货单）

在 APO 系统，通过复制生产部要求颜色对应的工单，创建计划单。[reference:4]

- **4-1-1**：操作功能代码 `ZSOH_SE06`[reference:5]
- **4-1-2**：操作功能代码 `ZSOH_SE17`[reference:6]
  - ① 删除 SF0251（補布原因）特性值
  - ② 更改 PG0886（分紗ID）特性值为“F”开头
  - ③ 更改 PF0621（是否已鎖胚）特性值为“Z”
- **4-1-3**：操作功能代码 `ZTRIM_XS___START` — 操作：分缸[reference:7]
- **4-1-4**：操作功能代码 `ZSOH_SE17` — 更改 PF0621（是否已鎖胚）特性值为“Y”（锁胚）[reference:8]
- **4-1-5**：手动转工单：`/SAPAPO/RRP3`[reference:9]

### 第五步：ECC 系统创建工单（方法2——适用于办单）

在 ECC 系统，通过复制生产部要求颜色对应的工单，复制创建工单。[reference:10]

- **4-2-1**：操作功能代码 `CO01` — 操作：复制创建工单[reference:11]
- **4-2-2**：重读数据[reference:12]
- **4-2-3**：在 Components（工单元件）界面，删除“B”开头的物料数据[reference:13]

### 第六步：锁胚 · 报工 · 发单

工单锁胚-报工-发单[reference:14]
- **功能代码**：`ZSOHPP159`
- **操作要点**：[reference:15]
  - ① 删除不需要的工序
  - ② 抽胚异常栏位注明抽布缸号胚布染色
  - ③ 填写差异原因：`RDD5`（胚布抽用）
  - 双击工单号码，进入 Components（工单元件）界面，进行锁胚

### 第七步：工单投料

工单投料[reference:16]
- **功能代码**：`MIGO`（收货批次在线边仓则直接投料，收货批次在成品仓则正常流程从成品仓提布）[reference:17]

> ✅ 胚布抽用工单开单流程结束。[reference:18]

## 🛠️ 技术工具

- **SAP系统**：多个定制功能代码（ZSOHPP190、ZSOHWM002、ZSOH_SE06、ZSOH_SE17、ZTRIM_XS___START、ZSOHPP159、CO01、MIGO、/SAPAPO/RRP3）
- **前端技术**：HTML/CSS/JavaScript 构建响应式操作指引页面

## 🚀 快速开始

直接访问在线演示地址即可浏览完整的胚布抽用工单开单流程：
[https://liuyang042.github.io/Production-Order-Create/Greige-Transfe/](https://liuyang042.github.io/Production-Order-Create/Greige-Transfe/)
