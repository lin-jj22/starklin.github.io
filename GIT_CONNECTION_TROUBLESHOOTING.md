# Git 连接 GitHub 故障排除指南

## 当前错误

```
fatal: unable to access 'https://github.com/lin-jj22/lin-jj22.github.io.git/': 
Failed to connect to github.com port 443 after 21102 ms: Could not connect to server
```

## 问题分析

- ✅ 网络连接正常（ping github.com 成功）
- ❌ HTTPS (端口 443) 连接被阻止
- 可能原因：防火墙、代理设置、或网络策略限制

## 解决方案

### 方案 1: 配置代理（如果您使用代理）

如果您在使用代理（如公司网络、VPN 等），需要配置 Git 使用代理：

```bash
# 设置 HTTP 代理（替换为您的代理地址和端口）
git config --global http.proxy http://proxy.example.com:8080
git config --global https.proxy https://proxy.example.com:8080

# 如果代理需要认证
git config --global http.proxy http://username:password@proxy.example.com:8080

# 取消代理设置（如果不需要）
git config --global --unset http.proxy
git config --global --unset https.proxy
```

### 方案 2: 使用 SSH 方式（推荐）

SSH 方式通常更稳定，不受 HTTPS 端口限制影响。

#### 步骤 1: 检查是否已有 SSH 密钥

```bash
ls ~/.ssh
```

如果看到 `id_rsa` 或 `id_ed25519` 文件，说明已有密钥。

#### 步骤 2: 生成 SSH 密钥（如果没有）

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

按回车使用默认路径，设置密码（可选）。

#### 步骤 3: 添加 SSH 密钥到 GitHub

1. 复制公钥内容：
```bash
cat ~/.ssh/id_ed25519.pub
```

2. 登录 GitHub → Settings → SSH and GPG keys → New SSH key
3. 粘贴公钥内容并保存

#### 步骤 4: 测试 SSH 连接

```bash
ssh -T git@github.com
```

如果看到 "Hi username! You've successfully authenticated..." 说明成功。

#### 步骤 5: 更改远程仓库地址为 SSH

```bash
git remote set-url origin git@github.com:lin-jj22/lin-jj22.github.io.git
```

#### 步骤 6: 验证并推送

```bash
git remote -v
git push origin main
```

### 方案 3: 检查 Windows 防火墙

1. 打开"Windows Defender 防火墙"
2. 检查是否阻止了 Git 或 PowerShell
3. 临时关闭防火墙测试（不推荐长期关闭）

### 方案 4: 使用 GitHub CLI（gh）

如果命令行方式都失败，可以尝试使用 GitHub CLI：

```bash
# 安装 GitHub CLI（如果未安装）
winget install --id GitHub.cli

# 登录
gh auth login

# 推送（使用 gh 命令）
gh repo sync
```

### 方案 5: 使用 VPN 或更换网络

如果是在受限网络环境（如公司网络），尝试：
- 使用手机热点
- 连接 VPN
- 更换网络环境

### 方案 6: 检查 DNS 设置

```bash
# 刷新 DNS 缓存
ipconfig /flushdns

# 尝试使用不同的 DNS（如 8.8.8.8）
```

## 快速测试命令

```bash
# 测试 HTTPS 连接
curl -I https://github.com

# 测试 SSH 连接
ssh -T git@github.com

# 查看当前 Git 配置
git config --list

# 查看远程仓库地址
git remote -v
```

## 推荐操作顺序

1. **首先尝试方案 2（SSH 方式）** - 最稳定可靠
2. 如果 SSH 不可用，尝试方案 1（配置代理）
3. 如果都不行，尝试方案 4（GitHub CLI）
4. 最后考虑方案 5（更换网络）

## 注意事项

- 提交已经成功（`[main 0327a04] Update homepage content`），只是推送失败
- 您的更改已保存在本地，不会丢失
- 成功推送后，更改才会同步到 GitHub

