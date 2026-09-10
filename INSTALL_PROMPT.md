# 安装提示词（复制粘贴给 AI 即可）

> 文中的仓库地址已替换为 `face2333/moleportal-skills`，可直接使用。

---

## 主推版本 · 公开仓库（推荐发给同事这段）

```
帮我安装「运营周报数据」这个 skill，按下面的步骤做：

1. 运行：
   npx skills add face2333/moleportal-skills --skill moleportal-weekly-mcp -y -g

2. 装完后用这条命令找到它装在哪：
   find ~ -maxdepth 5 -type d -name "moleportal-weekly-mcp" 2>/dev/null

   如果路径不是 ~/.workbuddy/skills/moleportal-weekly-mcp，
   就把生成的 moleportal-weekly-mcp 整个目录复制到 ~/.workbuddy/skills/ 下。

3. 最后告诉我三件事：
   - 技能最终装在哪
   - 我需要在 ~/.workbuddy/mcp.json 里配置 moleportal 的 MCP 地址和 Bearer Token
     （这两个我要去找管理员要，你不要猜）
   - 提醒我改完配置要重启客户端才会生效
```

---

> ⚠️ **前提：对方机器上要有 Node.js ≥ 18**（也就是终端里敲 `npx` 有反应）。
> 没有的话会报 `command not found: npx`。两种处理：
> 1. 让对方去 [nodejs.org](https://nodejs.org) 装一个 LTS 版，装完重开终端即可
> 2. 或者直接用下面的「备选 A · 直链 zip」，那条完全不依赖 Node

## 精简版（对方会用终端时）

```
帮我安装 npx skills add face2333/moleportal-skills --skill moleportal-weekly-mcp -y -g，
然后把生成的 moleportal-weekly-mcp 目录复制到 ~/.workbuddy/skills/ 下。
```

---

## 备选 A · 直链 zip（不想依赖 GitHub 时用）

把技能目录打包成 `moleportal-weekly-mcp.zip` 放到内网或对象存储，然后发这段：

```
帮我安装「运营周报数据」这个 skill：
1. 下载 https://<你的地址>/moleportal-weekly-mcp.zip 到临时目录
2. 解压，把里面的 moleportal-weekly-mcp 目录放到 ~/.workbuddy/skills/ 下
3. 告诉我最终路径，并提醒我需要配置 MCP 地址和 Token（我去找管理员要）
```

> 这条路完全不需要 GitHub 账号，也不需要 skills CLI。缺点是更新要重新装一次。

---

## 备选 B · 本地目录（同一台机器上最快）

```
帮我安装这个 skill：
npx skills add /path/to/moleportal-weekly-mcp-publish/skills/moleportal-weekly-mcp -y -g
装完后复制到 ~/.workbuddy/skills/ 下。
```

---

## 发布者自检清单

推送到公开仓库前，逐项确认：

- [x] 仓库地址已替换为 `face2333/moleportal-skills`
- [ ] 全仓搜不到真实 IP、Token、callerId、security
      ```bash
      grep -rniE "36\.133|bearer [a-f0-9]{16,}|caller[_ -]?id|security=" . || echo "干净"
      ```
- [ ] `references/` 未包含（服务端运维文档，含业务密钥）
- [ ] 没有 `.DS_Store`
- [ ] 自己先跑一遍验证能被发现：
      ```bash
      npx skills add face2333/moleportal-skills --list
      ```
