---
title: "llm-wiki"
source: "https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f"
author:
  - "[[262588213843476]]"
published:
created: 2026-07-24
description: "llm-wiki. GitHub Gist: instantly share code, notes, and snippets."
tags:
  - "clippings"
---
## LLM Wiki LLM 维基

A pattern for building personal knowledge bases using LLMs.使用大语言模型构建个人知识库的模式。

This is an idea file, it is designed to be copy pasted to your own LLM Agent (e.g. OpenAI Codex, Claude Code, OpenCode / Pi, or etc.). Its goal is to communicate the high level idea, but your agent will build out the specifics in collaboration with you.这是一个创意文件，旨在复制粘贴到您自己的LLM代理（例如OpenAI Codex、Claude Code、OpenCode / Pi等）中。其目的是传达高层次的思路，具体细节将由您的代理与您共同完成。

## The core idea 核心概念

Most people's experience with LLMs and documents looks like RAG: you upload a collection of files, the LLM retrieves relevant chunks at query time, and generates an answer. This works, but the LLM is rediscovering knowledge from scratch on every question. There's no accumulation. Ask a subtle question that requires synthesizing five documents, and the LLM has to find and piece together the relevant fragments every time. Nothing is built up. NotebookLM, ChatGPT file uploads, and most RAG systems work this way.大多数人在使用大语言模型（LLM）和文档时，体验类似于RAG：上传一组文件，LLM在查询时检索出相关片段，并生成回答。这种方式确实有效，但LLM每次回答问题时都在从零开始重新发现知识，没有知识的累积。如果提出一个需要综合五篇文档的复杂问题，LLM就必须每次都找到并拼接相关的片段。没有任何知识被积累起来。NotebookLM、ChatGPT的文件上传以及大多数RAG系统都是这样运作的。

The idea here is different. Instead of just retrieving from raw documents at query time, the LLM **incrementally builds and maintains a persistent wiki** — a structured, interlinked collection of markdown files that sits between you and the raw sources. When you add a new source, the LLM doesn't just index it for later retrieval. It reads it, extracts the key information, and integrates it into the existing wiki — updating entity pages, revising topic summaries, noting where new data contradicts old claims, strengthening or challenging the evolving synthesis. The knowledge is compiled once and then *kept current*, not re-derived on every query.这里的思路有所不同。与在查询时仅从原始文档中检索信息不同，大语言模型会逐步构建并维护一个持久的维基——一个结构化、相互链接的Markdown文件集合，位于你和原始资料之间。当你添加新的资料时，大语言模型不会仅仅将其索引以备后续调用。它会读取内容，提取关键信息，并将其整合到现有的维基中——更新实体页面，修订主题摘要，指出新数据与旧说法之间的矛盾之处，从而强化或挑战不断演进的知识综合。这些知识一旦被编译完成，便保持最新状态，而非每次查询时都重新推导。

This is the key difference: **the wiki is a persistent, compounding artifact.** The cross-references are already there. The contradictions have already been flagged. The synthesis already reflects everything you've read. The wiki keeps getting richer with every source you add and every question you ask.关键区别在于：维基是一个持续积累、不断扩展的产物。交叉引用早已存在，矛盾之处也已被标注，综合内容已经反映了你所阅读的一切。随着你添加更多资料和提出更多问题，维基会不断变得丰富起来。

You never (or rarely) write the wiki yourself — the LLM writes and maintains all of it. You're in charge of sourcing, exploration, and asking the right questions. The LLM does all the grunt work — the summarizing, cross-referencing, filing, and bookkeeping that makes a knowledge base actually useful over time. In practice, I have the LLM agent open on one side and Obsidian open on the other. The LLM makes edits based on our conversation, and I browse the results in real time — following links, checking the graph view, reading the updated pages. Obsidian is the IDE; the LLM is the programmer; the wiki is the codebase.你从不（或很少）亲自编写维基内容——所有内容均由LLM撰写和维护。你负责信息的收集、探索以及提出恰当的问题。LLM则承担全部基础工作，包括总结、交叉引用、归档和记录，这些都让知识库随着时间推移真正变得有用。实际上，我一边打开LLM代理，另一边打开Obsidian。LLM根据我们的对话进行编辑，而我则实时浏览结果——点击链接、查看图表视图、阅读更新后的页面。Obsidian是IDE，LLM是程序员，维基就是代码库。

