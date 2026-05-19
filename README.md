# 🛡️ Awesome AI Agent Cost Control

> A curated list of tools, frameworks, guides, and resources for managing and reducing AI agent costs in production.

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)
[![MIT License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)

AI agents in production can silently drain budgets through retry loops, model escalation, context window bloat, and uncontrolled tool chains. This list collects the best resources for keeping agent costs under control.

## Contents

- [Cost Control Libraries](#cost-control-libraries)
- [Model Pricing Comparison](#model-pricing-comparison)
- [Observability & Monitoring](#observability--monitoring)
- [Guides & Articles](#guides--articles)
- [Cost Calculators](#cost-calculators)
- [Best Practices](#best-practices)

## Cost Control Libraries

| Tool | Language | Description | Stars |
|------|----------|-------------|-------|
| [TokenFence](https://tokenfence.dev) | Python, Node.js | Per-workflow budget caps, auto model downgrade, kill switch for AI agents | [![GitHub](https://img.shields.io/badge/pip-tokenfence-blue)](https://pypi.org/project/tokenfence/) |
| [LiteLLM](https://github.com/BerriAI/litellm) | Python | Unified API + budget management for 100+ LLM providers | ![GitHub stars](https://img.shields.io/github/stars/BerriAI/litellm) |
| [Portkey](https://github.com/Portkey-AI/gateway) | TypeScript | AI gateway with budget limits and routing | ![GitHub stars](https://img.shields.io/github/stars/Portkey-AI/gateway) |
| [Helicone](https://github.com/Helicone/helicone) | TypeScript | LLM observability with cost tracking | ![GitHub stars](https://img.shields.io/github/stars/Helicone/helicone) |
| [LangFuse](https://github.com/langfuse/langfuse) | TypeScript | Open source LLM observability, cost tracking, evaluation | ![GitHub stars](https://img.shields.io/github/stars/langfuse/langfuse) |

## Model Pricing Comparison

| Provider | Input (per 1M tokens) | Output (per 1M tokens) | Notes |
|----------|----------------------|------------------------|-------|
| GPT-4o | $2.50 | $10.00 | Best all-around |
| GPT-4o-mini | $0.15 | $0.60 | 94% cheaper for simple tasks |
| Claude Sonnet 4 | $3.00 | $15.00 | Strong on code |
| Claude Haiku 3.5 | $0.80 | $4.00 | Fast, cheap |
| Gemini 2.5 Flash | $0.15 | $0.60 | Google's budget option |
| DeepSeek V3 | $0.27 | $1.10 | Open-source friendly |

*Prices as of March 2026. Check provider pages for current rates.*

## Observability & Monitoring

- **[agenttrace](https://github.com/luoyuctl/agenttrace)** — Local-first TUI and CLI for AI coding-agent cost, token, latency, and failure regression reports
- **[LangSmith](https://smith.langchain.com/)** — LangChain's observability platform with cost tracking
- **[Langfuse](https://langfuse.com/)** — Open-source LLM observability with per-trace cost attribution
- **[Helicone](https://helicone.ai/)** — LLM proxy with cost analytics and caching
- **[Datadog LLM Observability](https://www.datadoghq.com/product/llm-observability/)** — Enterprise LLM monitoring
- **[Weights & Biases](https://wandb.ai/)** — ML experiment tracking with LLM support

## Guides & Articles

### Budget & Cost Control
- [AI Agent Budget Guardrails: The Production Checklist](https://tokenfence.dev/blog/ai-agent-budget-guardrails-production-checklist)
- [AI Agent Cost Optimization Checklist 2026](https://tokenfence.dev/blog/ai-agent-cost-optimization-checklist-2026)
- [AI Agent Cost Benchmarks 2026: Real Numbers](https://tokenfence.dev/blog/ai-agent-cost-benchmarks-2026-real-numbers)
- [Cost-Per-Task Tracking: The Metric That Saves $50K/Year](https://tokenfence.dev/blog/ai-agent-cost-per-task-tracking-guide)

### Common Cost Problems
- [AI Agent Retry Storms: $2 Becomes $200](https://tokenfence.dev/blog/ai-agent-retry-storms-cost-explosion)
- [Context Window Cost Trap](https://tokenfence.dev/blog/ai-agent-context-window-cost-optimization)
- [RAG Pipeline Cost Explosion](https://tokenfence.dev/blog/rag-pipeline-cost-control-budget-optimization)
- [Error Handling: Silent Failures Drain Your Budget](https://tokenfence.dev/blog/ai-agent-error-handling-cost-silent-failures)

### Security & Cost
- [Prompt Injection Attacks Are Draining Your AI Budget](https://tokenfence.dev/blog/ai-agent-prompt-injection-cost-attack)

### Framework-Specific
- [LangChain & CrewAI Cost Control](https://tokenfence.dev/blog/langchain-crewai-cost-control-budget-limits)
- [GPT-5 Agent Cost Overruns Prevention](https://tokenfence.dev/blog/gpt-5-agent-cost-overruns-prevention-guide)

## Cost Calculators

- **[OpenAI Tokenizer](https://platform.openai.com/tokenizer)** — Count tokens before they cost you money
- **[LLM Price Check](https://llmpricecheck.com/)** — Compare prices across providers
- **[Tokencost](https://github.com/AgentOps-AI/tokencost)** — Python library to estimate token costs

## Best Practices

### The 5-Layer Cost Defense

1. **Per-request budget caps** — Every API call has a dollar limit
2. **Auto model downgrade** — Switch GPT-4o → GPT-4o-mini when budget runs low
3. **Kill switch** — Hard stop when budget is exhausted
4. **Tool call depth limits** — Cap recursive/loop patterns
5. **Cost anomaly alerting** — Flag requests that exceed 3x median cost

### Quick Wins (Day 1)

- Add `max_tokens` to every API call
- Set per-workflow budget limits (even generous ones)
- Log token usage for every request
- Separate dev/staging/production budgets

### Architecture (Week 1)

- Implement tiered model routing (simple tasks → cheap models)
- Add caching for repeated queries
- Use streaming to enable early termination
- Pin model selection in config, not in user-influenceable prompts

---

## Contributing

Pull requests welcome! Please keep entries in alphabetical order within categories.

## License

MIT
