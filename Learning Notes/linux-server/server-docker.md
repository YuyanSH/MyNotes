### 1、连接服务器前的准备工作
#### 1、生成新的密钥
##### 1. 打开 Git Bash，然后输入以下命令来生成新的 SSH 密钥
```bash
ssh-keygen -t rsa -b 4096 -C "2735389670@qq.com"
```
`-t rsa` 表示使用 RSA 算法，`-b 4096` 指定了 4096 位的密钥长度
##### 2.指定密钥存放路径
当提示 `Enter file in which to save the key` 时，输入你想要保存密钥的位置，例如
```bash
/d/Files/SelfLearningProject/SSH-keys/SSH-key-github-1/.ssh/id_rsa
```
##### 3.设置密钥密码（可选）
- 如果你想给密钥添加密码保护，可以在提示 `Enter passphrase` 时输入密码（此密码在每次使用密钥时都要输入）
- 如果不想设置密码，可以直接按回车跳过
##### 4.C:\Users\lenovo\.ssh讲解
`C:\Users\lenovo\.ssh` 文件夹是 SSH 的默认配置目录，它通常用于存储 SSH 的密钥文件、配置文件和连接记录等。具体文件的用途如下：
1. **`known_hosts` 文件**：
   - 该文件存储了你曾经连接过的远程主机的公钥指纹。每当你连接到一个新主机时，SSH 会将该主机的指纹记录在 `known_hosts` 文件中，以防止中间人攻击。
   - 当你再次连接到该主机时，SSH 会检查主机指纹是否匹配。如果指纹匹配，则继续连接；如果不匹配，则会给出警告，以防止连接到伪装的主机。
2. **`known_hosts.old` 文件**：
   - 这是 `known_hosts` 文件的备份文件。SSH 会在你手动修改 `known_hosts` 文件（例如删除某些主机指纹）或系统自动更新时创建一个 `.old` 备份，以防出现意外问题，可以还原记录。
3. **私钥文件（如 `id_rsa`）**：
   - `id_rsa` 是你的私钥文件，用于对你发往远程服务器的数据进行签名。这个文件需要严格保护，不能泄露，否则会导致你的身份被冒用。
4. **公钥文件（如 `id_rsa.pub`）**：
   - `id_rsa.pub` 是对应的公钥文件，可以分享给远程服务器，以便该服务器能够验证你的身份。
5. **`config` 文件**（可选）：
   - `config` 是一个 SSH 配置文件，你可以在其中定义常用的 SSH 设置，比如特定主机的别名、指定的私钥文件路径、用户名等。这样可以简化连接命令。
###### `.ssh` 目录中文件的用途总结
- `known_hosts` 和 `known_hosts.old`：用于记录和验证连接主机的身份。
- `id_rsa` 和 `id_rsa.pub`：本地生成的 SSH 密钥对，分别用于身份验证和身份标识。
- `config`：保存 SSH 连接的自定义设置。
这些文件共同作用，保障了 SSH 连接的安全性和便捷性。
##### 5.查看公钥
```bash
cat /d/Files/SelfLearningProject/SSH-keys/SSH-key-github-1/.ssh/id_rsa.pub
```


### 2、连接服务器
可以从git-bash中访问

- 连接SIOM-server服务器
```bash
ssh SIOM-server
```

- 列出所有镜像
```bash
docker images
```

- 查看全部容器
```bash
docker ps -a
```

- 创建一个新容器
```bash
 docker run -itd --gpus all --cpus 64 -v /home/mingliangxu:/home_local -p 8001:8001 --name SpikeInterface --shm-size 64G 030e9072eba0 /bin/zsh
```

##### 解析命令：
```bash
docker run -itd --gpus all --cpus 64 -v /home/mingliangxu:/home_local -p 8001:8001 --name SpikeInterface --shm-size 64G spikeinterface_with_bash /bin/bash
```

1. **`docker run`**：
   - 这是启动一个新的容器的命令。

2. **`-itd`**：
   - `-i`：让容器保持运行（即进入交互模式）。
   - `-t`：分配一个伪终端（让你可以在容器中使用命令行界面）。
   - `-d`：在后台启动容器，运行后不会阻塞终端。

3. **`--gpus all`**：
   - 让容器使用所有可用的 GPU。这是为了在容器中运行需要 GPU 支持的任务（例如深度学习模型训练）。

4. **`--cpus 64`**：
   - 限制容器可以使用的 CPU 核心数，这里设置为 64。

5. **`-v /home/mingliangxu:/home_local`**：
   - 这将宿主机的 `/home/mingliangxu` 目录挂载到容器内的 `/home_local` 目录。这意味着你可以在容器内访问宿主机的这些文件。
   
6. **`-p 8001:8001`**：
   - 将容器的 8001 端口映射到宿主机的 8001 端口。这样你就可以从宿主机访问容器中的服务（如果该端口上有服务在运行）。

