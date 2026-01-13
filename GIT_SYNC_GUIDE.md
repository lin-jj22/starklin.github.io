# Git 同步指南

本指南将帮助您将当前文件夹与 GitHub 仓库 `https://github.com/lin-jj22/lin-jj22.github.io.git` 进行同步。

## 前提条件

1. 确保已安装 Git。如果未安装，请访问 https://git-scm.com/download/win 下载安装。
2. 确保已配置 Git 用户信息（如果未配置）：
   ```bash
   git config --global user.name "您的用户名"
   git config --global user.email "您的邮箱"
   ```

## 首次设置（如果当前文件夹还不是 Git 仓库）

### 步骤 1: 初始化 Git 仓库
```bash
git init
```

### 步骤 2: 添加远程仓库
```bash
git remote add origin https://github.com/lin-jj22/lin-jj22.github.io.git
```

### 步骤 3: 检查远程仓库配置
```bash
git remote -v
```

## 日常同步操作

### 方案 A: 将本地文件推送到 GitHub（上传本地更改）

#### 1. 查看当前状态
```bash
git status
```

#### 2. 添加所有更改的文件
```bash
git add .
```
或者添加特定文件：
```bash
git add index.html styles.css avatar.jpg
```

#### 3. 提交更改
```bash
git commit -m "描述您的更改内容"
```

#### 4. 推送到 GitHub
```bash
git push -u origin main
```
如果您的默认分支是 `master`，则使用：
```bash
git push -u origin master
```

### 方案 B: 从 GitHub 拉取最新更改（下载远程更改）

#### 1. 拉取并合并远程更改
```bash
git pull origin main
```
或
```bash
git pull origin master
```

#### 2. 如果出现冲突，需要解决冲突后再提交

### 方案 C: 完整同步（先拉取再推送）

```bash
# 1. 先拉取远程更改
git pull origin main

# 2. 如果有本地更改，添加并提交
git add .
git commit -m "您的提交信息"

# 3. 推送到远程
git push origin main
```

## 常用命令速查

| 命令 | 说明 |
|------|------|
| `git status` | 查看当前仓库状态 |
| `git add .` | 添加所有更改的文件到暂存区 |
| `git commit -m "消息"` | 提交更改 |
| `git push origin main` | 推送到远程仓库 |
| `git pull origin main` | 从远程仓库拉取更新 |
| `git log` | 查看提交历史 |
| `git diff` | 查看未暂存的更改 |
| `git remote -v` | 查看远程仓库地址 |

## 如果仓库已存在但需要重新连接

如果当前文件夹已经是 Git 仓库，但远程地址不正确：

```bash
# 查看当前远程地址
git remote -v

# 移除旧的远程地址（如果需要）
git remote remove origin

# 添加正确的远程地址
git remote add origin https://github.com/lin-jj22/lin-jj22.github.io.git

# 验证
git remote -v
```

## 注意事项

1. **首次推送**：如果 GitHub 仓库已有内容，可能需要先拉取：
   ```bash
   git pull origin main --allow-unrelated-histories
   ```

2. **分支名称**：确认您的默认分支是 `main` 还是 `master`，使用相应的命令。

3. **认证**：GitHub 已不再支持密码认证，需要使用：
   - Personal Access Token (PAT)
   - SSH 密钥
   - GitHub CLI

4. **冲突处理**：如果本地和远程都有更改，可能需要解决冲突后再推送。

## 快速同步脚本

您可以创建一个批处理文件来简化操作：

**Windows (sync.bat)**:
```batch
@echo off
git add .
git commit -m "更新文件"
git push origin main
pause
```

使用方法：双击运行 `sync.bat` 即可自动同步。


