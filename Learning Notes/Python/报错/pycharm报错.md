1、
结果：Error:Python packaging tool 'setuptools'not found
原因：setuptools包的版本太高
1、已经安装setuptools，仍然报错Error:Python packaging tool 'setuptools'not found 
2、检查setuptools版本号：命令提示框中输入，pip show setuptools  
3、如果setuptools版本号过高，就下载低版本的setuptools
     ①  卸载原有setuptools：  pip uninstall  setuptools
     ②  安装新版本setuptools:   pip install  setuptools67.6.1
也可以直接在pycharm终端输入：pip install setuptools

2、
在安装某一个包时
错误： module 'pkgutil' has no attribute 'ImpImporter'. Did you mean: 'zipimporter'?
原因：安装python3.12时，由于自带的pip(22.3.1)版本较低，使用了在 python 3.12 中删除的废弃 API pkgutil.ImpImporter，其在 python 3.3 中标记为 deprecated。使用 pip install manim 时报上面这种异常。
并且在pycharm中使用pip install setuptools依然会报“AttributeError: module 'pkgutil' has no attribute 'ImpImporter'. Did you mean: 'zipimporter'?”错。
解决方案：将pip升级到最新的版本
在电脑cmd终端进入本项目所使用的虚拟环境目录下的Scripts目录下，例如 D:\Files\SelfLearningProject\Python\BCI-Projects\wandb_hydra_pytorchlightning_version\wandb_hydra_pytorchlightning_version\venv\Scripts>
使用py -m ensurepip --upgrade
也可以使用python.exe -m pip install --upgrade pip来安装最新版本的pip
然后可以用pip uninstall -y stuptools 卸载掉老版本的setuptools
再使用pip install setuptools安装新版本的setuptools
如果pycharm中还报错，那就在pycharm中先pip list列出包的版本，下载最新版setuptools。




