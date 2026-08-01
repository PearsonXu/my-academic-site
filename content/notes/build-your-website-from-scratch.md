---
title: "Build Your Personal Website from Scratch"
date: 2025-08-01
description: "A step-by-step guide to building your own academic/personal website with Hugo + AI — no coding experience required."
tags: ["tutorial", "建站"]
featured: true
---

<div class="zx-lang-switch">
  <button class="zx-lang-btn active" data-lang="en">English</button>
  <button class="zx-lang-btn" data-lang="zh">中文</button>
</div>

<div class="zx-lang-content" data-lang="en">

> This guide is written for people with **zero programming experience**. If you can type and click a mouse, you can follow along. The whole process takes about one afternoon.

## Overview: What Are We Building?

End goal: a website at your own domain (e.g. `www.yourname.com`), hosted on GitHub Pages, **completely free** (except the domain itself, ~$10–15/year).

The tech stack is simple:

| Component | Role | Cost |
|-----------|------|------|
| Domain (Namecheap / Squarespace) | Your web address | ~$10–15/yr |
| [Hugo](https://gohugo.io) | Static site generator | Free |
| [PaperMod](https://github.com/adityatelange/hugo-PaperMod) | Hugo theme | Free |
| [GitHub](https://github.com) + GitHub Pages | Code hosting + site hosting | Free |
| [VS Code](https://code.visualstudio.com) + [Cline](https://cline.bot) + AI API | Your AI programming assistant | API usage, negligible |

You do **not** need to write code yourself — the AI writes it for you. Your role is more like a "project manager": describe what you want, and the AI executes.

---

## Step 1: Buy a Domain

A domain is your website's address. Two recommended registrars:

- **[Namecheap](https://www.namecheap.com)**: Affordable, friendly UI. A `.com` domain typically costs $9–12 for the first year.
- **[Squarespace Domains](https://domains.squarespace.com)**: Cleaner interface, slightly more expensive (~$20/yr).

**Instructions (using Namecheap):**

1. Go to [namecheap.com](https://www.namecheap.com) and type your desired domain (e.g. `yourname.com`) in the search box.
2. If available, click "Add to Cart" → checkout → create an account → pay.
3. After purchase, go to **Domain List** → click your domain → you'll see **Nameservers** and **Advanced DNS** tabs. **Remember this page** — you'll come back in Step 8.

> 💡 Tip: Stick with `.com`. If your name is taken, try adding a middle initial or field abbreviation (e.g. `yourname-math.com`).

---

## Step 2: Install VS Code

[Visual Studio Code](https://code.visualstudio.com) (VS Code) is a free code editor by Microsoft. It's also the home for Cline, your AI assistant.

1. Go to [code.visualstudio.com](https://code.visualstudio.com) and click "Download".
2. Install it (macOS: drag to Applications; Windows: click Next through the wizard).
3. Open VS Code — you'll see a clean editor interface.

> You don't need to understand any editor features yet. It's just the AI assistant's "home".

---

## Step 3: Install the Cline Extension

[Cline](https://cline.bot) is a VS Code extension that lets AI read/write files and run commands directly on your computer. Think of it as "a programmer sitting inside your machine".

1. In VS Code, click the **Extensions icon** in the left sidebar (four squares, shortcut `Cmd+Shift+X` / `Ctrl+Shift+X`).
2. Search for **"Cline"**, find the one by `saoudrizwan`, click **Install**.
3. After installation, a Cline icon (robot-like) appears in the sidebar. Click it.
4. On first launch, it will ask you to configure an AI provider (next step).

---

## Step 4: Configure an AI API

Cline needs a "brain". Two excellent and affordable options:

### Option A: DeepSeek API (recommended, cheapest)

1. Go to [platform.deepseek.com](https://platform.deepseek.com) and sign up.
2. Go to **API Keys** → "Create API Key" → copy the key (starts with `sk-`).
3. Top up ¥10 (~$1.5) in the billing page — enough for a long time.
4. Back in VS Code → Cline panel → Settings → choose **OpenAI Compatible** provider:
   - API Key: paste your key
   - Base URL: `https://api.deepseek.com`
   - Model ID: `deepseek-chat`

### Option B: Qwen (Tongyi Qianwen) API

1. Go to [Alibaba Cloud Bailian](https://bailian.console.aliyun.com/) and log in with Alipay/Taobao.
2. Go to **API-KEY Management** → create a key.
3. New users usually get free credits.
4. In Cline settings, choose **OpenAI Compatible**:
   - API Key: paste your key
   - Base URL: `https://dashscope.aliyuncs.com/compatible-mode/v1`
   - Model ID: `qwen-plus`

> 💡 Both use the OpenAI-compatible format, so Cline configuration is identical. DeepSeek is cheaper; Qwen has slightly stronger Chinese comprehension. Either works.

---

## Step 5: Build the Website

Now the fun part. In Cline's chat box, describe what you want in plain language.

### 5.1 Create the Project

Type in Cline's chat:

```
Create a Hugo website in the current directory using the PaperMod theme.
Site title: "Your Name | Your Field", baseURL: "https://www.yourname.com/".
```

Cline will automatically:
- Install Hugo (if not already on your machine)
- Create the project structure
- Download the PaperMod theme
- Generate the config file `hugo.toml`

### 5.2 Add Pages

Continue telling Cline:

```
Create the following pages:
- About: a short bio
- Research: list research interests
- Teaching: list TA/course experience
- Notes (blog): for writing articles
Add navigation menu links for all of them.
```

### 5.3 Write Your First Post

```
Create a post at content/notes/hello-world.md,
title "Hello, World", with a few test sentences.
```

### 5.4 Customize Styling (Optional)

```
Customize the PaperMod theme colors and fonts
to make it look like a clean academic website.
```

> 💡 You don't need to say everything at once. Chat with Cline iteratively — after each change, refresh your browser to see the result.

---

## Step 6: Local Testing

In VS Code's terminal (menu: Terminal → New Terminal), run:

```bash
hugo server -D
```

Then open **http://localhost:1313** in your browser. You'll see a live preview — any file change auto-refreshes.

Checklist:
- [ ] Homepage displays correctly
- [ ] All nav links work
- [ ] Post pages render properly
- [ ] Mobile view (F12 → device emulation) looks good

When satisfied, press `Ctrl+C` to stop the server.

---

## Step 7: Deploy to GitHub Pages

### 7.1 Create a GitHub Repository

1. Go to [github.com](https://github.com), sign up / log in.
2. Click "+" → **New repository**.
3. Name it anything (e.g. `my-academic-site`), Public or Private.
4. After creation, in VS Code terminal:

```bash
git init
git add -A
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/my-academic-site.git
git push -u origin main
```

(Or just tell Cline: "Initialize git and push to GitHub for me.")

### 7.2 Set Up GitHub Actions Auto-Deploy

Tell Cline:

```
Create a GitHub Actions workflow that builds with Hugo
and deploys to GitHub Pages on every push to main.
```

It creates `.github/workflows/hugo.yml`. After pushing, go to your repo → **Settings** → **Pages** → Source: **GitHub Actions**.

Wait a few minutes — your site appears at `https://YOUR_USERNAME.github.io/my-academic-site/`.

### 7.3 Bind Your Custom Domain

1. Repo → **Settings** → **Pages** → **Custom domain**: enter `www.yourname.com` → Save.
2. Check **Enforce HTTPS**.
3. Create a `static/CNAME` file containing `www.yourname.com` (tell Cline: "Create static/CNAME with content www.yourname.com").

---

## Step 8: DNS Configuration

Go back to your domain registrar (Namecheap → Domain List → your domain → **Advanced DNS**).

Add these records:

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A Record | `@` | `185.199.108.153` | Automatic |
| A Record | `@` | `185.199.109.153` | Automatic |
| A Record | `@` | `185.199.110.153` | Automatic |
| A Record | `@` | `185.199.111.153` | Automatic |
| CNAME Record | `www` | `YOUR_USERNAME.github.io` | Automatic |

> These four IPs are GitHub Pages' official addresses ([source](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)).

After saving, DNS propagation takes **10 minutes to 48 hours** (usually under 1 hour).

---

## Step 9: Verify & Test

Once DNS propagates, check each item:

1. **Browser**: Open `https://www.yourname.com` — see your site? ✅
2. **HTTPS**: Padlock icon in the address bar? ✅ (GitHub auto-issues Let's Encrypt certs)
3. **Command line** (optional, in terminal):

```bash
# Check DNS resolution
dig www.yourname.com +short
# Should return YOUR_USERNAME.github.io

# Check HTTP response
curl -I https://www.yourname.com
# Should return HTTP/2 200
```

4. **Global reachability**: Open [whatsmydns.net](https://www.whatsmydns.net), enter your domain, check worldwide DNS sync.
5. **Mobile test**: Open your domain on your phone's browser (turn off Wi-Fi, use cellular).

---

## FAQ

**Q: I truly cannot code. Can I really do this?**
A: Yes. Every "technical operation" in this guide can be done by telling Cline one sentence. Your job is to describe what you want.

**Q: I don't understand the code the AI writes. What do I do?**
A: You don't need to understand it. Like driving a car without understanding the engine. If something breaks, paste the error to Cline — it will fix it.

**Q: How much does this cost per year?**
A: Domain ~$10–15. Hosting free (GitHub Pages). AI API a few cents per month. Total under $20/year.

**Q: How do I update content later?**
A: Open the `.md` file in VS Code, edit, save, then `git add -A && git commit -m "update" && git push`. Or tell Cline: "Change the second paragraph of my About page to…"

---

## Link Summary

| Resource | Link |
|----------|------|
| Namecheap (domain) | https://www.namecheap.com |
| Squarespace Domains | https://domains.squarespace.com |
| VS Code | https://code.visualstudio.com |
| Cline extension | https://cline.bot |
| DeepSeek API | https://platform.deepseek.com |
| Qwen API | https://bailian.console.aliyun.com |
| Hugo | https://gohugo.io |
| PaperMod theme | https://github.com/adityatelange/hugo-PaperMod |
| GitHub | https://github.com |
| GitHub Pages docs | https://docs.github.com/en/pages |
| DNS checker | https://www.whatsmydns.net |

---

*Written August 2025. If you follow along and finish, feel free to email me your website.*

</div>

<div class="zx-lang-content" data-lang="zh" style="display:none">

> 这篇文章面向完全没有编程经验的朋友。你只需要会打字、会点鼠标，就能跟着做完。整个过程大约需要一个下午。

## 总览：我们要做什么？

最终目标：一个以你自己域名命名的网站（比如 `www.yourname.com`），托管在 GitHub Pages 上，**完全免费**（除了域名本身每年约 $10–15）。

技术栈很简单：

| 组件 | 作用 | 费用 |
|------|------|------|
| 域名（Namecheap / Squarespace） | 你的网址 | ~$10–15/年 |
| [Hugo](https://gohugo.io) | 静态网站生成器 | 免费 |
| [PaperMod](https://github.com/adityatelange/hugo-PaperMod) | Hugo 主题 | 免费 |
| [GitHub](https://github.com) + GitHub Pages | 代码托管 + 网站托管 | 免费 |
| [VS Code](https://code.visualstudio.com) + [Cline](https://cline.bot) + AI API | 你的 AI 编程助手 | API 按量计费，极低 |

你**不需要**自己写代码——AI 会帮你写。你的角色更像是一个"项目经理"：告诉 AI 你想要什么，它来执行。

---

## 第一步：购买域名

域名就是你网站的地址。推荐两个注册商：

- **[Namecheap](https://www.namecheap.com)**：便宜，界面友好，`.com` 域名首年通常 $9–12。
- **[Squarespace Domains](https://domains.squarespace.com)**：界面更简洁，适合不想折腾的人，价格略高（~$20/年）。

**操作（以 Namecheap 为例）：**

1. 打开 [namecheap.com](https://www.namecheap.com)，在搜索框输入你想要的域名（比如 `yourname.com`）。
2. 如果可用，点击 "Add to Cart" → 结账 → 注册账号 → 付款。
3. 购买完成后，进入 **Domain List** → 点击你的域名 → 你会看到 **Nameservers** 和 **Advanced DNS** 选项卡。**先记住这个页面**，后面第八步会回来。

> 💡 建议：选 `.com` 后缀。如果名字被占了，试试加中间名缩写或专业缩写（如 `yourname-math.com`）。

---

## 第二步：安装 VS Code

[Visual Studio Code](https://code.visualstudio.com)（简称 VS Code）是微软出品的免费代码编辑器，也是 AI 编程助手 Cline 的运行环境。

1. 打开 [code.visualstudio.com](https://code.visualstudio.com)，点击 "Download" 按钮。
2. 下载完成后双击安装（macOS 拖入 Applications 文件夹；Windows 一路 Next）。
3. 打开 VS Code，你会看到一个简洁的编辑器界面。

> 你暂时不需要理解编辑器的任何功能。它只是 AI 助手的"家"。

---

## 第三步：安装 Cline 插件

[Cline](https://cline.bot) 是一个 VS Code 插件，让 AI 直接在你的电脑上读写文件、运行命令。你可以把它理解为一个"坐在你电脑里的程序员"。

1. 在 VS Code 左侧栏点击 **扩展图标**（四个方块的图标，快捷键 `Cmd+Shift+X` / `Ctrl+Shift+X`）。
2. 搜索 **"Cline"**，找到发布者 `saoudrizwan` 的那个，点击 **Install**。
3. 安装完成后，左侧栏会出现一个 Cline 的图标（像一个机器人）。点击它。
4. 首次打开会要求你配置 AI 提供商（见下一步）。

---

## 第四步：配置 AI API

Cline 需要一个"大脑"来驱动。推荐两个对中文支持极好且价格低廉的选项：

### 选项 A：DeepSeek API（推荐，最便宜）

1. 打开 [platform.deepseek.com](https://platform.deepseek.com)，注册账号。
2. 进入 **API Keys** 页面 → 点击 "Create API Key" → 复制生成的密钥（以 `sk-` 开头）。
3. 在左侧 **充值** 页面充入 ¥10（约 $1.5），足够用很久。
4. 回到 VS Code → Cline 面板 → 设置中选择 **OpenAI Compatible** 提供商：
   - API Key：粘贴你的密钥
   - Base URL：`https://api.deepseek.com`
   - Model ID：`deepseek-chat`

### 选项 B：通义千问（Qwen）API

1. 打开 [阿里云百炼平台](https://bailian.console.aliyun.com/)，用支付宝/淘宝账号登录。
2. 进入 **API-KEY 管理** → 创建密钥。
3. 新用户通常有免费额度。
4. 在 Cline 设置中选择 **OpenAI Compatible**：
   - API Key：粘贴你的密钥
   - Base URL：`https://dashscope.aliyuncs.com/compatible-mode/v1`
   - Model ID：`qwen-plus`

> 💡 两家都兼容 OpenAI 格式，Cline 配置方式完全一样。DeepSeek 更便宜，Qwen 中文理解略强。选哪个都行。

---

## 第五步：搭建网站

现在进入正题。在 Cline 的对话框里，你可以直接用自然语言告诉它你想做什么。以下是推荐的操作顺序：

### 5.1 创建项目

在 Cline 对话框中输入：

```
帮我在当前目录创建一个 Hugo 网站，使用 PaperMod 主题。
网站标题叫 "Your Name | Your Field"，baseURL 设为 "https://www.yourname.com/"。
```

Cline 会自动执行：
- 安装 Hugo（如果你电脑上没有）
- 创建项目结构
- 下载 PaperMod 主题
- 生成配置文件 `hugo.toml`

### 5.2 添加页面

继续对 Cline 说：

```
帮我创建以下页面：
- About（关于我）：放一段自我介绍
- Research（研究）：列出研究方向
- Teaching（教学）：列出助教/课程经历
- Notes（漫谈/博客）：用来写文章
并在导航栏菜单里加上这些页面的链接。
```

### 5.3 写第一篇文章

```
在 content/notes/ 下创建一篇文章 hello-world.md，
标题是 "Hello, World"，内容随便写几句测试文字。
```

### 5.4 自定义样式（可选）

```
帮我自定义 PaperMod 主题的配色和字体，
让它看起来更像一个学术网站，简洁大方。
```

> 💡 你不需要一次说完所有需求。可以像聊天一样，一步步告诉 Cline 你想改什么。每次它改完，你刷新浏览器就能看到效果。

---

## 第六步：本地测试

在 VS Code 的终端（菜单 Terminal → New Terminal）中运行：

```bash
hugo server -D
```

然后打开浏览器访问 **http://localhost:1313**。你会看到你的网站实时预览——任何文件改动都会自动刷新。

检查清单：
- [ ] 首页正常显示
- [ ] 导航栏链接都能点开
- [ ] 文章页面排版正常
- [ ] 手机尺寸下（浏览器按 F12 → 切换设备模拟）没有错位

满意之后，按 `Ctrl+C` 停止服务器。

---

## 第七步：部署到 GitHub Pages

### 7.1 创建 GitHub 仓库

1. 打开 [github.com](https://github.com)，注册/登录。
2. 点击右上角 "+" → **New repository**。
3. 仓库名随意（如 `my-academic-site`），选 **Private** 或 Public 均可。
4. 创建后，在 VS Code 终端执行：

```bash
git init
git add -A
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/你的用户名/my-academic-site.git
git push -u origin main
```

（或者直接让 Cline 帮你做：`帮我把项目初始化 git 并推送到 GitHub`）

### 7.2 配置 GitHub Actions 自动部署

让 Cline 帮你：

```
帮我创建 GitHub Actions 工作流，每次 push 到 main 分支时自动用 Hugo 构建并部署到 GitHub Pages。
```

它会创建 `.github/workflows/hugo.yml`。推送后，进入 GitHub 仓库 → **Settings** → **Pages** → Source 选择 **GitHub Actions**。

等几分钟，你的网站就会出现在 `https://你的用户名.github.io/my-academic-site/`。

### 7.3 绑定自定义域名

1. 在 GitHub 仓库 → **Settings** → **Pages** → **Custom domain** 填入 `www.yourname.com` → Save。
2. 勾选 **Enforce HTTPS**。
3. 在仓库根目录创建 `static/CNAME` 文件，内容写 `www.yourname.com`（让 Cline 做：`创建 static/CNAME 文件，内容是 www.yourname.com`）。

---

## 第八步：DNS 设置

回到第一步买域名的那个页面（Namecheap → Domain List → 你的域名 → **Advanced DNS**）。

添加以下记录：

| Type | Host | Value | TTL |
|------|------|-------|-----|
| A Record | `@` | `185.199.108.153` | Automatic |
| A Record | `@` | `185.199.109.153` | Automatic |
| A Record | `@` | `185.199.110.153` | Automatic |
| A Record | `@` | `185.199.111.153` | Automatic |
| CNAME Record | `www` | `你的用户名.github.io` | Automatic |

> 这四个 IP 是 GitHub Pages 的官方地址（[来源](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site#configuring-an-apex-domain)）。

保存后，DNS 生效需要 **10 分钟到 48 小时**（通常 1 小时内）。

---

## 第九步：验证与网络测试

DNS 生效后，逐项检查：

1. **浏览器访问**：打开 `https://www.yourname.com`，看到你的网站？✅
2. **HTTPS 证书**：地址栏有🔒图标？✅（GitHub 自动签发 Let's Encrypt 证书）
3. **命令行测试**（可选，在终端执行）：

```bash
# 检查 DNS 解析
dig www.yourname.com +short
# 应返回 你的用户名.github.io

# 检查网站响应
curl -I https://www.yourname.com
# 应返回 HTTP/2 200
```

4. **全球可达性测试**：打开 [whatsmydns.net](https://www.whatsmydns.net)，输入你的域名，查看全球各地 DNS 是否已同步。
5. **手机测试**：用手机浏览器（关掉 Wi-Fi，用流量）访问你的域名。

---

## 常见问题

**Q：我完全不会写代码，真的能做吗？**
A：能。这篇文章里所有"技术操作"都可以用一句话让 Cline 完成。你的工作就是描述你想要什么。

**Q：AI 写的代码我不懂怎么办？**
A：不需要懂。就像你不需要懂发动机原理也能开车。如果网站出了问题，把错误信息贴给 Cline，它会修。

**Q：每年要花多少钱？**
A：域名 ~$10–15。托管免费（GitHub Pages）。AI API 每月几毛钱到几块钱。总计每年不超过 ¥100。

**Q：以后想改内容怎么办？**
A：在 VS Code 里打开对应的 `.md` 文件，改完保存，然后 `git add -A && git commit -m "update" && git push`。或者直接告诉 Cline："帮我把 About 页面的第二段改成……"。

---

## 链接汇总

| 资源 | 链接 |
|------|------|
| Namecheap（域名） | https://www.namecheap.com |
| Squarespace Domains | https://domains.squarespace.com |
| VS Code | https://code.visualstudio.com |
| Cline 插件 | https://cline.bot |
| DeepSeek API | https://platform.deepseek.com |
| 通义千问 API | https://bailian.console.aliyun.com |
| Hugo | https://gohugo.io |
| PaperMod 主题 | https://github.com/adityatelange/hugo-PaperMod |
| GitHub | https://github.com |
| GitHub Pages 文档 | https://docs.github.com/en/pages |
| DNS 检测工具 | https://www.whatsmydns.net |

---

*写于 2025 年 8 月。如果你跟着做完了，欢迎给我发邮件分享你的网站。*

</div>

<script>
(function () {
  var btns = document.querySelectorAll('.zx-lang-btn');
  var sections = document.querySelectorAll('.zx-lang-content');
  btns.forEach(function (btn) {
    btn.addEventListener('click', function () {
      var lang = btn.dataset.lang;
      btns.forEach(function (b) { b.classList.toggle('active', b === btn); });
      sections.forEach(function (s) {
        s.style.display = s.dataset.lang === lang ? '' : 'none';
      });
    });
  });
})();
</script>