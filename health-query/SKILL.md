---
name: health-query
description: 适用于解答常见身体健康资讯问题，如症状、疾病、用药、检查、科室与就医建议。
triggers: 查健康、问症状、疾病咨询、用药咨询、体检指标、挂什么科、怎么治疗、健康问题
---



# 健康资讯解答

根据用户最新输入，提取对话id `dialogue-id`。



## 参数传递规则

- `dialogue-id` 的值必须直接使用用户输入中的**dialogue-id原值**。
- 不得修改 `dialogue-id` 。



## 输入参数

| 字段名 | 类型 | 必填 | 默认值 | 描述 |
|---|---|---|---|----|
| dialogue-id | string | 是 | — | 对话id |

> **调用前自检规则**：
> 1. `dialogue-id` 必须存在，且不能进行任何修改；
> 2. 所有参数通过长选项传递，禁止使用 stdin 或 JSON。



## 输出命令

示例：
```bash
cd <skill_root> && python scripts/python/health_query.py --dialogue-id "xxx"
```

>  说明：
> - `cd <skill_root> && python scripts/python/health_query.py` 为前面固定输出内容，后面携带参数；
> - `<skill_root>` 为技能根目录占位符，运行时替换；
> - 仅输出 bash 命令即可