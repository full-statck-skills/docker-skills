---
name: docker-networking
description: Guidance for Docker networking configuration and inter-container communication. Covers network modes (bridge/host/overlay/none/macvlan/ipvlan), custom bridge networks with DNS resolution, port publishing (-p/--publish), container linking and service discovery, network troubleshooting (inspect/ping/nslookup), overlay networks for Swarm, and network security (internal networks, encrypted overlay). Use when the user asks about docker network, container networking, bridge mode, port mapping, inter-container communication, network troubleshooting, or Docker network modes. 使用场景：docker network、容器网络、bridge、overlay、端口映射、容器通信、网络配置、网络排查.
license: Apache-2.0
---

# Docker Networking — 网络配置与容器通信

Comprehensive guidance for Docker networking modes, configuration, and troubleshooting.

## When to Use

**ALWAYS use this skill when the user mentions:**
- "docker network", "容器网络"
- "bridge network", "host network", "overlay network"
- "端口映射", "publish port"
- "容器之间怎么通信", "跨容器通信"
- "网络不通", "network troubleshooting"

## Network Mode Comparison

| Mode | Isolation | Use Case | Cross-Host? |
|------|:--:|------|:--:|
| **bridge** (default) | Container-level | Single-host containers | ❌ |
| **host** | None (share host) | Max performance, no isolation | ❌ |
| **overlay** | Container-level | Swarm multi-host | ✅ |
| **none** | Full | No networking needed | ❌ |
| **macvlan/ipvlan** | MAC/IP-level | Legacy apps needing physical IP | ✅ |

## Custom Bridge Network (Recommended)

```bash
# Create a custom network
docker network create --driver bridge mynet

# Run containers on it
docker run -d --name app1 --network mynet nginx:alpine
docker run -d --name app2 --network mynet nginx:alpine

# DNS resolution works automatically
docker exec app1 ping app2    # ✅ responds
docker exec app1 nslookup app2  # ✅ resolves

# Benefits over default bridge:
# - Automatic DNS resolution
# - Container isolation from default bridge
# - Can connect/disconnect at runtime
```

## Port Publishing

```bash
# Basic port mapping
docker run -p 8080:80 nginx     # host:8080 → container:80
docker run -p 8080              # random host port → container:8080
docker run -P nginx             # publish all EXPOSE'd ports to random host ports

# Multiple ports
docker run -p 8080:80 -p 8443:443 nginx

# Bind to specific interface
docker run -p 127.0.0.1:8080:80 nginx  # only localhost
```

## Service Discovery

```
Custom bridge network provides automatic DNS:

┌──────────────────────────────────┐
│  my-network (bridge)             │
│                                  │
│  ┌──────┐  ┌──────┐  ┌──────┐   │
│  │ app1 │  │ app2 │  │  db  │   │
│  └──┬───┘  └──┬───┘  └──┬───┘   │
│     │         │         │        │
│     └─── DNS: app2 → 172.18.0.3 │
│          DNS: db → 172.18.0.4   │
└──────────────────────────────────┘

app1 can connect to db:5432 directly — no IP needed!
```

## Overlay Network (Swarm)

```bash
# Create overlay for multi-host
docker network create --driver overlay --attachable my-overlay

# In compose:
networks:
  backend:
    driver: overlay
```

## Network Troubleshooting

```bash
# Inspect network details
docker network inspect mynet

# Test connectivity from container
docker exec app1 ping -c 3 app2
docker exec app1 nslookup db
docker exec app1 curl http://app2:8080/health

# Check iptables (host)
sudo iptables -t nat -L DOCKER -n
```

## Workflow — 推荐配置流程

Step 1: **确定需求**: 容器间通信？端口暴露？跨主机？选择网络模式
Step 2: **创建网络**: `docker network create --driver bridge mynet`
Step 3: **启动容器**: `docker run -d --network mynet --name db mysql` + `docker run -d --network mynet --name api myapp`
Step 4: **验证连通性**: `docker exec api ping db`（服务名 DNS 解析）
Step 5: **排查问题**: `docker network inspect mynet` → `docker exec api nslookup db`

