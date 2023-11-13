```markdown
# ChatGPT Telegram Bot

加入[Telegram 群组](https://t.me/+_01cz9tAkUc1YzZl)聊天，分享您的用户体验或报告 Bug。

[English](./README.md) | [简体中文](./README.zh-CN.md) | [繁體中文](./README.zh-TW.md)

## ✨ 特性

✅ 支持 ChatGPT 和 GPT4 API

✅ 支持使用 duckduckgo 和 Google🔍 进行在线搜索。默认提供 DuckDuckGo 搜索，用户需申请 Google 搜索的官方 API。它可以提供 GPT 以前无法回答的实时信息，例如今日微博热搜，某地今日天气，以及某人或新闻的进展。

✅ 支持基于嵌入式向量数据库的文档问答。在搜索中，对于搜索的 PDF，将执行 PDF 文档的自动向量语义搜索，并基于向量数据库提取与 PDF 相关的内容。支持使用 "qa" 命令将整个网站进行向量化，使用 "sitemap.xml" 文件，并根据向量数据库回答问题，特别适用于某些项目的文档网站和维基网站。

✅ 支持通过聊天窗口中的 "info" 命令在 GPT3.5、GPT4 和其他模型之间切换

✅ 异步处理消息，多线程回答问题，支持隔离对话，不同用户有不同的对话

✅ 支持消息的精确 Markdown 渲染，使用我另一个[项目](https://github.com/yym68686/md2tgmd)

✅ 支持流式输出，实现打字机效果

✅ 支持白名单，防止滥用和信息泄漏

✅ 跨平台，在任何地方都可以通过 Telegram 打破知识障碍

✅ 支持一键 Zeabur、Replit 部署，真正的零成本，白痴化部署，支持 Docker，fly.io 部署

## 环境变量

| 变量名                 | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| **BOT_TOKEN (required)** | Telegram 机器人令牌。在 [BotFather](https://t.me/BotFather) 上创建机器人以获取 BOT_TOKEN。 |
| **WEB_HOOK (required)**  | 每当 Telegram 机器人收到用户消息时，消息将传递到 WEB_HOOK，机器人将监听并及时处理收到的消息。 |
| **API (required)**       | OpenAI 或第三方 API 密钥。                                   |
| API_URL(optional)       | 如果使用 OpenAI 官方 API，则无需设置此项。如果使用第三方 API，则需要填写第三方代理网站。默认值为：https://api.openai.com/v1/chat/completions |
| GPT_ENGINE (optional)    | 设置默认的 QA 模型；默认为：`gpt-3.5-turbo`。此项目可以通过机器人的 "info" 命令自由切换，并且原则上无需设置。 |
| NICK (optional)          | 默认为空，NICK 是机器人的名称。只有当用户输入的消息以 NICK 开头时，机器人才会回应，否则机器人将回应所有消息。特别是在群聊中，如果没有 NICK，则机器人将回复所有消息。 |
| PASS_HISTORY (optional)  | 默认为 true。机器人会记住对话历史，并在下次回复时考虑上下文。如果设置为 false，则机器人将忘记对话历史，仅考虑当前对话。 |
| GOOGLE_API_KEY (optional)| 如果需要使用 Google 搜索，需要设置它。如果不设置此环境变量，机器人将默认提供 duckduckgo 搜索。在 Google Cloud 的 [APIs & Services](https://console.cloud.google.com/apis/api/customsearch.googleapis.com) 中创建凭据，API 密钥将在凭据页面上显示为 GOOGLE_API_KEY。Google 搜索每天最多可查询 100 次，对于轻度使用完全足够。当使用限额达到时，机器人将自动关闭 Google 搜索。 |
| GOOGLE_CSE_ID (optional) | 如果需要使用 Google 搜索，需要与 GOOGLE_API_KEY 一起设置。在 [Programmable Search Engine](https://programmablesearchengine.google.com/) 中创建一个搜索引擎，搜索引擎 ID 是 GOOGLE_CSE_ID 的值。 |
| whitelist (optional)     | 设置哪些用户可以访问机器人，并将授权使用机器人的用户 ID 与 ',' 连接。默认值为 `None`，表示机器人对所有人开放。 |

## Zeabur 远程部署（推荐）

一键部署：

[![在 Zeabur 上部署](https://zeabur.com/button.svg)](https://zeabur.com/templates/R5JY5O?referralCode=yym68686)

如果需要后续功能更新，建议使用以下部署方法：

首先在此仓库中 Fork，然后注册[Zeabur](https://zeabur.com)。免费配额对轻度使用足够。从您自己的 Github 仓库导入，设置域名（必须与 WEB_HOOK 一致）和环境变量，然后重新部署。如果需要后续的功能更新，只需在您自己的仓库中同步此仓库并在 Zeabur 中重新部署，即可获得最新功能。

## Replit 远程部署

[![在 Repl.it 上运行](https://replit.com/badge/github/yym68686/ChatGPT-Telegram-Bot)](https://replit.com/new/github/yym68686/ChatGPT-Telegram-Bot)

导入 Github 仓库后，设置运行命令

```bash
pip install -r requirements.txt > /dev/null && python