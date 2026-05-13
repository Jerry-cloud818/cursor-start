# 学习计划页面（GitHub Pages）

本仓库包含静态学习计划页面。部署后，任何人可通过浏览器访问你的 GitHub Pages 地址。

- **入口文件**：根目录的 `index.html`（与 `study-plan.html` 内容相同，便于 Pages 默认打开根路径）。
- **自动发布**：推送至 `main` 或 `master` 分支时，由 [GitHub Actions](.github/workflows/github-pages.yml) 部署到 Pages。

---

## 用 GitHub Desktop 发布（推荐）

### 1. 安装并登录

1. 下载安装 [GitHub Desktop](https://desktop.github.com/)（安装程序会带上 Git，一般无需再单独配置）。
2. 打开后按提示 **Sign in to GitHub.com**，用你的 GitHub 账号登录并授权。

### 2. 把本文件夹变成仓库并提交

1. 菜单 **File → Add Local Repository…**（添加本地仓库）。
2. 点 **Choose…**，选中文件夹：`d:\cursor\cursor-start`。
3. 若提示「This directory does not appear to be a Git repository」：
   - 点 **create a repository**（在此文件夹创建仓库），或菜单 **File → New Repository…**；
   - **Local path** 选 `d:\cursor\cursor-start`；
   - **Name** 可填 `cursor-start`（仅本地显示用）；
   - **不要**勾选 “Initialize this repository with a README”（避免多出一个 README 与现有文件冲突）；
   - 点 **Create Repository**。
4. 左侧应列出 `index.html`、`.github` 等变更；在左下角 **Summary** 写一句说明（例如：`Initial study plan site`），点 **Commit to main**。

### 3. 发布到 GitHub

1. 点 **Publish repository**（发布仓库）。
2. **Name**：在 GitHub 上的仓库名（例如 `study-plan`），按需勾选是否 **Keep this code private**。
3. **Organization** 一般选自己的用户名即可。
4. 点 **Publish repository**，等待推送完成。

若按钮是 **Push origin** 而不是 Publish，说明远程已存在，直接 **Push origin** 即可。

### 4. 在网页上打开 GitHub Pages

1. 浏览器打开该仓库页面：**Settings → Pages**。
2. **Build and deployment** 里，**Source** 选 **GitHub Actions**（不要选 “Deploy from a branch”，除非你不用本仓库里的 workflow）。
3. 打开 **Actions** 标签，等待 **Deploy static site to GitHub Pages** 变为绿色成功。若首次被禁用，到 **Settings → Actions → General** 里允许 Actions。

### 5. 访问网址

一般为：

`https://你的用户名.github.io/仓库名/`

具体地址可在 **Settings → Pages** 顶部，或对应一次 Actions 运行结果里查看。

---

## 以后改页面怎么更新

1. 用编辑器改 **`index.html`**（若只改了 `study-plan.html`，请复制覆盖到 `index.html`，否则线上首页可能仍是旧版）。
2. 打开 **GitHub Desktop**，左侧勾选变更，写 Summary，**Commit to main**。
3. 点 **Push origin**。等 Actions 跑完，一两分钟内网站会更新。

---

## 命令行方式（可选）

已安装 Git 且熟悉命令行时，可在 `d:\cursor\cursor-start` 下：

```bash
git init
git add .
git commit -m "Add study plan page and GitHub Pages workflow"
git branch -M main
git remote add origin https://github.com/你的用户名/你的仓库名.git
git push -u origin main
```

若远程仓库已用网页创建过 README 导致冲突，可先：

`git pull origin main --allow-unrelated-histories`

合并后再 `git push`。
