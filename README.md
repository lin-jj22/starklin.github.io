# Junjian Lin's Academic Homepage

Personal academic homepage hosted on GitHub Pages.

## 部署说明 (Deployment Instructions)

### 步骤 1: 创建 GitHub 仓库

1. **登录 GitHub 账号**（如果没有账号，请先注册：https://github.com/join）

2. **创建新仓库**：
   - 点击 GitHub 右上角的 `+` 按钮，选择 `New repository`
   - **仓库名称必须为**：`yourusername.github.io`（将 `yourusername` 替换为你的 GitHub 用户名）
     - 例如：如果用户名是 `junjianlin`，则仓库名应为 `junjianlin.github.io`
   - 设置为 **Public**（公开仓库）
   - **不要**勾选 "Initialize this repository with a README"
   - 点击 `Create repository`

### 步骤 2: 上传文件到 GitHub

#### 方法 A: 使用 GitHub Web 界面（简单方式）

1. 在仓库页面，点击 `uploading an existing file`
2. 将以下文件拖拽或选择上传：
   - `index.html`
   - `styles.css`
   - `avatar.jpg`（你的头像图片，如果没有，可以先上传一个占位图片）
3. 在页面底部填写提交信息（如 "Initial commit"）
4. 点击 `Commit changes`

#### 方法 B: 使用 Git 命令行（推荐方式）

1. **打开命令行工具**（Windows: PowerShell 或 Git Bash）

2. **初始化 Git 仓库并上传文件**：
   ```bash
   # 进入项目目录
   cd D:\Cursor\Website
   
   # 初始化 Git 仓库
   git init
   
   # 添加所有文件
   git add .
   
   # 提交更改
   git commit -m "Initial commit: Add academic homepage"
   
   # 添加远程仓库（将 YOURUSERNAME 替换为你的 GitHub 用户名）
   git remote add origin https://github.com/YOURUSERNAME/YOURUSERNAME.github.io.git
   
   # 推送到 GitHub（如果是新仓库，使用 -u 参数）
   git branch -M main
   git push -u origin main
   ```

3. **如果遇到认证问题**，GitHub 现在需要 Personal Access Token：
   - 前往 GitHub Settings → Developer settings → Personal access tokens → Tokens (classic)
   - 点击 "Generate new token (classic)"
   - 勾选 `repo` 权限
   - 生成后复制 token，在 Git push 时使用 token 作为密码

### 步骤 3: 启用 GitHub Pages

1. 在 GitHub 仓库页面，点击 **Settings** 标签
2. 在左侧菜单中找到 **Pages**（在 "Code and automation" 部分）
3. 在 "Source" 部分：
   - 选择分支：**main**（或 **master**，取决于你的默认分支）
   - 选择文件夹：**/ (root)**
   - 点击 **Save**

### 步骤 4: 访问你的网站

- 等待 1-2 分钟后，访问：`https://yourusername.github.io`
- 如果显示 404，可能需要等待更长时间（最多 10 分钟）

### 步骤 5: 添加头像

1. 准备一张头像图片（建议尺寸：200x200 像素或更大，正方形）
2. 将图片命名为 `avatar.jpg`（或 `avatar.png`）
3. 上传到仓库根目录
4. 如果使用 PNG 格式，需要在 `index.html` 中将 `avatar.jpg` 改为 `avatar.png`

## 自定义域名（可选）

如果你想使用自定义域名（如 `www.yourname.com`）：

1. 在仓库根目录创建 `CNAME` 文件，内容为你的域名（如 `www.yourname.com`）
2. 在你的域名 DNS 设置中添加以下记录：
   - 类型：`CNAME`
   - 名称：`www`（或 `@`）
   - 值：`yourusername.github.io`
3. 在 GitHub Pages 设置中会自动识别 CNAME 文件

## 更新网站内容

每次修改文件后：

```bash
git add .
git commit -m "Update homepage content"
git push origin main
```

推送后，网站会在几分钟内自动更新。

## 文件说明

- `index.html` - 主页 HTML 文件
- `styles.css` - 样式表文件
- `avatar.jpg` - 个人头像（需要自行添加）
- `README.md` - 本说明文件

## 技术支持

如有问题，请参考：
- [GitHub Pages 官方文档](https://docs.github.com/en/pages)
- [Git 使用教程](https://git-scm.com/book)


