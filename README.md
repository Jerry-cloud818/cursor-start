# 学习计划页面（GitHub Pages）

本仓库包含静态学习计划页面。部署后，任何人可通过浏览器访问你的 GitHub Pages 地址。

- **入口文件**：根目录的 **`index.html`**（正式页面，请只改这一份）。
- **`study-plan.html`**：自动跳转到 `index.html`，避免维护两份相同代码。
- **自动发布**：推送至 `main` 或 `master` 分支时，由 [GitHub Actions](.github/workflows/github-pages.yml) 部署到 Pages（若你改用「从分支部署」，不依赖该 workflow 亦可）。

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

1. 浏览器打开该仓库：**Settings → Pages**（左侧「Code and automation」下）。
2. 在 **Build and deployment**（构建与部署）区域：
   - 若有下拉菜单，选 **GitHub Actions**；或
   - 选 **Deploy from a branch**，Branch 选 `main`，文件夹选 **`/ (root)`**，再保存（静态 `index.html` 两种方式都可以）。
3. 若使用 **GitHub Actions**：打开 **Actions**，等 **Deploy static site to GitHub Pages** 成功。若 Actions 被禁用，到 **Settings → Actions → General** 里允许。

### 5. 访问网址

一般为：

`https://你的用户名.github.io/仓库名/`

具体地址在 **Settings → Pages** 顶部 **Visit site**，或某次 Actions 运行摘要里。

---

## 部署完成后（收尾清单）

1. **收藏正式地址**：用电脑和手机各打开一次，确认能打开首页（根路径即 `index.html`）。
2. **日常只改 `index.html`**：`study-plan.html` 仅为跳转，不要在里面写业务页面。
3. **数据说明**：学习计划数据存在浏览器 **localStorage**，换设备或清空站点数据后不会同步；换浏览器也是各自一份。
4. **可选**：把下面一行里的占位符改成你的真实地址，方便以后查找（改完提交推送即可）。

```text
线上地址：https://你的用户名.github.io/你的仓库名/
```

---

## 以后改页面怎么更新

1. 用编辑器改 **`index.html`**。
2. 打开 **GitHub Desktop**：勾选变更 → 写 Summary → **Commit to main** → **Push origin**。
3. 若用 Actions 部署，等 workflow 绿勾后约 1～2 分钟站点更新；若用「从分支部署」，通常推送后很快生效。

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
