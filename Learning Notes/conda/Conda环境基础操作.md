## 一. 基础应用
### 一. 管理conda
1. 验证conda是否已安装
```bash
conda --version
或者
conda info
或者
conda -v
```
2. 更新conda
```bash
conda update conda
Proceed ([y]/n)? y

运行以下命令更新conda环境
conda update -n <env_name>
例如: conda update -n base conda
```

### 二. 管理环境
#### 1. 创建环境
##### 方法1
1. 创建环境
`conda create -n <my-env>`
2. 创建具有特定python版本的环境
```bash
conda create -n myenv python=3.10
```
3. 要创建具有特定包的环境
```bash
conda create -n myenv scipy
或者
conda create -n myenv python
conda install -n myenv scipy
```
4. 创建具有特定版本包的环境
```bash
conda create -n myenv scipy=0.17.3
或者
conda create -n myenv python
conda install -n myenv scipy=0.17.3
```
5. 创建具有特定版本的python和多个包的环境
```bash
conda create -n myenv python=3.9 scipy=0.17.3 astroid babel
```
6. 要在每次创建新环境时自动安装 pip 或其他程序，请将默认程序添加到 配置文件的[create_default_packages](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/settings.html#config-add-default-pkgs)`.condarc`部分。每次创建新环境时都会安装默认软件包。如果您不想在特定环境中安装默认软件包，请使用以下`--no-default-packages`标志
```bash
conda create --no-default-packages -n myenv python
```
> [!tip] 使用`conda create --help`获取更多帮助

##### 方法2
1. 从文件`environment.yml`创建环境
```bash
conda env create -f environment.yml
其中.yml文件的第一行含有创建环境的名称信息
```
例：一个简单的环境
```
name: stats
dependencies:
  - numpy
  - pandas
```
2. 激活环境
```bash
conda activate myenv
```
3. 验证新环境是否已正确安装
```bash
conda env list
或
conda info --envs
```
4. 退出环境
```bash
conda deactivate
```
> [!tip] 不建议将环境安装到自定义位置，参考官方文档：https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-file-manually

#### 2. 更新环境
1. 更新相应的.yml文件，然后运行
```bash
conda env update --file environment.yml --prune
```
> [!tip] 该`--prune`选项使 conda 删除环境中不再需要的任何依赖项

#### 3.克隆环境
```bash
conda create --name myclone --clone myenv
```
> [!tip] `<myclone>`为新环境名称，`<myenv>`为要复制的现有环境名称

验证是否已复制
```bash
conda info --envs
```

#### 4. 构建相同的conda(创建环境-方法3)
使用显式规范文件在同一个操作系统平台上构建相同的conda环境，同一台机器或者不同机器都可以。
1. 运行`conda list --explicit`生成规格列表(explicit显式)
例如：
```bash
# This file may be used to create an environment using:
# $ conda create --name <env> --file <this file>
# platform: osx-64
@EXPLICIT
https://repo.anaconda.com/pkgs/free/osx-64/mkl-11.3.3-0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/numpy-1.11.1-py35_0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/openssl-1.0.2h-1.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/pip-8.1.2-py35_0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/python-3.5.2-0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/readline-6.2-2.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/setuptools-25.1.6-py35_0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/sqlite-3.13.0-0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/tk-8.5.18-0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/wheel-0.29.0-py35_0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/xz-5.2.2-0.tar.bz2
https://repo.anaconda.com/pkgs/free/osx-64/zlib-1.2.8-3.tar.bz2
```
2. 将此规范列表创建为当前工作目录中的文件，运行
```bash
conda list --explicit > spec-file.txt
```
> [!tip] `spec-file.txt`为文件名

3. 使用spec文件在同一台机器或者另一台机器上创建相同的环境
```bash
conda create --name myenv --file spec-file.txt
```
4. 使用spec文件将列出的包安装在现有环境中
```bash
conda install --name myenv --file spec-file.txt
```
> [!tip] Conda 在从 spec 文件安装时不会检查体系结构或依赖项。为确保软件包正常工作，请确保该文件是从工作环境创建的，并在相同的体系结构、操作系统和平台上使用它，例如 linux-64 或 osx-64

#### 5. 激活环境
1. 激活环境
```bash
conda activate myenv
```
2. 在激活的环境中运行可执行文件
```bash
conda run <file_name>
```

#### 6.停用环境
```bash
conda deactivate
```

#### 7.查看环境列表
1. 使用下列命令
```bash
conda env list
或者
conda info --envs
```

#### 8. 查看一个环境中安装的包的列表
1. 如果环境未激活
```bash
conda list -n myenv
```
2. 如果环境已经激活
```bash
conda list
```
3. 检查特定包是否安装在环境中
```bash
conda list -n myenv scipy
```

#### 9. 在环境中使用pip
1. 如果要在一个环境中使用`pip`，运行
```bash
conda install -n myenv pip
conda activate myenv
pip <pip_subcommand>
```
>[!warning]  同时使用 pip 和 conda 时可能会出现问题。结合使用 conda 和 pip 时，最好使用隔离的 conda 环境。只有在使用 conda 安装了尽可能多的软件包后，才能使用 pip 安装剩余的软件。如果需要修改环境，最好创建一个新环境，而不是在 pip 之后运行 conda。在适当的情况下，应将 conda 和 pip 要求存储在文本文件中。
>

>[!tip] **尽量不要使用pip** 一旦使用了pip，conda将不会意识到这些变化，要安装其他conda 包最好重新创建环境。

#### 10. 设置环境变量
>[!tip] 先不要使用这个

#### 11. 保存环境变量
>[!tip] 先不要使用这个

#### 12. 分享环境
1. 激活要导出的环境
```bash
conda activate myenv
```
2. 将激活的环境导出到新文件
```bash
conda env export > environment.yml
```
>[!tip] 该文件处理环境的 pip 包和 conda 包。

#### 13. 导出初始设置的包
如果使用`conda env export`将会导出所有包
这时可以使用`conda env export --from-history`
- 例如：
如果创建了一个环境，安装了python和一个包
```bash
conda install python=3.7 codecov
```
>[!warning] 这将下载并安装大量附加软件包来解决依赖关系问题。这将引入可能不跨平台兼容的软件包。

如果使用`conda env export`，将导出所有的包，包括额外的依赖项的包。但是如果使用`conda env export --from-history`
```
(env-name) ➜  ~ conda env export --from-history
name: env-name
channels:
  - conda-forge
  - defaults
dependencies:
  - python=3.7
  - codecov
prefix: /Users/username/anaconda3/envs/env-name
```

#### 14. 手动创建一个环境文件
1. 一个简单的环境文件：
```
name: stats
dependencies:
  - numpy
  - pandas
```
2. 一个复杂的环境文件
```
name: stats2
channels:
  - javascript
dependencies:
  - python=3.9
  - bokeh=2.4.2
  - conda-forge::numpy=1.21.*
  - nodejs=16.13.*
  - flask
  - pip
  - pip:
    - Flask-Testing
```
>[!note] 请注意，在复杂环境文件中定义一些版本时使用了通配符`*`。保持主版本和次版本固定不变，同时允许补丁为任意数字，这样就可以使用环境文件获得任何错误修复，同时还能保持环境的一致性。有关软件包安装值的更多信息，请参阅[软件包搜索和安装规范](https://docs.conda.io/projects/conda/en/latest/user-guide/concepts/pkg-search.html) 。
>****在 “通道 ”之外指定通道****  
有时，你可能想指定 conda 将使用哪个通道来安装特定软件包。要做到这一点，在dependencies: 中使用channel::package语法，如上文中的conda-forge::numpy（版本号可选）。指定的频道不需要出现在channels:列表中，如果你想从社区频道（如conda-forge）安装某些软件包，但不是_所有_软件包，这一点非常有用。

您可以通过`nodefaults`添加到频道列表来排除默认频道
```
channels:
  - javascript
  - nodefaults
```
这相当于在大多数`conda`命令中传递`--override-channels`选项。  
在`environment.yml`的通道列表中添加`节点` `默认值`与从`.condarc`文件的[通道列表](https://docs.conda.io/projects/conda/en/latest/user-guide/configuration/settings.html#config-channels)中删除`默认值`类似。不过，更改`environment.yml`只影响一个 conda 环境，而更改`.condarc`会影响所有环境。  
有关从`environment.yml`文件创建环境的详细信息，请参阅[从 environment.yml 文件创建环境](https://docs.conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html#create-env-from-file) 。

#### 15. 恢复一个环境
1. Conda会保留对环境做的所有更改的历史记录，要列出当前环境的每个更改的历史记录，执行
```bash
conda list --revisions
```
2. 要恢复到以前版本
```bash
conda install --revision=REVNUM
或
conda install --rev REVNUM
```
>[!note] 使用revision版本号替换REVNUM

例如：If you want to restore your environment to revision 8, run `conda install --rev 8`.

#### 16. 删除环境
```bash
conda remove --name myenv --all
or
conda env remove --name myenv
```

### 三. 管理频道
#### 1. 安装包时，指定频道
1. 命令行使用channel
```bash
conda install scipy --channel conda-forge
```
2. 使用多次传递函数指定多个通道
```bash
conda install scipy --channel conda-forge --channel bioconda
```
第一个优先级高于第二个优先级


### 四. 管理包
#### 1. 搜索包
1. 检查特定包是否支持安装
```bash
conda search scipy
```
2. 查看是否可以从Anaconda.org 安装特定软件包
```bash
conda search --override-channels --channel defaults scipy
```
3. 查看特定频道中是否存在特定包并且可以安装
```bash
conda search --override-channel --channel http://conda.anaconda.org/mutirri iminuit
```
#### 2. 安装包
1. 将特定包安装到现有环境中
```bash
conda install --name myenv scipy
```
2. 若未指定环境名称，则安装到当前环境中
```bash
conda install scipy
```
3. 安装特定版本的包
```bash
conda install scipy=0.15.0
```
4. 一次安装多个包
```bash
conda install scipy curl
```
>[!note] 最好一次安装所有包，以便所有依赖项都可以同时安装
5. 一次安装多个包并指定包的版本
```bash
conda install scipy=0.15.0 curl=7.26.0
```
#### 3. 从Anaconda.org中安装包
使用`conda install`无法安装的包，可以从anaconda.org中获取
1. 在浏览器中，搜索 [http://anaconda.org](http://anaconda.org/)
2. 搜索要找的包比如`bottleneck`
3. 查看包的详情页，详情页会显示频道的名字，例如这个例子中的频道是"pandas"
4. 安装
```bash
conda install -c pandas bottleneck
```
5. 检查
```bash
conda list
```
#### 4. 安装非conda包
如果无法使用conda安装，请尝试使用 [conda-forge](https://conda-forge.org/search.html)查找并安装它。如果仍然无法安装，则使用pip安装。
要安装非conda包
1. 激活想要放置程序的环境
```bash
conda activate myenv
```
2. 使用pip安装see之类的程序
```bash
pip install see
```
3. 检查
```bash
conda list
```
#### 5. 查看已安装包的列表
1. 在一个激活的环境中时
```bash
conda list
```
2. 未激活的环境
```bash
conda list -n myenv
```
#### 6. 列出包依赖项
要查找环境中哪些包依赖于特定包，没有一个特定的conda命令，需要一系列的步骤
1. 列出特定包运行所需的依赖项
```bash
conda search package_name --info
```
2. 找到安装的包缓存目录
```bash
conda info
```
3. 查找软件包依赖项。默认情况下，Anaconda/Miniconda 将软件包存储在 ~/anaconda/pkgs/（或 macOS Catalina 上的 ~/opt/pkgs/）中。每个软件包都有一个 index.json 文件，其中列出了软件包的依赖项。此文件位于 ~anaconda/pkgs/package_name/info/index.json。
4. 现在使用grep搜索所有index.json文件
```bash
grep package_name ~/anaconda/pkgs/*/info/index.json
```
结果将是包含 <package_name> 的任何内容的完整包路径和版本。
例如
```bash
grep numpy ~/anaconda/pkgs/*/info/index.json
```
上述命令的输出：
```bash
/Users/testuser/anaconda3/pkgs/anaconda-4.3.0-np111py36_0/info/index.json: numpy 1.11.3 py36_0
/Users/testuser/anaconda3/pkgs/anaconda-4.3.0-np111py36_0/info/index.json: numpydoc 0.6.0 py36_0
/Users/testuser/anaconda3/pkgs/anaconda-4.3.0-np111py36_0/info/index.json: numpy 1.11.3 py36_0
```

请注意，这也返回了“numpydoc”，因为它包含字符串“numpy”。要获得更具体的结果集，您可以添加 < 和 >
#### 7. 更新包
1. 更新特定包
```bash
conda up date biopython
```
2. 更新python
```bash
conda update python
```
3. 更新conda本身
```bash
conda update conda
```
4. 更新anaconda元包
```bash
conda update conda 
conda update anaconda
```
#### 8. 固定软件包
在`conda-meta`目录中，添加一个名为`pinned`的文件，其中包含不想更新的软件列表。
示例：下面的文件强制munpy停留在1.7系列。强制Scipy停留在0.14.2版本：
```bash
numpy 1.7.*
scipy ==0.14.2
```
使用`--no-pin`标志可覆盖软件包的更新限制，在终端中运行
```bash
conda update numpy --no-pin
```
#### 9. 自动将默认包添加到新环
1. 打开终端窗口并运行
```bash
conda config --add create_default_packages PACKAGENAME1 PACKAGENAME2
```
2. 创建新环境并且默认包将安装在所有环境中
3. 在命令行使用
```bash
--no-default-packages
```
#### 10. 删除包
1. 在myenv等环境中删除Scipy包
```bash
conda remove -n myenv scipy
```
2. 删除当前环境中的Scipy包
```bash
conda remove scipy
```
3. 一次删除多个包
```bash
conda remove scipy curl
```
4. 检查
```bash
conda list
```


### 五. 管理python
#### 1. 列出可安装的python版本
1. 列出名称中包含文本的所有包
```bash
conda search python
```
2. 列出全名完全正确的软件包
```bash
conda search --full-name python
```
#### 2. 安装不同版本的python
1. 创建新环境
```bash
conda create -n py39 python=3.9
```
2. 激活新环境
3. 验证
```bash
python --version
```
### 六. 创建项目
- 使用`environment.yml`文件创建一个新的python项目
#### 1. 创建项目文件
1. 创建目录
```bash
mkdir my-project
```
2. 在VSCODE中创建`environment.yml`文件并编辑
```
name: my-project
channels:
  - defaults
dependencied:
  - python
```
#### 2. 创建环境
```bash
conda env create --file environment.yml
conda activate my-project
```
#### 3. 更新环境
1. 更新`environment.yml`文件
```
name: my-project
channels:
  - defaults
dependencies:
  - python
  - pandas  # <-- This is our new dependency
```
2. 更新
```bash
conda env update --file environment.yml
```
### 七. 查看命令行帮助
```bash
conda --help
conda -h
conda create -h
```

## 二. 配置
### 一. 使用.condarc conda配置文件
#### 1. 概述
