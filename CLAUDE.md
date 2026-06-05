# docker-skills — CLAUDE.md

Docker containerization Agent Skills, part of the [Full Stack Skills](https://github.com/partme-ai/full-stack-skills) ecosystem maintained by PartMe.AI. Pure Markdown documentation repo — no build, no source code, no tests.

## Skills (16)

| Skill | Summary |
|-------|---------|
| `docker-basics` | Concepts, architecture, container vs VM, first container |
| `docker-dockerfile` | Complete Dockerfile instruction reference and authoring guide |
| `docker-build` | `docker build` command, tagging, build args, layer caching |
| `docker-buildx` | Multi-platform builds, BuildKit, buildx drivers |
| `docker-run` | Container lifecycle: create, start, stop, rm, exec, limits |
| `docker-compose` | Multi-container orchestration, compose.yml authoring |
| `docker-networking` | Network modes (bridge/host/overlay), container communication |
| `docker-storage` | Volumes, bind mounts, tmpfs, data persistence |
| `docker-hub` | Docker Hub, image registries, tag management, publishing |
| `docker-security` | Minimal base images, non-root users, image signing, secrets |
| `docker-scout` | Vulnerability scanning, SBOM generation, policy evaluation |
| `docker-cicd` | GitHub Actions, GitLab CI, multi-platform pipelines |
| `docker-production` | Docker Swarm, production patterns, health checks |
| `docker-troubleshooting` | Debugging: exit codes, logs, exec, dangling resources |
| `docker-testcontainers` | Testcontainers for Java/Go/Node/Python integration tests |
| `docker-ai-ml` | Docker Model Runner, local LLMs, GPU acceleration |

Learning path: `basics → dockerfile → build → buildx → run → networking/storage → compose → security/cicd → production/troubleshooting → ai-ml`

## Directory Structure

```
skills/
  docker-<name>/
    SKILL.md           # Core skill definition (YAML frontmatter + body)
    examples/          # Scenario files (01-name.md, 02-name.md, ...)
    references/        # Reference docs (01-name.md, 02-name.md, ...)
.claude-plugin/
  plugin.json          # Plugin manifest listing all 16 skills
README.md / README.zh-CN.md   # Bilingual project docs
```

## SKILL.md Authoring Conventions

### Frontmatter (every SKILL.md)

```yaml
---
name: docker-<name>
description: <English paragraph describing what the skill covers. Ends with 使用场景：<comma-separated Chinese keywords>.>
license: Apache-2.0
---
```

### Body structure (consistent across all 16 skills)

1. **H1 title** — Bilingual: `# English Title — 中文标题`
2. **When to Use** — Two-column table (`Use When | Skip When`) plus bullet list of trigger keywords
3. **Core content** — Skill-specific title. Tables, code blocks (bash/yaml), ASCII diagrams, CLI output
4. **Workflow — 推荐使用流程** — Numbered steps 1-5 describing recommended learning/implementation path (Chinese)
5. **Gotchas — Common Pitfalls** — Bullet list, each: `<problem>` → `**Recovery**: <solution>`
6. **Boundary — 能力边界** — Three-column table: `✅ 能做` / `⚠️ 需条件` / `❌ 超范围`
7. **When NOT to Use** — Two-column `Skip | Use Instead` table redirecting to appropriate skill
8. **Security & Stability** — Bullet list of security notes and limitations (English)
9. **📚 官方文档参考** — Two-column table linking to docs.docker.com
10. **🧭 Docker Skills Journey** — ASCII art showing position in learning path with Previous/Next links

### Conventions

- **Bilingual**: Titles and section headers mix English and Chinese; code blocks are English only; "Workflow" and "Boundary" sections in Chinese
- **Examples/references numbering**: `01-topic.md`, `02-topic.md` — one scenario/topic per file
- **Code blocks**: Always specify language (`bash`, `yaml`, `dockerfile`)
- **Tables**: Consistently used for comparisons, references, and boundaries
- **Self-contained**: Each SKILL.md is independently loadable by an agent; cross-skill references use backtick-quoted names (`docker-build`)
- **Size target**: SKILL.md files range 135-368 lines; target ~180 lines

## Key Files

| File | Purpose |
|------|---------|
| `.claude-plugin/plugin.json` | Plugin manifest — skill directory paths, metadata, version |
| `README.md` / `README.zh-CN.md` | Bilingual project README with install instructions |
| `LICENSE` | Apache 2.0 (root + copy in `skills/docker-compose/`) |

## Common Tasks

- **Add a new skill**: Create `skills/docker-<name>/` with `SKILL.md`, `examples/`, `references/`; register in `plugin.json`
- **Edit a skill**: Modify `SKILL.md` following the section order above; keep frontmatter `description` in sync
- **Skill discovery**: `npx skills add full-statck-skills/docker-skills` (all) or `--skill <name>` (specific)
