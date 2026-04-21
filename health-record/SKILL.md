---
name: health-record
description: 适用于健康档案相关操作，包括查询健康档案与创建健康档案。
triggers: 查健康档案、查询健康档案、创建健康档案、新建健康档案、健康档案管理、健康档案
---



# 健康档案操作

根据用户最新输入，判断用户是要**查询健康档案**还是**创建健康档案**，并提取对应操作参数 `operation`。



## 核心执行规则（必须严格遵循）

### 1. 需求分析
- 是否调用技能，只基于**用户最新输入**判断。
- 当前问题属于**健康档案相关操作**时，调用该技能。
- 仅识别两类操作：
  - 查询健康档案 → `search`
  - 创建健康档案 → `create`

### 2. 上下文与记忆融合
- **上下文**仅用于补全省略、指代、续问。
- **记忆**仅用于辅助理解当前意图，不得替代用户当前明确表达。
- 信息优先级：**用户最新输入 > 当前上下文 > 用户记忆**。
- 若用户当前输入已明确表达操作意图，则直接以当前输入为准。



## 输入参数

| 字段名 | 类型 | 必填 | 默认值 | 描述 |
|---|---|---|---|---|
| operation | enum[string] | 是 | — | 健康档案操作类型。仅允许两个取值：`search`、`create`。 |

> **调用前自检规则**：
> 1. `operation` 必须存在，且取值只能为 `search` 或 `create`；
> 2. 所有参数通过长选项传递，禁止使用 stdin 或 JSON；



## 输出命令

示例：
```bash
cd <skill_root> && python scripts/python/health_record.py --operation "search"
```
```bash
cd <skill_root> && python scripts/python/health_record.py --operation "create"
```

>  说明：
> - `cd <skill_root> && python scripts/python/health_record.py` 为前面固定输出内容，后面携带参数；
> - `<skill_root>` 为技能根目录占位符，运行时替换；
> - 仅输出 bash 命令即可