<div align="center">

# 📊 PaperPlotHub

**🎨 给所有需要画图的研究者，一个互相借力的画廊。**

🌐 [paperplothub.tech](https://paperplothub.tech) · 🇨🇳 [中文](./README.md) · 📚 [English](./README.en.md)

[![status](https://img.shields.io/badge/status-在线-22c55e?style=flat-square)](https://paperplothub.tech)
[![for](https://img.shields.io/badge/面向-研究者%20%26%20学生-3b82f6?style=flat-square)](#-我们想做的事)
[![contribute](https://img.shields.io/badge/三种贡献方式-FULL%20%7C%20REPRO%20%7C%20PAPER-f97316?style=flat-square)](#%EF%B8%8F-当贡献者)
[![agents](https://img.shields.io/badge/Agent-MCP%20%2B%20REST-a855f7?style=flat-square)](#-给-ai-agent-用)

</div>

---

## 💡 我们想做的事

论文里那张让你眼前一亮的图，背后往往是某个作者熬到凌晨两点才调出来的。我们觉得，这些用心做的图谱，不该只属于一篇论文。

所以我们做了 **PaperPlotHub** —— 一个面向所有研究者的图表分享空间。在这里：

- 🤝 **你可以分享**自己曾经画过、自己骄傲的论文图，连同那段调好的脚本，留给后来人参考。
- 🛠️ **我们也会持续复现**一些高质量论文里值得一看的图表，把脚本附上，放进这个画廊。
- 🌱 **想画图的同学**可以从这些模板里找灵感、复用配色和排版，把精力留给自己的想法和实验，而不是跟 matplotlib 的某个边角参数较劲。

我们的初衷很简单：把"这张图怎么画"的时间还给"我到底想说什么"的思考，让大家能更顺利地把论文写完。 ✍️📈

---

## 🌍 画廊里有什么

每条提交是三件套并排，方便你把"论文里发表的那张"和"在你笔记本上跑出来的那张"对照着看。

| 🖼️ 论文原图 | ✅ 复现图 | 🐍 脚本 |
| :---: | :---: | :---: |
| 从论文里截下来的小图 | 用脚本本地跑出来的图 | 独立、可复制、能跑 |

…再加上 arXiv 链接、图表类型标签（bar / line / heatmap / radar / …）、风格标签、中英双语描述。

每条提交在公开前会过一遍**轻量 AI 审核**：静态安全扫描、arXiv 元数据抓取、视觉 LLM 校验渲染图确实来自这段脚本。我们的标准是 *"这对其他人有用吗？"*，而不是 *"是否像素级还原论文里那张图？"*。 🛡️

---

## 🚀 怎么用这个网站

### 👀 当访客（不用登录）

| 想干啥 | 去哪儿 |
| --- | --- |
| 🏠 浏览最新画廊 | [`/`](https://paperplothub.tech/) |
| 🗂️ 按图表类型筛选 | [`/c/bar`](https://paperplothub.tech/c/bar)、[`/c/line`](https://paperplothub.tech/c/line)、[`/c/heatmap`](https://paperplothub.tech/c/heatmap)…… |
| 🔬 看原图 vs 复现图并排 | `/p/[slug]` |
| 📋 复制脚本 | 详情页绿色 **`copy`** 按钮 |
| 💾 下载渲染好的 PNG | 图片下方 **`download`** 链接 |
| 🌗 切换亮 / 暗 / 跟随系统 | 顶部导航栏的主题按钮 |

> 💁 整个画廊免费看、免费用。如果一段脚本帮你省了一个小时，那就是它存在的意义。

### ✍️ 当贡献者

按你手头有什么，三种贡献方式都同样欢迎 —— **每一条都在帮别人画得更快**。

| 模式 | 你要传啥 | 什么时候用 |
| --- | --- | --- |
| **`FULL`** 🟢 | 论文原图 + 复现图 + 脚本 | 默认款。你看上了一张论文图，自己复现了，脚本也整理过了。 |
| **`REPRO_ONLY`** 🔵 | 复现图 + 脚本 | 你跑了自己的实验、自己的图、自己的脚本，引用了某篇论文的设定。 |
| **`PAPER_ONLY`** 🟠 | 仅论文原图 | 你看到一张值得复现的图，但暂时没空动手。把它丢上来挂个 `🎯 reproduction wanted`，让社区里的人接力。 |

**怎么贡献：**

1. 🔑 在 [`/login`](https://paperplothub.tech/login) 用 GitHub 登录。
2. ⬆️ 进 [`/upload`](https://paperplothub.tech/upload)，先选模式，粘 arXiv 链接或 ID。
3. 📎 按所选模式补齐文件。
4. 🤖 AI 流水线审核。置信度高（≥ 0.85）的自动公开；其余进入人工二审队列。
5. 📈 在 [`/me`](https://paperplothub.tech/me) 看状态；标题 / 标签 / 描述随时可以在 `/me/edit/[slug]` 微调。

> 🛡️ **安全说明：** 任何尝试调 `eval` / `exec`、走外网、或夹带可识别 API key 的脚本会在人看到之前自动拒收。本站**永远不会执行**上传的脚本 —— 你的脚本是给人看的，渲染图是你自己提供的，仅此而已。

---

## 🤖 给 AI Agent 用

现在很多图本来就是 Agent 帮忙画的，所以我们做了两套协议，让 Agent 不用离开对话就能把成果分享回社区。

1. **🛰️ MCP server** —— 直接接进 Claude Desktop / Cursor 等任何支持 MCP 的宿主。
2. **🌐 REST API** —— Bearer token、`multipart/form-data`，对 `curl` 和 CI 友好。

### 🪄 1 分钟接入

```text
1. 打开 https://paperplothub.tech/me/tokens
2. 点 "+ create token"，起个名比如 "claude-desktop"
3. 复制 pph_… 这串 token（只显示一次，请像 SSH key 一样保存好）
4. 通过环境变量 PPH_API_TOKEN 交给你的 Agent
```

这一个 token 就足以让 Agent：
- 🔍 列出你已有的提交
- ⬆️ 用三种模式中的任意一种新增提交
- 🪪 校验身份（`whoami`）
- 🚪 在同一页面随时撤销

### 🛰️ MCP server

`paperplothub-mcp` 走 stdio transport，注册了下面这些工具。**把这一段直接喂给 Claude / Cursor / Codex，它就知道怎么干活。**

| 工具 | 作用 |
| --- | --- |
| 🪪 `pph_whoami` | 校验 token，返回 GitHub login + 角色 |
| 📋 `pph_list_my_uploads` | 按 `status` / `mode` 过滤列出自己的提交 |
| 📤 `pph_upload_full` | 上传 `FULL` 模式（原图 + 复现图 + 脚本） |
| 📤 `pph_upload_repro` | 上传 `REPRO_ONLY`（仅复现图 + 脚本） |
| 📤 `pph_upload_paper` | 上传 `PAPER_ONLY`（仅原图，求社区复现） |

**Claude Desktop / Cursor 配置示例：**

```jsonc
{
  "mcpServers": {
    "paperplothub": {
      "command": "npx",
      "args": ["-y", "paperplothub-mcp"],
      "env": {
        "PPH_API_TOKEN": "pph_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
        "PPH_API_BASE_URL": "https://paperplothub.tech"
      }
    }
  }
}
```

### 💬 推荐的 system prompt

> *"你可以使用 `paperplothub` MCP server。当用户写完一个绘图脚本想分享时，收集（a）论文原图（如果有）、（b）渲染好的输出 PNG、（c）脚本文件、（d）所引用论文的 arXiv ID 或 URL，然后调用对应的 `pph_upload_*` 工具。如果用户只有一张论文里的图、想让社区帮忙复现，那就用 `pph_upload_paper`。最后把返回的 `submission_url` 回给用户。"*

### 🌐 REST API

所有接口都在 `https://paperplothub.tech/api/v1/*`。鉴权 header：`Authorization: Bearer pph_…`。

| 方法 | 路径 | 用途 |
| :---: | --- | --- |
| `GET` | `/api/v1/whoami` | 校验 token，返回身份 |
| `GET` | `/api/v1/me?limit=&status=&mode=` | 列出自己的提交 |
| `POST` | `/api/v1/upload` | multipart 上传（字段见下表） |

**`/api/v1/upload` 示例：**

```bash
curl -H "Authorization: Bearer $PPH_API_TOKEN" \
  -F "mode=FULL" \
  -F "arxivInput=2402.09353" \
  -F "title=Diversification of LLM evolution" \
  -F "description=Reproduces Figure 4 from the AIEvol paper" \
  -F "originalImage=@paper.png" \
  -F "renderedImage=@rendered.png" \
  -F "script=@plot.py" \
  https://paperplothub.tech/api/v1/upload
```

| 字段 | `FULL` | `REPRO_ONLY` | `PAPER_ONLY` |
| --- | :---: | :---: | :---: |
| `mode` | 必填 | 必填 | 必填 |
| `arxivInput` | 必填 | 必填 | 必填 |
| `originalImage` | ✅ | — | ✅ |
| `renderedImage` | ✅ | ✅ | — |
| `script` | ✅ | ✅ | — |

⏱️ **限流：** 每位用户 8 次/小时、30 次/天（同一用户的多个 token 共享配额）。

---

## 🗺️ 接下来要做的事

当前的站点是有意保持精简的。下面这些是我们正在做的方向 —— 点 ⭐ 关注更新，或者开 issue 投票把你最想看到的功能往前提。

### 🛡️ 审核与安全

- [ ] 🪶 **AI 辅助脚本润色** —— 自动整理缩进、类型注解、删未用 import，但不改变绘图本身。
- [ ] 🧹 **编辑时文本审核**（标题 / 描述）。
- [ ] 🎚️ **不同图表类别独立配置 AI 通过分数阈值**（比如 heatmap 要求更严的视觉匹配）。

### 🔍 发现与协作

- [ ] 🔎 **标签筛选 + 全文搜索**。
- [ ] 💬 **评论 / 讨论**，支持 @mention。
- [ ] 🔁 **"复现这张图" 工作流** —— 把社区复现自动关联回原 `PAPER_ONLY` 提交，并通知最初发布者。
- [ ] 👤 **作者主页**：显示提交历史。
- [ ] 📚 **精选合集**（如 *"NeurIPS 2024 最佳图表 Top 20"*、*"LLM scaling law 经典图集"*）。

### 📦 提交形态

- [ ] 🖼️ **多图提交** —— 一篇论文里多张图打包提交。
- [ ] 🧩 **浏览器扩展** —— 直接在 arXiv / OpenReview 页面上抠图并提交，两步搞定。
- [ ] 🐍 **浏览器内脚本预览** —— 用 Pyodide 在沙箱里跑内联数据的 `.py` 脚本。

### 🏗️ 基础设施

- [ ] ☁️ **对象存储后端**（S3 / 腾讯 COS），让画廊不用担心磁盘占用。
- [ ] 📦 **公开数据集导出** `/api/v1/dataset.zip`（CC BY 4.0，供学术研究使用）。
- [ ] 🔔 **通知系统**：你提交的 `PAPER_ONLY` 被人复现时及时提醒。

### 🌍 国际化

- [ ] 🇨🇳🇺🇸 **完整的 UI 双语切换** —— 当前只有提交内容是双语，外壳仍偏英文。
- [ ] 🇯🇵🇰🇷 **日 / 韩语本地化**（社区贡献）。

---

## 🙋 常见问题

<details>
<summary><b>❓ 站点为啥这么简朴？没有圆角阴影卡片？</b></summary>

故意的 —— 画廊是给图看的，不是给图的包装看的。Hero 区是个伪终端，卡片是平的，整个站点最显眼的颜色应该来自图本身。

</details>

<details>
<summary><b>❓ 我能上传 arXiv 上没有的论文里的图吗？</b></summary>

暂时不行 —— AI 流水线依赖 arXiv 的元数据 API。"会议-only、无 arXiv 预印本" 的情形在 roadmap 里。

</details>

<details>
<summary><b>❓ 我的脚本依赖私有数据，还能传吗？</b></summary>

可以。本站**不会执行**任何上传的脚本，只展示你提供的渲染结果图。脚本里那条私有数据路径只是行注释，没人能跑。

</details>

<details>
<summary><b>❓ 怎么删除或下架我的提交？</b></summary>

进 `/me` 打开条目，用 *"unpublish"* 按钮下架。硬删除还在 roadmap 里 —— 在那之前，下架的条目会从公开画廊和搜索里消失。

</details>

<details>
<summary><b>❓ 什么样的图最适合提交？</b></summary>

任何会让别人想"借这张图的样式"的：带置信区间的柱状图、训练曲线面板、带注释的热力图、雷达图、带 inset zoom 的散点、t-SNE 聚类、broken-axis 对比图……只要这段脚本的价值主要在于*版式、配色、排版*，就值得放进画廊。

</details>

---

## 📬 联系我们

- 🌐 站点：<https://paperplothub.tech>
- 🐙 文档仓库：<https://github.com/Trae1ounG/PaperPlotHub>
- 🐛 发现 bug、觉得某个图表类型标签缺了，或者想推荐我们下一批复现的论文？在本仓库开 issue。

---

## 📄 License

采用 [MIT](./LICENSE) 协议发布。

> *献给所有右键过论文图，心想"要是我有这张图的脚本就好了"的人 ❤️*
