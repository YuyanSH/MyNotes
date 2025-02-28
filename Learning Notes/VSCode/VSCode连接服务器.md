## 1. vscode连接远程服务器出错
`Permissions for 'D:/Files/SelfLearningProject/SSH-keys/SSH-key-server-1/.ssh/id_rsa' are too open`
### 解释原因：

1. **Git Bash 使用的是 Git 自带的 SSH 客户端**：
    
    - Git Bash 通常会使用它自带的 OpenSSH 客户端，这个客户端在 Windows 上可能没有过多的权限限制。它可能允许你使用权限较宽松的私钥文件（尽管这不是最安全的做法）。
    - Git Bash 可能会自动忽略某些权限警告，或它自身对权限管理有不同的处理方式。
2. **VS Code 使用的是 Windows 系统自带的 OpenSSH 客户端**：
    
    - 在默认情况下，VS Code 会使用 Windows 系统中内置的 OpenSSH 客户端（位于 `C:\Windows\System32\OpenSSH\ssh.exe`），它对私钥文件的权限要求较为严格。
    - Windows 上的 OpenSSH 客户端会要求私钥文件的权限设置为 `600`，即只有文件的所有者可以读取和写入。其他任何用户（包括 `Authenticated Users` 和 `Everyone`）的访问都会被拒绝，这就是你在 VS Code 中看到权限错误的原因。
### 解决方案
要解决这个问题，你可以让 VS Code 和 Git Bash 使用相同的 SSH 客户端。你有两个选择：
#### 1. **让 VS Code 使用 Git Bash 的 SSH 客户端**

你可以告诉 VS Code 使用 Git Bash 自带的 SSH 客户端，而不是默认的 Windows 系统 SSH 客户端。这样，VS Code 就会像 Git Bash 一样处理私钥文件，从而避免权限问题。

**步骤：**

1. 在 VS Code 中打开 **Settings**（设置）。
    
2. 搜索 `remote.SSH.path`。
    
3. 设置 `remote.SSH.path` 为 Git Bash 的 SSH 客户端路径，在本人电脑上是：
`E:/APP/TechSoftware/Git/Git/usr/bin/ssh.exe`
4. 在vs code Settings(JSON)文件中，添加以下配置：
`"E:/APP/TechSoftware/Git/Git/usr/bin/ssh.exe"`


