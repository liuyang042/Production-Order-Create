# Production-Order-Create / Recipe-AT

**复方AT单开单流程（Recipe-AT Production Order Creation）**

[![在线演示](https://img.shields.io/badge/在线演示-访问页面-brightgreen)](https://liuyang042.github.io/Production-Order-Create/Recipe-AT/)

## 📖 项目简介

本项目为**复方AT单开单流程**的操作指引与培训教材网站，系统化地展示了从查询AT标记库存数据到创建复方AT单并完成锁胚、报工、发单的完整流程。内容涵盖SAP系统操作、功能代码调用及关键操作步骤，旨在帮助生产、计划及相关部门人员规范、高效地完成复方AT单的创建与跟进。

🔗 **在线演示**: [https://liuyang042.github.io/Production-Order-Create/Recipe-AT/](https://liuyang042.github.io/Production-Order-Create/Recipe-AT/)

## 📋 流程背景

复方AT单是针对特定物料（AT标记）的生产工单类型，涉及从库存查询、数据筛选到工单创建的完整闭环流程。本指引旨在规范复方AT单的开单操作，确保数据准确性与流程一致性。

## ✨ 核心流程

### 第一步：查询AT标记的库存数据

操作代码：`ZSOHWM014`

查询带有AT标记的库存数据，显示物料的仓库库存与批次特性。

**操作参数设置**：
- 物料：`B*` 至（物料范围）
- 工厂：`VN03`
- 储存地点：`1063`
- 用途分类（ATI）


> 💡 操作完成后可将结果添加到日志表，便于后续追溯。

### 第二步：创建复方AT单

操作代码：`ZSOHPP219`

1. 输入 **Sale Group**（销售组）、**Plant**（工厂）、**Material**（物料）后回车
2. 系统自动计算生成 **Generated Order**（生成的工单）
3. 双击工单号码，进入锁胚界面
4. 完成**锁胚** → **报工** → **发单**，开单流程完结

## 🛠️ 技术工具

- **SAP系统**：定制功能代码（ZSOHWM014、ZSOHPP219）
- **前端技术**：HTML/CSS/JavaScript 构建响应式操作指引页面

## 🚀 快速开始

直接访问在线演示地址即可浏览完整的复方AT单开单流程：
[https://liuyang042.github.io/Production-Order-Create/Recipe-AT/](https://liuyang042.github.io/Production-Order-Create/Recipe-AT/)
