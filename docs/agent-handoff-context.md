# Agent Handoff Context — OOB IoT Sec Labs

> 用途：将本文件交给新的 agent / 新模型读取，使其快速熟悉 `https://www.oobsec.cn/` 网站维护工作区。  
> 更新时间：2026-09-20  
> 当前主仓库：`C:\github\oob-iot-sec-labs.github.io`

---

## 1. 当前目标与工作边界

本工作区只保留与 OOB IoT Sec Labs 社区网站相关的上下文。

需要关注：

- 网站：`https://www.oobsec.cn/`
- GitHub Pages 仓库：`https://github.com/oob-iot-sec-labs/oob-iot-sec-labs.github.io`
- 本地网站仓库：`C:\github\oob-iot-sec-labs.github.io`
- 组织主页仓库：`https://github.com/oob-iot-sec-labs/.github.git`
- 本地组织主页仓库：`C:\github\.github`

不需要保留：

- 固件审计、MikroTik、IDA 数据审核等历史任务上下文。
- 与当前网站维护无关的临时分析内容。

---

## 2. 品牌与站点事实

- 品牌名称统一为：`OOB IoT Sec Labs`
- 网站描述：`IoT 网络安全社区`
- 站点主域名：`https://www.oobsec.cn/`
- `_config.yml` 中当前 URL 可能为 `https://oobsec.cn`，用户已说明有无 `www` 都可访问；除非明确要求，不要随意改 `CNAME`。
- 网站技术栈：Jekyll + `jekyll-theme-hacker`
- 语言风格：中文为主；文章是正式技术文章，不是草稿、笔记或内部整理记录。
- 联系邮箱保留为：`chinagreatsec@outlook.com`

写作风格要求：

- 不要在正式文章中写“原始记录”“草稿”“整理笔记”“笔记中提到”等编辑痕迹。
- 不要随意改作者已有表达，尤其是与读者互动的句子，例如“需要读者注意”“希望读者获得什么”。
- 可补充结构化内容，但尽量不要重写作者复现过程。
- 技术文章应保持正式技术叙述；能省略主语时尽量省略。

---

## 3. 当前网站模块结构

主要模块：

```text
index.md                                  # 首页
vulnerabilities/                          # 漏洞研究
  index.md
  CVE/                                    # CVE 正式归档
    index.md
    CVE-2022-42475/
    CVE-2026-8452/
  research/                               # 原创研究
  vendor-labs/                            # 品牌设备研究入口
    index.md
    citrix/
      index.md
      environment-setup/
      debugging/
    fortinet/
      index.md
tools/
resources/
writeups/
docs/
```

品牌设备研究不是替代 CVE 库：

- 有 CVE 编号的漏洞文章：主归档放 `vulnerabilities/CVE/CVE-XXXX-XXXXX/index.md`
- 同时在对应品牌页增加文章卡片，例如 `vulnerabilities/vendor-labs/citrix/index.md`
- 非 CVE 的品牌系列文章，例如环境搭建、调试方法：放在 `vulnerabilities/vendor-labs/<vendor>/<topic>/index.md`

---

## 4. 图片与附件规范

CVE 文章图片：

```text
assets/images/<Vendor>/CVE-XXXX-XXXXX/
```

示例：

```text
assets/images/Citrix/CVE-2026-8452/
assets/images/Forti/CVE-2022-42475/
```

品牌设备研究文章图片：

```text
assets/images/vulnerabilities/vendor-labs/<vendor>/<topic>/
```

示例：

```text
assets/images/vulnerabilities/vendor-labs/citrix/environment-setup/
assets/images/vulnerabilities/vendor-labs/citrix/debugging/
```

图片引用必须使用 Jekyll `relative_url`：

```markdown
![图片描述]({{ '/assets/images/Citrix/CVE-2026-8452/example.png' | relative_url }})
```

不要保留 Obsidian 图片语法：

```markdown
![[assets/...]]
```

---

## 5. 技术文章 Front Matter 规范

CVE 文章示例：

```yaml
---
layout: default
title: "CVE-XXXX-XXXXX | Vendor Product 漏洞类型分析"
permalink: /vulnerabilities/CVE/CVE-XXXX-XXXXX/
category: vulnerability
tags:
  - Vendor
  - Product
  - CVE
vendor: Vendor
product: Product
author: ChinaGreat-IoTSec
date: YYYY-MM-DD
---
```

品牌设备研究文章示例：