This can apply to a lot of different contexts. A few examples:这可以适用于许多不同的情况。几个例子：

- **Personal**: tracking your own goals, health, psychology, self-improvement — filing journal entries, articles, podcast notes, and building up a structured picture of yourself over time.个人：追踪自己的目标、健康、心理状态和自我提升——记录日记、文章、播客笔记，并随着时间推移逐步构建起清晰的自我画像。
- **Research**: going deep on a topic over weeks or months — reading papers, articles, reports, and incrementally building a comprehensive wiki with an evolving thesis.研究：在数周或数月内深入探讨某一主题——阅读论文、文章和报告，并逐步构建一个内容全面的维基，同时不断推进自己的论点。
- **Reading a book**: filing each chapter as you go, building out pages for characters, themes, plot threads, and how they connect. By the end you have a rich companion wiki. Think of fan wikis like [Tolkien Gateway](https://tolkiengateway.net/wiki/Main_Page) — thousands of interlinked pages covering characters, places, events, languages, built by a community of volunteers over years. You could build something like that personally as you read, with the LLM doing all the cross-referencing and maintenance.阅读一本书时，可以边读边整理每一章内容，为人物、主题、情节线索及其关联关系逐步扩充页面。最终你将拥有一个内容丰富的配套维基。可以将粉丝维基比作托尔金门户（Tolkien Gateway）——由志愿者社区多年积累，构建出成千上万相互链接的页面，涵盖人物、地点、事件和语言等信息。你可以像这样在阅读过程中亲自创建类似的维基，而LLM则负责所有交叉引用和维护工作。
- **Business/team**: an internal wiki maintained by LLMs, fed by Slack threads, meeting transcripts, project documents, customer calls. Possibly with humans in the loop reviewing updates. The wiki stays current because the LLM does the maintenance that no one on the team wants to do.业务/团队：由LLM维护的内部维基，内容来自Slack讨论、会议记录、项目文档和客户通话。可能还包含人工参与更新审核环节。该维基始终保持最新，因为LLM负责维护工作，而团队中没有人愿意主动承担这项任务。
- **Competitive analysis, due diligence, trip planning, course notes, hobby deep-dives** — anything where you're accumulating knowledge over time and want it organized rather than scattered.竞争分析、尽职调查、行程规划、课程笔记、兴趣深入研究——任何你长期积累知识并希望系统整理而非零散散乱的内容。

## Architecture 架构

There are three layers: 有三层：

**Raw sources** — your curated collection of source documents. Articles, papers, images, data files. These are immutable — the LLM reads from them but never modifies them. This is your source of truth.原始资料——您精心整理的源文件集合。包括文章、论文、图片和数据文件。这些内容不可更改——LLM 会从中读取，但不会修改。这是您的真实来源。

**The wiki** — a directory of LLM-generated markdown files. Summaries, entity pages, concept pages, comparisons, an overview, a synthesis. The LLM owns this layer entirely. It creates pages, updates them when new sources arrive, maintains cross-references, and keeps everything consistent. You read it; the LLM writes it.维基——一个由LLM生成的Markdown文件目录。包含摘要、实体页面、概念页面、对比分析、概览以及综合总结。该层级完全由LLM负责，它创建页面、在新资料出现时更新内容、维护交叉引用，并确保所有信息保持一致。你阅读它，LLM撰写它。

**The schema** — a document (e.g. CLAUDE.md for Claude Code or AGENTS.md for Codex) that tells the LLM how the wiki is structured, what the conventions are, and what workflows to follow when ingesting sources, answering questions, or maintaining the wiki. This is the key configuration file — it's what makes the LLM a disciplined wiki maintainer rather than a generic chatbot. You and the LLM co-evolve this over time as you figure out what works for your domain.架构文件——即一份文档（例如 Claude Code 使用 CLAUDE.md，Codex 使用 AGENTS.md），用于告知大语言模型（LLM）维基的结构、规范以及在导入内容、回答问题或维护维基时应遵循的工作流程。这是关键的配置文件，它使 LLM 成为一个有条理的维基维护者，而非一个通用的聊天机器人。随着时间推移，你和 LLM 会共同演化这一文件，以确定最适合你们特定领域的方案。

## Operations 运营

**Ingest.** You drop a new source into the raw collection and tell the LLM to process it. An example flow: the LLM reads the source, discusses key takeaways with you, writes a summary page in the wiki, updates the index, updates relevant entity and concept pages across the wiki, and appends an entry to the log. A single source might touch 10-15 wiki pages. Personally I prefer to ingest sources one at a time and stay involved — I read the summaries, check the updates, and guide the LLM on what to emphasize. But you could also batch-ingest many sources at once with less supervision. It's up to you to develop the workflow that fits your style and document it in the schema for future sessions.导入。你将一个新资料源添加到原始集合中，并告知大语言模型（LLM）进行处理。例如流程如下：LLM 阅读该资料，与你讨论关键要点，在维基上撰写摘要页面，更新索引，同步修改维基中的相关实体和概念页面，并在日志中新增一条记录。单个资料可能涉及 10 到 15 个维基页面。我个人更倾向于逐个导入资料并持续参与——我阅读摘要、核对更新内容，并指导 LLM 关注哪些重点。但你也可以一次性批量导入多个资料，减少监督。你可以根据自己的工作习惯制定合适的流程，并在后续会话中将其记录于模板中以供参考。

**Query.** You ask questions against the wiki. The LLM searches for relevant pages, reads them, and synthesizes an answer with citations. Answers can take different forms depending on the question — a markdown page, a comparison table, a slide deck (Marp), a chart (matplotlib), a canvas. The important insight: **good answers can be filed back into the wiki as new pages.** A comparison you asked for, an analysis, a connection you discovered — these are valuable and shouldn't disappear into chat history. This way your explorations compound in the knowledge base just like ingested sources do.查询。你向维基提出问题。LLM 会搜索相关页面，阅读内容，并结合引用信息综合出答案。根据问题的不同，答案可以呈现多种形式——如 Markdown 页面、对比表格、幻灯片（Marp）、图表（matplotlib）或画布。关键在于：优质回答可以重新归档为维基的新页面。你提出的比较、分析结果或发现的关联，这些都极具价值，不应消失在聊天记录中。这样一来，你的探索成果就像吸收的资料一样，不断累积进知识库之中。

**Lint.** Periodically, ask the LLM to health-check the wiki. Look for: contradictions between pages, stale claims that newer sources have superseded, orphan pages with no inbound links, important concepts mentioned but lacking their own page, missing cross-references, data gaps that could be filled with a web search. The LLM is good at suggesting new questions to investigate and new sources to look for. This keeps the wiki healthy as it grows.定期请LLM对维基进行健康检查，查找以下问题：页面之间的矛盾、已被新来源取代的过时声明、没有外部链接的孤岛页面、重要概念虽被提及但缺乏独立页面、缺失的交叉引用，以及可通过网络搜索填补的数据空白。LLM擅长提出新的调查问题和新的资料来源，这有助于维基在不断扩展的同时保持健康状态。

## Indexing and logging 索引和日志

Two special files help the LLM (and you) navigate the wiki as it grows. They serve different purposes:两个特殊文件帮助LLM（以及你）在维基不断扩展的过程中进行导航。它们各具不同的用途：

**index.md** is content-oriented. It's a catalog of everything in the wiki — each page listed with a link, a one-line summary, and optionally metadata like date or source count. Organized by category (entities, concepts, sources, etc.). The LLM updates it on every ingest. When answering a query, the LLM reads the index first to find relevant pages, then drills into them. This works surprisingly well at moderate scale (~100 sources, ~hundreds of pages) and avoids the need for embedding-based RAG infrastructure.index.md 是以内容为导向的，它是一个维基中所有内容的目录——每一页都列有链接、一行摘要，以及可选的元数据（如日期或来源数量）。内容按类别组织（实体、概念、来源等）。LLM 在每次数据导入时都会更新该索引。当回答查询时，LLM 首先读取索引以找到相关页面，然后深入这些页面进行分析。这种方法在中等规模（约100个来源，数百页）下表现得相当出色，并且无需依赖嵌入式 RAG 基础架构。

**log.md** is chronological. It's an append-only record of what happened and when — ingests, queries, lint passes. A useful tip: if each entry starts with a consistent prefix (e.g. `## [2026-04-02] ingest | Article Title`), the log becomes parseable with simple unix tools — `grep "^## \[" log.md | tail -5` gives you the last 5 entries. The log gives you a timeline of the wiki's evolution and helps the LLM understand what's been done recently.log.md 是按时间顺序记录的，仅支持追加式记录事件及其发生的时间——包括数据导入、查询和代码清理等操作。一个实用小技巧：如果每条记录都以一致的前缀开头（例如 ## \[2026-04-02\] import | 文章标题），那么就可以使用简单的 Unix 工具解析日志——比如用 grep “^## \\\[” log.md | tail -5 可以获取最近五条记录。该日志提供了维基发展的时间线，有助于大语言模型了解近期的操作内容。

## Optional: CLI tools 可选：命令行工具

At some point you may want to build small tools that help the LLM operate on the wiki more efficiently. A search engine over the wiki pages is the most obvious one — at small scale the index file is enough, but as the wiki grows you want proper search. [qmd](https://github.com/tobi/qmd) is a good option: it's a local search engine for markdown files with hybrid BM25/vector search and LLM re-ranking, all on-device. It has both a CLI (so the LLM can shell out to it) and an MCP server (so the LLM can use it as a native tool). You could also build something simpler yourself — the LLM can help you vibe-code a naive search script as the need arises.在某个时候，你可能希望开发一些小工具，以帮助大语言模型（LLM）更高效地操作维基。维基页面的搜索引擎是最明显的选择——在小规模下，索引文件就足够了，但随着维基规模扩大，就需要更完善的搜索功能。qmd 是一个不错的选择：它是一个本地化的 Markdown 文件搜索引擎，结合了混合的 BM25/向量搜索和 LLM 重排序，所有操作都在设备端完成。它既提供命令行界面（CLI），允许 LLM 调用其执行任务，也提供 MCP 服务器，让 LLM 可以直接将其作为原生工具使用。你也可以自行构建一个更简单的工具——当需要时，LLM 可以帮你快速生成一个朴素的搜索脚本。

## Tips and tricks 技巧与窍门

- **Obsidian Web Clipper** is a browser extension that converts web articles to markdown. Very useful for quickly getting sources into your raw collection.Obsidian Web Clipper 是一款浏览器扩展程序，可将网页文章转换为 Markdown 格式，非常便于快速将资料添加到你的原始收藏中。
- **Download images locally.** In Obsidian Settings → Files and links, set "Attachment folder path" to a fixed directory (e.g. `raw/assets/`). Then in Settings → Hotkeys, search for "Download" to find "Download attachments for current file" and bind it to a hotkey (e.g. Ctrl+Shift+D). After clipping an article, hit the hotkey and all images get downloaded to local disk. This is optional but useful — it lets the LLM view and reference images directly instead of relying on URLs that may break. Note that LLMs can't natively read markdown with inline images in one pass — the workaround is to have the LLM read the text first, then view some or all of the referenced images separately to gain additional context. It's a bit clunky but works well enough.本地下载图片。在 Obsidian 的设置中，进入“文件和链接”选项，将“附件文件夹路径”设为一个固定目录（例如 raw/assets/）。然后进入“设置”→“快捷键”，搜索“Download”以找到“为当前文件下载附件”，并将其绑定到一个快捷键（例如 Ctrl+Shift+D）。剪切文章后，按下该快捷键，所有图片就会被下载到本地磁盘。此功能虽非必需但非常实用——它能让大语言模型直接查看和引用图片，而无需依赖可能失效的 URL。请注意，大语言模型无法原生一次性读取包含内联图片的 Markdown 文件，因此需要采取绕过方式：先让模型读取文本内容，再单独查看部分或全部引用的图片以获取更多上下文信息。虽然略显繁琐，但效果良好。
- **Obsidian's graph view** is the best way to see the shape of your wiki — what's connected to what, which pages are hubs, which are orphans.Obsidian 的图表视图是查看你的维基结构的最佳方式——可以清楚地看到哪些页面相互关联，哪些是中心节点，哪些是孤立页面。
- **Marp** is a markdown-based slide deck format. Obsidian has a plugin for it. Useful for generating presentations directly from wiki content.Marp 是一种基于 Markdown 的幻灯片演示格式，Obsidian 为此提供了插件，可用于直接从维基内容生成演示文稿。
- **Dataview** is an Obsidian plugin that runs queries over page frontmatter. If your LLM adds YAML frontmatter to wiki pages (tags, dates, source counts), Dataview can generate dynamic tables and lists.Dataview 是一个 Obsidian 插件，可对页面前端信息执行查询。如果您的大语言模型为维基页面添加了 YAML 前端信息（如标签、日期、来源数量），Dataview 就可以生成动态表格和列表。
- The wiki is just a git repo of markdown files. You get version history, branching, and collaboration for free.该维基只是一个包含 Markdown 文件的 Git 仓库，您可以免费获得版本历史、分支管理和协作功能。

## Why this works 为什么这样工作

The tedious part of maintaining a knowledge base is not the reading or the thinking — it's the bookkeeping. Updating cross-references, keeping summaries current, noting when new data contradicts old claims, maintaining consistency across dozens of pages. Humans abandon wikis because the maintenance burden grows faster than the value. LLMs don't get bored, don't forget to update a cross-reference, and can touch 15 files in one pass. The wiki stays maintained because the cost of maintenance is near zero.维护知识库最令人厌烦的部分并非阅读或思考，而是记录工作——更新交叉引用、保持摘要的时效性、注意新数据与旧说法之间的矛盾，并确保数十页内容的一致性。人类会放弃维基，因为维护负担增长得比其价值更快。而大语言模型不会感到厌倦，不会忘记更新交叉引用，一次可同时处理15个文件。由于维护成本几乎为零，维基得以持续维护。

The human's job is to curate sources, direct the analysis, ask good questions, and think about what it all means. The LLM's job is everything else.人类的任务是筛选信息、指导分析、提出好问题，并思考这一切的含义。而LLM的任务则是其他一切。

The idea is related in spirit to Vannevar Bush's Memex (1945) — a personal, curated knowledge store with associative trails between documents. Bush's vision was closer to this than to what the web became: private, actively curated, with the connections between documents as valuable as the documents themselves. The part he couldn't solve was who does the maintenance. The LLM handles that.这一理念在精神上与范纳瓦·布什的“记忆存档”（Memex，1945年）相关——一个个人化的知识库，文档之间通过关联路径相互连接。布什的构想更接近这种模式，而非后来的网络：私密、主动维护，文档之间的联系价值不亚于文档本身。他无法解决的问题是维护者是谁，而LLM则负责处理这一点。

## Note 注意

This document is intentionally abstract. It describes the idea, not a specific implementation. The exact directory structure, the schema conventions, the page formats, the tooling — all of that will depend on your domain, your preferences, and your LLM of choice. Everything mentioned above is optional and modular — pick what's useful, ignore what isn't. For example: your sources might be text-only, so you don't need image handling at all. Your wiki might be small enough that the index file is all you need, no search engine required. You might not care about slide decks and just want markdown pages. You might want a completely different set of output formats. The right way to use this is to share it with your LLM agent and work together to instantiate a version that fits your needs. The document's only job is to communicate the pattern. Your LLM can figure out the rest.本文档旨在抽象化，描述的是理念而非具体实现。确切的目录结构、数据模型规范、页面格式以及工具支持等，都将取决于你的领域、个人偏好以及所选的大语言模型（LLM）。上述所有内容均为可选且模块化设计——你可以选择有用的部分，忽略不相关的部分。例如：如果你的资料仅包含纯文本，那么完全不需要图像处理功能，你的维基规模较小，仅需索引文件即可，无需搜索引擎，你可能并不关心幻灯片演示，只想使用 Markdown 页面，或者你希望采用完全不同的输出格式。正确的方式是将此文档与你的 LLM 代理共享，并共同协作构建出符合你需求的版本。本文档唯一的作用是传达模式，其余部分由你的 LLM 自行完成。