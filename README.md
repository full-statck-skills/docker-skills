<div align="center">

# docker-skills

**Docker containerization skills — Docker, Docker Compose**

[![GitHub](https://img.shields.io/badge/github-full--statck--skills%2Fdocker-skills-green.svg)](https://github.com/full-statck-skills/docker-skills)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Compatible-purple.svg)](https://agentskills.io)

English | [简体中文](./README.zh-CN.md)

[Introduction](#-introduction) ·
[Install](#-install) ·
[Skills](#-skills) ·
[Supported Agents](#-supported-agents) ·
[Ecosystem](#-ecosystem)

</div>

---

## 📖 Introduction

**Docker Skills** is a curated collection of Agent Skills for AI coding agents, part of the [Full Stack Skills](https://github.com/partme-ai/full-stack-skills) ecosystem maintained by [PartMe.AI](https://github.com/partme-ai).

This package includes **16 skills**. Each skill is a self-contained `SKILL.md` file that AI agents load on-demand.

## 📦 Install

```bash
npx skills add full-statck-skills/docker-skills
```

Or install specific skills:

```bash
npx skills add full-statck-skills/docker-skills --skill <skill-name>
```

## 🎯 Skills (16)

| Skill | Description |
|-------|-------------|
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

## 🤖 Supported Agents

Works with [Claude Code](https://code.claude.com), [Codex](https://developers.openai.com/codex), [Cursor](https://cursor.com), [OpenCode](https://opencode.ai), [Gemini CLI](https://geminicli.com), [GitHub Copilot](https://github.com/features/copilot), [Windsurf](https://codeium.com/windsurf), and [70+ others](https://agentskills.io/clients).

### Claude Code Installation

**Option 1: npx skills CLI (Recommended)**

```bash
npx skills add full-statck-skills/docker-skills
```

**Option 2: Manual Installation**

```bash
git clone https://github.com/full-statck-skills/docker-skills.git
cp -r docker-skills/skills/* .claude/skills/
```

For more details, see the [Claude Code Skills Guide](https://code.claude.com/docs/en/skills) and [Agent Skills Spec](https://agentskills.io/).

## 🌐 Ecosystem

| Resource | Link |
|----------|------|
| **Full Stack Skills** | [github.com/partme-ai/full-stack-skills](https://github.com/partme-ai/full-stack-skills) |
| **All Skill Groups** | [github.com/full-statck-skills](https://github.com/full-statck-skills) |
| **Agent Skills Spec** | [agentskills.io](https://agentskills.io) |
| **Skills CLI** | [github.com/vercel-labs/skills](https://github.com/vercel-labs/skills) |

## 📄 License

Apache 2.0 — see [LICENSE](LICENSE).
