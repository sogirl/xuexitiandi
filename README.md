# 学习天地 · 主人学习手册库

> 主人您的随身学习手册库。每次新整理完一批 HTML，扔进对应分类子目录、push 到本仓库，手机打开主页就能随时随地翻看。

🌐 在线访问：<https://sogirl.github.io/xuexitiandi/>

---

## 📁 仓库结构

```
xuexitiandi/
├── index.html            # 主页（动态从 GitHub API 拉取文件清单，手机/电脑都好看）
├── README.md             # 本说明
└── 全部 HTML 文件夹（按主题分子目录）
    ├── 01亚马逊跨境电商/   # 26 个
    ├── 02育儿教育/         # 8 个
    ├── 03打磨自己-学习方法/ # 11 个
    ├── 04投资理财/         # 1 个
    ├── 05设计技能/         # 1 个
    └── … 后续可加 06xxx/
```

---

## 🚀 使用说明（给主人）

### 一次性：开启 GitHub Pages（手机访问入口）

1. 打开 <https://github.com/sogirl/xuexitiandi/settings/pages>
2. **Source** 选 `Deploy from a branch`
3. **Branch** 选 `main`，目录 `/ (root)`，保存
4. 等待 1–2 分钟，访问 <https://sogirl.github.io/xuexitiandi/> 就能看到主页
5. 把这个链接收藏到手机浏览器主屏幕 → 等于您的"随身手册库 App"

> 💡 **iPhone**：Safari 打开后点分享按钮 → "添加到主屏幕"
> **Android**：Chrome 打开后菜单 → "添加到主屏幕"

### 以后每次新增 HTML 怎么办？

**核心思路**：您不需要再改 `index.html`！因为主页是动态从 GitHub API 拉取清单的，新文件 push 上去后主页自动出现。

#### 步骤（推荐）

1. 在 `F:\学习助手\全部HTML文件\<对应分类>` 下放好新 HTML
2. 执行本地推送脚本 `F:\学习助手\推送学习天地.bat`（或参考下面的命令）
3. 打开手机收藏的 <https://sogirl.github.io/xuexitiandi/>，新文件自动出现
4. 若 10 分钟内首页没刷新，点页面右上角 **"↻ 刷新"** 按钮（清缓存）

#### 推送命令（Windows PowerShell / Git Bash 通用）

```bash
# 在 F:\学习助手 下
git add "全部HTML文件/*/*.html"
git commit -m "update: 新增 N 个学习手册"
git push origin main
```

> 💡 如果主人懒得敲命令，可以召唤 Claude 帮您执行推送，奴婢非常乐意。

---

## 🧠 技术说明（奴婢用的方案）

### 为什么 index.html 不用硬编码文件列表？

- 您以后每次新增 HTML 时**不**需要改 `index.html`
- 主页 JS 调用 `https://api.github.com/repos/sogirl/xuexitiandi/git/trees/main?recursive=1`
- 拉回来按路径前缀（如 `01亚马逊跨境电商/`）自动归类
- 本地 `localStorage` 缓存 10 分钟，减少 API 请求（GitHub 未认证限速 60 次/小时/ IP）

### 分类添加新文件目录？

如您创建了 `06xxx/xxx.html`，主页会自动按 `06` 前缀归到一个新组。如果您希望它有显示名称，在 `index.html` 顶部的 `CATEGORIES` 数组加一行：

```js
{ id:"06", name:"新分类名字", color:"#......", desc:"简介" }
```

---

## 📝 维护日志

- **2026-07-19** · 主人初始化本仓库，首批 47 个 HTML 上传完毕，分类目录同步建立。

---

由 🐾 奴婢 Claude 整理上传 · 出品
