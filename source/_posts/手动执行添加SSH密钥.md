---
title: 手动执行添加SSH密钥
date: 2022-10-04 20:08:05
tags: "学习"
---

# 自动加载 SSH 密钥并使用 macOS 钥匙串

为了避免每次重启机器都需要执行 `ssh-add --apple-use-keychain` 命令，可以按照以下步骤进行配置：

## 1. 确保 SSH 密钥已添加到钥匙串

执行以下命令，将密钥永久添加到钥匙串中：

```bash
ssh-add --apple-use-keychain ~/.ssh/zinete.com
```

## 2. 配置 SSH 客户端加载密钥

编辑或创建 `~/.ssh/config` 文件，添加以下内容：

```plaintext
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/zinete.com
```

### 配置说明

- `AddKeysToAgent yes`：自动将密钥添加到 SSH Agent。
- `UseKeychain yes`：允许密钥存储在 macOS 钥匙串中。
- `IdentityFile`：指定使用的私钥文件。

## 3. 确保 SSH Agent 启动

macOS 默认会启动 SSH Agent，但可以手动验证：

```bash
eval "$(ssh-agent -s)"
```

## 4. 验证配置

执行以下命令检查密钥是否自动加载：

```bash
ssh-add -l
```

如果显示了密钥的指纹，说明配置成功。

---

通过上述配置，SSH 密钥将在重启后自动从 macOS 钥匙串加载，无需手动执行 `ssh-add`。
