# Git 安装指南（Windows）

## 问题诊断

您遇到的错误 `无法将"git"项识别为 cmdlet、函数、脚本文件或可运行程序的名称` 表示：
- **Git 未安装**，或
- **Git 已安装但未添加到系统 PATH 环境变量**

## 解决方案

### 方法 1: 安装 Git for Windows（推荐）

#### 步骤 1: 下载 Git
1. 访问官方下载页面：https://git-scm.com/download/win
2. 下载会自动开始，或点击下载按钮
3. 下载的文件通常是 `Git-2.x.x-64-bit.exe` 格式

#### 步骤 2: 安装 Git
1. 双击下载的安装程序
2. **重要安装选项**：
   - ✅ **选择 "Git from the command line and also from 3rd-party software"**（这将自动添加到 PATH）
   - ✅ 其他选项保持默认即可
3. 点击 "Next" 完成安装

#### 步骤 3: 验证安装
安装完成后，**重新打开 PowerShell 或命令提示符**，然后运行：
```bash
git --version
```
如果显示版本号（如 `git version 2.42.0`），说明安装成功！

### 方法 2: 使用包管理器安装（如果您已安装）

#### 使用 Chocolatey（如果已安装）
```powershell
choco install git
```

#### 使用 Winget（Windows 10/11 自带）
```powershell
winget install --id Git.Git -e --source winget
```

### 方法 3: 检查是否已安装但未添加到 PATH

如果 Git 已安装但未添加到 PATH：

1. **找到 Git 安装位置**（通常在以下位置之一）：
   - `C:\Program Files\Git\bin\git.exe`
   - `C:\Program Files (x86)\Git\bin\git.exe`
   - `C:\Users\您的用户名\AppData\Local\Programs\Git\bin\git.exe`

2. **手动添加到 PATH**：
   - 按 `Win + R`，输入 `sysdm.cpl`，回车
   - 点击"高级"选项卡 → "环境变量"
   - 在"系统变量"中找到 `Path`，点击"编辑"
   - 点击"新建"，添加 Git 的 bin 目录路径（如 `C:\Program Files\Git\bin`）
   - 点击"确定"保存所有更改
   - **重新打开 PowerShell**

## 安装后配置

### 1. 配置用户信息（首次使用必须）
```bash
git config --global user.name "您的用户名"
git config --global user.email "您的邮箱"
```

### 2. 验证配置
```bash
git config --list
```

## 安装完成后，继续同步操作

安装 Git 后，回到您的项目目录，执行：

```bash
# 1. 初始化仓库
git init

# 2. 添加远程仓库
git remote add origin https://github.com/lin-jj22/lin-jj22.github.io.git

# 3. 检查远程配置
git remote -v

# 4. 添加文件
git add .

# 5. 提交
git commit -m "初始提交"

# 6. 推送到 GitHub
git push -u origin main
```

## 快速安装链接

- **官方下载**：https://git-scm.com/download/win
- **GitHub Desktop**（图形界面，可选）：https://desktop.github.com/

## 常见问题

### Q: 安装后仍然无法识别 git 命令？
A: 
1. 完全关闭并重新打开 PowerShell/命令提示符
2. 检查 PATH 环境变量是否包含 Git 的 bin 目录
3. 尝试重启计算机

### Q: 如何检查 Git 是否已安装？
A: 运行 `git --version`，如果显示版本号则已安装。

### Q: 安装时应该选择哪些选项？
A: 推荐选择 "Git from the command line and also from 3rd-party software"，这样会自动配置 PATH。

## 下一步

安装完成后，请参考 `GIT_SYNC_GUIDE.md` 文件了解如何同步您的文件。


