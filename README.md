# CodeMind

> 统一 LLM 调用 + Agent 编排内核 + 飞书 IM 桥接 —— 用 Python 搭建的 AI 编程助手内核。

## 项目是做什么的？

**CodeMind** 把多家大模型 API、Agent 主循环（工具调用、会话）、以及飞书消息桥接放在同一套代码里：你用自然语言描述任务，它可以读改代码、执行命令，并通过 CLI 或飞书把结果回给你。

## 技术栈（简要）

Python 3.10+、`asyncio`、`httpx`、可选 `lark-oapi`（飞书）、`pytest`（开发）。

## 快速开始

```bash
python3 --version   # 需 >= 3.10
cd CodeMind
python3 -m venv .venv && source .venv/bin/activate   # Windows: .venv\Scripts\activate

cp .env.example .env
# 编辑 .env，至少填写 ANTHROPIC_API_KEY 或 OPENAI_API_KEY（勿提交 .env）

python -m pip install -U pip setuptools wheel
pip install -e ".[dev]"

python -m coding_agent --mode interactive --provider anthropic --model-id claude-sonnet-4-5
# 或: python examples/quickstart.py
```

飞书 IM 需额外安装 `pip install -e ".[dev,feishu]"` 并在 `.env` 中配置飞书应用凭据；本地可用 `./dev.sh --mode cli` 或 `./dev.sh --mode im`。

```bash
pytest tests/ -v
```
