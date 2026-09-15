# 金彦祺 · 个人主页

访问地址（部署后）：**https://3yyyyyyyyyy.github.io**

## 项目结构

```
docs/
├── index.html          # 首页（Hero + 关于我 + 项目卡片 + 技能）
├── resume.html         # 电子版简历页（A4 打印友好）
├── projects.json       # 项目数据（卡片内容由它驱动，加项目改这里即可）
├── assets/
│   └── photo.png       # 个人照片
└── README.md           # 本文件
```

## 本地预览

需要走 HTTP 协议（首页用 fetch 加载 `projects.json`，`file://` 协议会被浏览器 CORS 拦截）：

```bash
cd docs
python -m http.server 8000
```

浏览器访问 <http://localhost:8000> 。

## 部署到 GitHub Pages

### 1. 新建同名仓库

在 GitHub 新建仓库，名字必须与用户名**完全一致**：

```
3yyyyyyyyyy.github.io
```

（设置仓库为 Public，初始化时不要勾选 README，保持空仓库）

### 2. 推送站点文件

把 `docs/` 目录下**所有内容**（不是 docs 文件夹本身，是里面的文件）推到仓库 `main` 分支根目录：

```bash
cd docs
git init
git remote add origin https://github.com/3yyyyyyyyyy/3yyyyyyyyyy.github.io.git
git branch -M main
git add .
git commit -m "init personal homepage"
git push -u origin main
```

### 3. 访问主页

推送后等待 1-2 分钟，访问：

**https://3yyyyyyyyyy.github.io**

即可看到主页。如果 5 分钟后仍打不开，进入仓库 `Settings → Pages`，确认 Source 为 `main` 分支根目录。

## 后续如何添加新项目

只需编辑 `projects.json`，加一项：

```json
{
  "title": "新项目名称",
  "description": "项目简介，一两句话",
  "tags": ["Python", "测试"],
  "github_url": "https://github.com/3yyyyyyyyyy/新项目",
  "demo_url": "",
  "status": "active",
  "year": "2026"
}
```

字段说明：

| 字段 | 说明 |
|---|---|
| `title` | 项目标题 |
| `description` | 项目简介 |
| `tags` | 技术栈标签数组 |
| `github_url` | GitHub 仓库链接（无则留空字符串） |
| `demo_url` | 在线 demo 链接（无则留空字符串） |
| `status` | `active`（正常显示）或 `coming_soon`（占位卡片） |
| `year` | 年份，显示在卡片右下 |

改完 `git add projects.json && git commit -m "add 新项目" && git push` 即可生效。

## 修改简历

直接编辑 `resume.html` 即可。`resume.html` 是 A4 单页打印友好版式，浏览器中 `Ctrl+P` 可直接打印或另存为 PDF。

## 修改照片

替换 `assets/photo.png`（建议保持 PNG 格式，正方形或竖向比例，分辨率 ≥ 400×400）。
