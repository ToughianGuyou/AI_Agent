# Vault Schema

这是 ToughianGuyou 的个人知识库，采用 llm-wiki 模式：LLM 负责写和维护，人类负责策源和提问。

## 目录约定

| 目录 | 用途 | 谁写 |
|------|------|------|
| `Clippings/` | 原始剪藏，不可修改 | 人类（Web Clipper） |
| `topics/` | 加工后的主题笔记 | LLM |

## 链接格式

- 内部链接使用 `[[wiki-link]]` 格式
- Clippings 中的人名引用使用数字 ID（如 `[[262588213843476]]`），保留原始格式即可

## Ingest 流程

当用户要求 ingest 一篇 Clippings 中的文章时：

1. 阅读该 Clippings 原文
2. 提炼 3-5 个关键要点，和用户讨论
3. 根据讨论结果，在 `topics/` 下创建或更新相关主题页面
4. 一个 source 通常只触达 1-3 个主题页（不追求大量碎页）

## Frontmatter 约定

```yaml
---
tags:
  - tag-name
created: YYYY-MM-DD
---
```

- `tags`: 用于分类，保持标签扁平（尽量复用已有标签）
- `created`: 创建日期

## 核心原则

- 笔记宁少勿碎。一个扎实的主题页 > 十个互相链接的碎片
- 结构从内容中生长。不要预先搭建空壳
- 每次 query 的好答案，考虑归档回 `topics/`