```yaml
---
layout: default
title: "Citrix NetScaler 调试：pitboss 心跳监控分析"
permalink: /vulnerabilities/vendor-labs/citrix/debugging/
category: vulnerability
tags:
  - Citrix
  - NetScaler
  - debugging
vendor: Citrix
product: NetScaler ADC
author: ChinaGreat-IoTSec
date: YYYY-MM-DD
---
```

技术文章不要手写返回按钮；全局布局会根据 `category: vulnerability` 自动生成返回导航。

---

## 6. 当前重要文章状态

已存在并已推送：

- `CVE-2022-42475`
  - 路径：`vulnerabilities/CVE/CVE-2022-42475/index.md`
  - 图片：`assets/images/Forti/CVE-2022-42475/`
  - Fortinet 专栏中做关联展示。

- Citrix 环境搭建
  - 路径：`vulnerabilities/vendor-labs/citrix/environment-setup/index.md`
  - 图片：`assets/images/vulnerabilities/vendor-labs/citrix/environment-setup/`

- Citrix 调试文章
  - 路径：`vulnerabilities/vendor-labs/citrix/debugging/index.md`
  - 图片：`assets/images/vulnerabilities/vendor-labs/citrix/debugging/`
  - 注意：目录已简化为 `debugging/`，不要再增加无必要的 `pitboss-watchdog/` 层级。

- `CVE-2026-8452`
  - 路径：`vulnerabilities/CVE/CVE-2026-8452/index.md`
  - 图片：`assets/images/Citrix/CVE-2026-8452/`
  - 最新提交：`e29852b feat: add CVE-2026-8452 Citrix analysis`
  - 已推送到 `origin/main`
  - 补充过漏洞成因概述，但尽量保留作者复现过程原表达。
  - 参考文章已添加：
    `https://labs.watchtowr.com/youre-back-in-the-room-citrix-netscaler-pre-auth-rce-cve-2026-8452/`

---

## 7. 索引页更新规则

新增 CVE 文章至少更新：

```text
vulnerabilities/CVE/index.md
vulnerabilities/index.md
vulnerabilities/vendor-labs/<vendor>/index.md
```

新增品牌设备研究文章至少更新：

```text
vulnerabilities/vendor-labs/index.md       # 如新增品牌
vulnerabilities/vendor-labs/<vendor>/index.md
```

首页 `index.md` 一般不需要每次新增文章都改，除非用户明确要求。

---

## 8. Git 与推送状态

当前网站仓库最近提交：

```text
e29852b feat: add CVE-2026-8452 Citrix analysis
33cee0b docs: polish Citrix debugging article wording
f49af12 feat: add Citrix debugging guide
8851c4b style: simplify vendor research pages
997b24b feat: add vendor device research section
```

当前网站仓库状态应为：

```text
main...origin/main
```

提交作者希望统一为：

```text
ChinaGreat-IoTSec <chinagreatsec@outlook.com>
```

用户已经讨论过全局 Git 配置；新 agent 如果要提交，先检查：

```powershell
git config user.name
git config user.email
git config --global user.name
git config --global user.email
```

---

## 9. 组织主页仓库状态

组织主页仓库：

```text
C:\github\.github
https://github.com/oob-iot-sec-labs/.github.git
```

已同步组织主页内容到网站风格。

最近相关提交：

```text
6525936 docs: sync organization profile with website
```

组织主页 README：

```text
C:\github\.github\profile\README.md
```

除非用户明确要求，不要随意改组织主页仓库。

---

## 10. 新 agent 开始工作前建议命令

```powershell
cd C:\github\oob-iot-sec-labs.github.io
git status -sb
git pull --ff-only
Get-Content -LiteralPath docs\agent-handoff-context.md
Get-Content -LiteralPath docs\site-context.md
Get-Content -LiteralPath docs\technical-article-template.md
```

如果需要处理组织主页：

```powershell
cd C:\github\.github
git status -sb
git pull --ff-only
Get-Content -LiteralPath profile\README.md
```

---

## 11. 交接提示词

可以把下面这段发给新 agent：

> 请先读取 `C:\github\oob-iot-sec-labs.github.io\docs\agent-handoff-context.md`、`docs\site-context.md` 和 `docs\technical-article-template.md`，了解 OOB IoT Sec Labs 网站维护规范。当前只处理 `https://www.oobsec.cn/` 社区网站相关任务。技术文章是正式文章，保留作者表达，不要使用“原始记录/草稿/整理笔记”等编辑痕迹。新增 CVE 文章放入 `vulnerabilities/CVE/`，同时更新 CVE 索引、漏洞研究首页和对应品牌页。
