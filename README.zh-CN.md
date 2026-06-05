<div align="center">

# docker-skills

**Docker containerization skills — Docker, Docker Compose**

[![GitHub](https://img.shields.io/badge/github-full--statck--skills%2Fdocker-skills-green.svg)](https://github.com/full-statck-skills/docker-skills)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-兼容-purple.svg)](https://agentskills.io)

[English](./README.md) | 简体中文

[简介](#-简介) ·
[安装](#-安装) ·
[技能列表](#-技能列表) ·
[支持的智能体](#-支持的智能体) ·
[生态](#-生态)

</div>

---

## 📖 简介

**Docker 技能** 是一组 AI 编码智能体技能，属于 [Full Stack Skills](https://github.com/partme-ai/full-stack-skills) 生态，由 [PartMe.AI](https://github.com/partme-ai) 维护。

本包包含 **16 个技能**。每个技能是一个独立的 `SKILL.md` 文件，AI 智能体按需加载。

## 📦 安装

```bash
npx skills add full-statck-skills/docker-skills
```

或按需安装特定技能：

```bash
npx skills add full-statck-skills/docker-skills --skill <skill-name>
```

## 🎯 技能列表 (16)

| 技能 | 描述 |
|------|------|
| `docker-ai-ml` | Guidance for running AI/ML workloads on Docker. Covers Docker Model Runner (docker model pull/run for local LLMs), Do... |
| `docker-basics` | Docker entry point — provides comprehensive guidance for Docker concepts, architecture, and basic operations. Covers ... |
| `docker-build` | Expert guidance for the `docker build` command — building container images, tagging strategies, build arguments, imag... |
| `docker-buildx` | Expert guidance for Docker image building — docker build CLI, buildx for multi-platform builds, BuildKit features (se... |
| `docker-cicd` | Guidance for integrating Docker into CI/CD pipelines. Covers GitHub Actions (docker/build-push-action, multi-platform... |
| `docker-compose` | Expert guidance for Docker Compose — writing production-grade compose.yml files for multi-container applications. Cov... |
| `docker-dockerfile` | Expert guidance for Dockerfile authoring — the complete reference for writing production-grade Dockerfiles. Covers ev... |
| `docker-hub` | Guidance for Docker image registries — publishing images to Docker Hub, pulling images, tag management strategies, pr... |
| `docker-networking` | Guidance for Docker networking configuration and inter-container communication. Covers network modes (bridge/host/ove... |
| `docker-production` | Guidance for deploying Docker in production environments. Covers Docker Swarm (init, join, stack deploy, service scal... |
| `docker-run` | Guidance for running and managing Docker containers. Covers the complete container lifecycle (create/start/stop/rm/re... |
| `docker-scout` | Guidance for Docker Scout — image vulnerability scanning, SBOM generation, and policy evaluation. Covers scout quickv... |
| `docker-security` | Guidance for Docker security hardening across the full lifecycle — image security (minimal base images, non-root user... |
| `docker-storage` | Guidance for Docker storage and data persistence. Covers storage types (Volume/Bind Mount/Tmpfs) with comparison and ... |
| `docker-testcontainers` | Guidance for Testcontainers — running Docker containers in automated integration tests. Covers Java (@Testcontainers,... |
| `docker-troubleshooting` | Guidance for debugging and troubleshooting Docker issues. Covers container startup failures (exit codes, docker logs,... |

## 🤖 支持的智能体

适用于 [Claude Code](https://code.claude.com)、[Codex](https://developers.openai.com/codex)、[Cursor](https://cursor.com)、[OpenCode](https://opencode.ai)、[Gemini CLI](https://geminicli.com)、[GitHub Copilot](https://github.com/features/copilot)、[Windsurf](https://codeium.com/windsurf) 及 [70+ 其他平台](https://agentskills.io/clients)。

### Claude Code 安装

**方式一：npx skills CLI（推荐）**

```bash
npx skills add full-statck-skills/docker-skills
```

**方式二：手动安装**

```bash
git clone https://github.com/full-statck-skills/docker-skills.git
cp -r docker-skills/skills/* .claude/skills/
```

更多详情请参阅 [Claude Code 技能指南](https://code.claude.com/docs/en/skills) 和 [Agent Skills 规范](https://agentskills.io/)。

## 🌐 生态

| 资源 | 链接 |
|------|------|
| **Full Stack Skills** | [github.com/partme-ai/full-stack-skills](https://github.com/partme-ai/full-stack-skills) |
| **全部技能组** | [github.com/full-statck-skills](https://github.com/full-statck-skills) |
| **Agent Skills 规范** | [agentskills.io](https://agentskills.io) |
| **Skills CLI** | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) |

## 📄 许可证

Apache 2.0 — 详见 [LICENSE](LICENSE)。