## Gotchas — Common Pitfalls

- **Default bridge no DNS**: Containers on the default bridge CANNOT resolve each other by name. → **Recovery**: `docker network create mynet && docker run --network mynet ...`; always use custom bridge networks.
- **Port already in use**: `-p 8080:80` fails if host port 8080 is taken. → **Recovery**: `lsof -i :8080` to find the process; use `-p 8081:80` or `-p 80` for random host port.
- **Mac host networking limitation**: `--network host` on Docker Desktop (Mac) joins the VM's network, not the Mac's. → **Recovery**: Publish ports with `-p` instead of `--network host`.
- **Overlay without Swarm**: Overlay networks only work with Swarm mode. → **Recovery**: `docker swarm init` first, or add `--attachable` flag for standalone containers.
- **EXPOSE does NOT publish**: `EXPOSE` in Dockerfile is documentation only. → **Recovery**: Always use `-p` or Compose `ports:` to actually make ports accessible.

## Boundary — 能力边界（适用与不适用场景）

| 分类 | 场景 | 说明 |
|------|------|------|
| ✅ 能做 | 单机容器网络配置 | bridge/host/none 模式选择 |
| ✅ 能做 | 容器间 DNS 通信 | 自定义 bridge 网络 + 服务名解析 |
| ✅ 能做 | 端口发布 | `-p host:container` 端口映射 |
| ⚠️ 需条件 | 跨主机通信 | 需要 overlay 网络 + Swarm 模式 |
| ⚠️ 需条件 | macOS `--network host` | 行为不同于 Linux，建议用 `-p` 替代 |
| ❌ 超范围 | K8s 网络策略（NetworkPolicy） | 使用 `docker-production` + K8s 文档 |
| ❌ 超范围 | 外部负载均衡（Nginx/HAProxy） | 基础设施层级 |
| ❌ 超范围 | iptables/nftables 精细配置 | Linux 网络管理 |

## When NOT to Use This Skill

| ❌ Skip | ✅ Use Instead |
|---------|---------------|
| Docker basics | `docker-basics` |
| Running containers | `docker-run` |
| Compose networking | `docker-compose` (compose handles network creation automatically) |
| Kubernetes networking | K8s documentation |

## Security & Stability

- Use `--internal` flag for networks that should not have internet access.
- Encrypt overlay network traffic: `--opt encrypted=true`.
- Avoid `--network host` in production — no network isolation.
- No executable scripts bundled. Guidance only.

## 📚 官方文档参考

| 文档 | 地址 |
|------|------|
| Docker 网络概述 | https://docs.docker.com/network/ |
| docker network 命令 | https://docs.docker.com/reference/cli/docker/network/ |
| 网络驱动 | https://docs.docker.com/network/drivers/ |
| Bridge 网络 | https://docs.docker.com/network/bridge/ |
| Overlay 网络 | https://docs.docker.com/network/overlay/ |
| 端口发布 | https://docs.docker.com/network/#published-ports |

## 🧭 Docker Skills Journey

> 📍 **You are here: `docker-networking` — 网络配置**

**← Previous**: `docker-run` | **→ Next**: `docker-compose`

## FAQ

**Q1: 如何快速上手此技能？**
A: 参考上方的快速开始章节，按步骤操作即可。

**Q2: 遇到版本不兼容问题怎么办？**
A: 检查依赖版本，使用 lock 文件锁定，参考常见陷阱章节。

**Q3: 如何在生产环境使用？**
A: 参考最佳实践章节，确保配置正确，做好监控和日志。

**Q4: 性能如何优化？**
A: 参考性能优化相关文档，使用缓存、索引等手段。

**Q5: 如何贡献或反馈问题？**
A: 在 GitHub 仓库提交 Issue 或 Pull Request。

**Q6: 是否支持中文？**
A: 支持中文文档和中文注释，详见国内适配章节。
