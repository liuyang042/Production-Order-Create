# Production-Order-Create / Warp-Knitting

**经编常规工单开单流程（Warp-Knitting Production Order Creation）**

[![在线演示](https://img.shields.io/badge/在线演示-访问页面-brightgreen)](https://liuyang042.github.io/Production-Order-Create/Warp-Knitting/)

## 📖 项目简介

本项目为**经编常规工单开单流程**的操作指引与培训教材网站，系统化地展示了从MRP产生计划单到审单、报工、发单的完整7步开单流程。内容涵盖SAP系统操作、功能代码调用、两大生产路径（G单模式与工单直接生产模式）说明以及详细的操作步骤图解，旨在帮助生产、计划及相关部门人员规范、高效地完成经编常规工单的创建与跟进。

🔗 **在线演示**: [https://liuyang042.github.io/Production-Order-Create/Warp-Knitting/](https://liuyang042.github.io/Production-Order-Create/Warp-Knitting/)

## 📋 流程背景

经编常规工单涉及从胚布采购到成品产出的完整生产链路。根据胚布处理方式的不同，分为两种生产路径：
- **路径A（G单模式）**：先创建G单做除油定胚，完工后转入半成品仓，再创建生产工单进行成品生产。
- **路径B（工单直接生产模式）**：直接创建生产工单，工艺路线中保留除油定胚工序，按工序顺序生产直至产出成品。

本指引旨在规范经编常规工单的开单操作，确保数据准确性与流程一致性。

## ✨ 核心流程（7步详解）

### 一、经编单运作流程介绍

**PCTL 创建备胚单** → TOPT 采购胚布，收货入 `1054` 仓（原胚·未除油定胚）→ 此后分两种处理路径：

- **路径A（G单模式）**：TOPT 创建 **G单** 做除油定胚 → 完工后收货入 `1055` 仓（半成品·已除油定胚）→ 再创建生产工单，配置 `1055` 仓胚布进行后续成品生产。
- **路径B（工单直接生产模式）**：TOPT 创建生产工单，配置 `1054` 仓胚布（工艺路线中保留除油定胚工序）→ 按工序顺序生产，直接产出成品。

### 第二步：MRP 产生成品计划单

TOPT 经编销售订单进入 APO 系统后，MRP 产生成品计划单。
- **功能代码**：`/SAPAPO/RRP3`

### 第三步：染厂计划员分缸

染厂计划员分缸（TE_TGWARP），产生已固定的成品计划单（写入染工作中心组，水比，分缸备注信息）。
- **功能代码**：`ZTRIM_XS___START`

### 第四步：计划单转工单

将分缸后的成品计划单转成染整印工单。
- **功能代码**：`/SAPAPO/RRP3` 或 `/SAPAPO/RRP4`

### 第五步：胚布库存查询

经编胚布库存查询功能 `ZSOHPP155`，了解胚布的情况（O方结果，K方结果）。

### 第六步：编辑工单 · 锁胚

操作功能代码：`ZSOHPP159`

本步骤包含3个子操作：
- **操作1**：删除不需要的工序（配置 `1054` 仓的胚布保留所有生产工序）
- **操作2**：双击工单号码，进入 Components（工单元件）界面，进行锁胚
- **操作3**：将胚布的 G 单信息写入长文

### 第七步：审单 · 报工 · 发单

审单、报工、发单。
- **功能代码**：`ZSOHPP163`

> ✅ 经编常规工单开单流程完结。

## 🛠️ 技术工具

- **SAP系统**：多个定制功能代码（/SAPAPO/RRP3、ZTRIM_XS___START、/SAPAPO/RRP4、ZSOHPP155、ZSOHPP159、ZSOHPP163）
- **前端技术**：HTML/CSS/JavaScript 构建响应式操作指引页面，支持深色模式、图片放大预览、步骤导航等交互功能

## 🚀 快速开始

直接访问在线演示地址即可浏览完整的经编常规工单开单流程：
[https://liuyang042.github.io/Production-Order-Create/Warp-Knitting/](https://liuyang042.github.io/Production-Order-Create/Warp-Knitting/)