7. **`--name SpikeInterface`**：
   - 给容器命名为 `SpikeInterface`。这样，你可以通过该名称引用容器，而不是使用容器 ID。

8. **`--shm-size 64G`**：
   - 设置容器共享内存的大小为 64GB。对于运行大规模应用（如深度学习模型）时，增加共享内存有助于提高性能。

9. **`spikeinterface_with_bash`**：
   - 这是容器的镜像名称。它告诉 Docker 使用名为 `spikeinterface_with_bash` 的镜像来创建容器。这个镜像应该包含所需的软件和环境。

10. **`/bin/bash`**：
    - 容器启动后运行的命令，这里是启动 `bash` shell，即进入容器内的终端环境。

##### 总结：
这行命令的作用是：

- 启动一个名为 `SpikeInterface` 的新 Docker 容器；
- 将宿主机的 `/home/mingliangxu` 目录挂载到容器内的 `/home_local`；
- 分配 64 个 CPU 核心和所有的 GPU；
- 设置容器的共享内存为 64GB；
- 将容器的 8001 端口映射到宿主机的 8001 端口；
- 并在容器内启动一个 `bash` shell。

通过此命令，你创建了一个隔离的环境，适用于需要大量计算资源（如 GPU、CPU）并且与宿主机文件系统共享数据的应用程序。`

 如果出现该镜像里面没有zsh终端的错误的话，该容器仍然会被创建，只不过不能以zsh终端启动，想要换别的启动方式，方法如下：
*方法1*
1. 删除并停止旧容器：
```bash
docker stop SpikeInterface
docker rm SpikeInterface
```
2. 改用启动bash shell
```bash
docker run -itd --gpus all --cpus 64 -v /home/mingliangxu:/home_local -p 8001:8001 --name SpikeInterface --shm-size 64G 030e9072eba0 /bin/bash
```
`容器名称：SpikeInterface
`使用的镜像：spikeinterface
`启动zsh shell

*方法2*
为新容器指定一个不同的名称（推荐方法1）
```bash
docker run -itd --gpus all --cpus 64 -v /home/mingliangxu:/home_local -p 8001:8001 --name SpikeInterface_new --shm-size 64G 030e9072eba0 /bin/bash
```

*方法3*
当然也可以将现有容器的镜像（即创建该容器时使用的镜像）保存为一个新的镜像，然后使用该镜像重新创建容器，但如继续使用这个容器名字，仍然需要删除原容器
1. 将现有的容器保存为一个新的镜像
```bash
docker commit <container_id> spikeinterface_with_bash
```
 创建了一个名为 `spikeinterface_with_bash` 的新镜像，它是基于原始的 `spikeinterface` 镜像，但包含了在容器内所做的修改（如安装 bash）
 2. 删除容器
```bash
docker rm SpikeInterface
```
3. 之后就可以创建新容器啦
```bash
docker run -itd --gpus all --cpus 64 -v /home/mingliangxu:/home_local -p 8001:8001 --name SpikeInterface --shm-size 64G spikeinterface_with_bash /bin/bash
```
`
- 连接到容器的现有终端
```bash
docker attach <container_name or container_id>
```

- 以bash shell终端进入容器
```bash
 docker exec -it SpikeInterface /bin/bash
```

创建新容器后一般会自动启动但若是要进入之前创建的容器的话
- 启动现有容器
```bash
docker start <container_name or container_id>
```

- 退出容器
1. 输入 `exit` 或 `Ctrl + D` 可以退出容器。
2. 按 `Ctrl + P` 和 `Ctrl + Q` 可以断开与容器的连接而不停止容器。

- 停止容器
```bash
docker stop <container_name or container_id>
```

 - 删除容器
```bash
docker rm SpikeInterface
```

- 删除镜像
```bash
docker rmi <image_name or image_id>
```

- 退出服务器
```bash
exit
```

### 3、进入容器后的操作
- 查看当前目录内容
1. 查看当前目录的文件和子目录
```bash
ls
```
2. 查看详细信息（例如权限、大小、修改时间等），可以使用 `-l` 选项
```bash
ls -l
```
3. 如果目录内容太多，你可以加上 `-a` 选项来查看所有文件（包括隐藏文件）
```bash
ls -la
```
- 查看其他目录内容
1. 要查看其他目录的文件，可以使用 `ls` 命令并指定路径。例如，查看 `/home` 目录
```bash
ls /home
```
2. 如果你想查看更深层次的文件或目录，可以直接进入子目录。进入 `/home` 目录后，再使用 `ls` 查看该目录下的内容
```bash
cd /home
ls
```
- 查看文件内容
1. 使用`cat`查看文件内容
```bash
cat <filename>
```
- 查找文件
1. 如果你想查找特定文件，可以使用 `find` 命令。例如，查找文件名包含 `config` 的所有文件
```bash
find / -name "*config*"
```
- 查看磁盘空间
1. 如果你想查看容器的磁盘空间使用情况，可以使用 `df` 命令
```bash
df -h
```
