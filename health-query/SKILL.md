---
name: health-query
description: 适用于解答常见身体健康资讯问题，如症状、疾病、用药、检查、科室与就医建议。
triggers: 查健康、问症状、疾病咨询、用药咨询、体检指标、挂什么科、怎么治疗、健康问题
---



# 健康资讯解答

根据用户最新输入，原样提取为身体健康相关问题 `query`，用于健康资讯解答。



## 参数传递规则

- `query` 的值必须直接使用**用户当前输入原文**。
- 不得结合上下文、记忆或推断信息对 `query` 内容做任何改写、补全。



## 输入参数

| 字段名 | 类型 | 必填 | 默认值 | 描述 |
|---|---|---|---|---|
| query | string | 是 | — | 用户当前输入原文 |

> **调用前自检规则**：
> 1. `query` 必须存在，且是用户当前输入原文；
> 2. 所有参数通过长选项传递，禁止使用 stdin 或 JSON。



## 输出命令

示例：
```bash
cd <skill_root> && python scripts/python/health_query.py --query "最近胃痛，怎么办？"
```
```bash
cd <skill_root> && python scripts/python/health_query.py --query "我家老人有心脏病史，最近头晕，该挂什么科？"
```

>  说明：
> - `cd <skill_root> && python scripts/python/health_query.py` 为前面固定输出内容，后面携带参数；
> - `<skill_root>` 为技能根目录占位符，运行时替换；
> - 仅输出 bash 命令即可