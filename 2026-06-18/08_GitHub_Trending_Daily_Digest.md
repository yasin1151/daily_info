
## GitHub Trending 今日 AI / Agent / 开发工具精选

本次扫描发现 15 个未读新项目，已筛选出与 AI、Agent、LLM、开发工具、MLOps、数据工程相关的高价值项目，并已标记本批内容为已读。

## 1. codebase-memory-mcp：给 AI 编程助手用的代码库长期记忆 MCP

**项目简介：** 高性能代码智能 MCP Server，可把代码库索引成持久化知识图谱，支持 158 种语言、亚毫秒级查询，并声称能减少 99% token 消耗。  
**为什么值得关注：** 这是典型的“Agent 基础设施”项目：把代码理解从一次性上下文窗口，推进到可复用的代码库记忆层。对 Claude Code、Codex、Cursor、Windsurf、Gemini CLI 等 AI 编程工具都很相关，尤其适合大仓库检索、跨文件依赖分析和长期项目上下文维护。  
**Stars：** 5,188（今日新增 718）  
**链接：** https://github.com/DeusData/codebase-memory-mcp

## 2. superpowers：面向软件工程 Agent 的 skills 方法论框架

**项目简介：** 一个 agentic skills framework 与软件开发方法论项目，用 Shell 组织可复用的工程技能与工作流。  
**为什么值得关注：** “Skills”正在成为 AI 编程 Agent 的重要抽象：把一次性的 prompt 经验沉淀为可复用、可组合的操作单元。这个项目的热度很高，说明开发者正在从“让模型临场发挥”转向“给 Agent 配一套工程操作系统”。  
**Stars：** 231,012（今日新增 1,205）  
**链接：** https://github.com/obra/superpowers

## 3. timesfm：Google Research 的时间序列基础模型

**项目简介：** TimesFM 是 Google Research 开源的预训练时间序列基础模型，用于时间序列预测。  
**为什么值得关注：** 时间序列预测正在从传统统计模型、任务专用深度学习模型，走向 foundation model 路线。它对需求预测、金融、运维监控、IoT、供应链和数据工程平台都有潜在价值，也适合作为 MLOps 中“可迁移预测模型”的观察样本。  
**Stars：** 21,864（今日新增 712）  
**链接：** https://github.com/google-research/timesfm

## 4. Continue：开源 AI 编程 Agent

**项目简介：** Continue 是一个开源 coding agent，主打面向开发者的 AI 编程工作流。  
**为什么值得关注：** 在 Cursor、Claude Code、Codex CLI 等工具快速演进的背景下，Continue 仍是开源 AI IDE / coding agent 生态里的关键项目。它适合关注本地模型接入、自定义上下文、企业内网部署和可控 AI 编程基础设施的人持续跟踪。  
**Stars：** 33,880（今日新增 38）  
**链接：** https://github.com/continuedev/continue

## 5. UI-TARS-desktop：字节开源的多模态桌面 Agent 栈

**项目简介：** 开源多模态 AI Agent Stack，连接前沿 AI 模型与 Agent 基础设施，聚焦 GUI Agent、computer use、browser use、MCP、VLM 等方向。  
**为什么值得关注：** 桌面 / 浏览器操作 Agent 是当前 Agent 落地的重要方向。UI-TARS-desktop 覆盖视觉理解、GUI 操作、MCP Server、多模态模型连接等关键层，适合观察“AI 直接操作软件界面”的开源实现路径。  
**Stars：** 36,681（今日新增 148）  
**链接：** https://github.com/bytedance/UI-TARS-desktop

## 6. OpenMontage：Agentic 视频生产系统

**项目简介：** 开源 agentic video production system，包含 12 条流水线、52 个工具、500+ agent skills，目标是把 AI 编程助手变成视频生产工作室。  
**为什么值得关注：** 这个项目把 Agent 工作流从代码生成扩展到多媒体生产：脚本、图像生成、TTS、FFmpeg、Remotion、视频生成等工具链被编排成端到端生产系统。它代表了“Agent + 工具链 + 多模态生成”的实用化方向。  
**Stars：** 5,271（今日新增 71）  
**链接：** https://github.com/calesthio/OpenMontage

## 7. rlm：Recursive Language Models 推理库

**项目简介：** 通用可插拔 Recursive Language Models 推理库，支持多种 sandbox。  
**为什么值得关注：** RLM 关注的是让语言模型在递归推理、沙箱执行和多阶段求解中更可控。虽然项目简介较短，但它切中 LLM 推理增强、工具调用隔离和可组合执行环境这些方向，值得做进一步技术阅读。  
**Stars：** 4,905（今日新增 37）  
**链接：** https://github.com/alexzhang13/rlm

## 8. Nautilus Trader：Rust 原生生产级交易引擎

**项目简介：** 生产级 Rust-native 交易引擎，采用确定性事件驱动架构，覆盖算法交易、加密货币、期权、期货等场景。  
**为什么值得关注：** 虽然不是纯 AI 项目，但其 topics 包含 artificial intelligence 与 machine learning，且交易系统是实时数据工程、回测、事件驱动架构和 ML 策略落地的典型高要求场景。对关注 AI 金融基础设施、低延迟数据管线和生产级 Rust 系统的人值得跟踪。  
**Stars：** 23,795（今日新增 86）  
**链接：** https://github.com/nautechsystems/nautilus_trader

## 9. Chatwoot：开源客服与全渠道会话平台

**项目简介：** 开源 live chat、邮件支持与全渠道客服平台，可作为 Intercom、Zendesk、Salesforce Service Cloud 的替代品。  
**为什么值得关注：** 客服系统是 LLM Agent 最容易落地的业务场景之一。Chatwoot 本身不是 LLM 框架，但它提供了真实会话、工单、渠道集成和运营后台，适合作为企业客服 Agent、RAG 客服、人工接管流程的开源底座。  
**Stars：** 32,354（今日新增 310）  
**链接：** https://github.com/chatwoot/chatwoot

## 10. Plane：开源项目管理平台，可作为 Agent 协作底座

**项目简介：** 开源 Jira / Linear / Monday / ClickUp 替代品，用于管理任务、冲刺、文档与 triage。  
**为什么值得关注：** AI coding agent 要进入团队生产环境，最终需要和 issue、sprint、docs、triage、项目状态流转打通。Plane 作为开源项目管理系统，具备成为 Agent 任务编排与工程管理集成底座的潜力。  
**Stars：** 51,252（今日新增 68）  
**链接：** https://github.com/makeplane/plane
