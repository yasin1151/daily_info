
# GitHub Trending 今日 AI/开发工具项目

## 1. Soup：用一份 YAML 微调 LLM
**项目简介：** Soup 是一个 Python LLM 微调工具，主打“从一份 YAML 配置 fine-tune LLM”，支持 LoRA/QLoRA、SFT、DPO、GGUF、Hugging Face、Ollama、本地 LLM 等工作流。项目描述中特别强调 layer streaming，可在 4GB 笔记本 GPU 上训练 8B 模型。  
**为什么值得关注：** 这是很明确的低门槛 LLMOps/本地微调工具，方向贴近消费级 GPU、本地 AI、低显存训练和模型交付。如果它的 layer streaming 路线稳定，可能会降低个人和小团队微调模型的硬件门槛。  
**语言：** Python  
**Stars：** 1,640，总计；今日新增 303  
**链接：** https://github.com/MakazhanAlpamys/Soup

## 2. CLI-Anything：让软件变成 Agent-Native CLI
**项目简介：** CLI-Anything 来自 HKUDS，定位是 “Making ALL Software Agent-Native”，围绕 CLI-Hub 将软件能力包装成更适合 Agent 调用的命令行接口。  
**为什么值得关注：** Agent 真正落地时，最卡的不是模型调用，而是工具接口、状态反馈、错误恢复和可组合执行。这个项目抓的是“软件如何被 Agent 稳定使用”的基础层问题，和未来的 agentic workflow、tool-use benchmark、自动化执行环境都有关。  
**语言：** Python  
**Stars：** 47,335，总计；今日新增 100  
**链接：** https://github.com/HKUDS/CLI-Anything

## 3. public-apis：免费公开 API 目录
**项目简介：** public-apis 是一个长期维护的免费 API 集合，覆盖大量公开数据源和服务接口。  
**为什么值得关注：** 它不是 AI 项目本身，但对 Agent、数据工程、自动化原型和工具型应用很有价值。做数据采集、demo、agent tool registry、评测数据源时，这类公开 API 索引能显著降低找数据源的成本。  
**语言：** Python  
**Stars：** 460,133，总计；今日新增 2,476  
**链接：** https://github.com/public-apis/public-apis

## 4. cordis：时空可组合 Meta-Framework
**项目简介：** cordis 是一个 TypeScript 框架，描述为 “Meta-Framework of Spatiotemporal Composability”，topics 包含 framework、plugin、nodejs、effect。  
**为什么值得关注：** 相关性偏开发框架/插件系统，不是直接 AI 项目。但它的插件化与 effect 风格组合能力，可能适合构建复杂工具链、机器人框架或多模块应用底座，值得作为基础设施观察。  
**语言：** TypeScript  
**Stars：** 4,045，总计；今日新增 616  
**链接：** https://github.com/cordiverse/cordis

已完成：`blogwatcher-cli` 扫描到 4 条新增，已抓取 GitHub Trending 页面和 GitHub API 元数据补全，最后已标记全部已读；复查结果为 `No unread articles!`。
