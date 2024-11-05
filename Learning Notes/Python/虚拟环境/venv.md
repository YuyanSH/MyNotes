首先进入CMD面板

一、创建虚拟环境
可以通过命令 E： 进入到相应的磁盘中，cd ..退出此目录
然后用命令 dir 列出该文件下的所有目录
再通过 cd 进入到相应目录中去
然后用 python -m venv venvname 创建一个名为“venvname”的虚拟环境
在该目录的 Scripts 下使用 activate 即可激活虚拟环境，当然直接在 Scripts 目录下
使用 python 后
import sys
sys.path
可以看到也是在虚拟环境中
然后 "Ctrl + z"退出python
deactivate 退出虚拟环境
pip -h 可以查看pip的一些功能
在Pycharm中就可以找到已经创建好的虚拟环境

二、保存和复制虚拟环境
进入虚拟环境下的Scripts然后 activate 激活
在里面 pip -h 列出pip的一些功能，其中有一个 pip freeze 可以将包打包成"requirements"的格式进行保存，可供他人下载
例：
使用 pip freeze 
然后 requirements1.txt 就可以将包打包成名为"requirements1"的 .txt 格式文件
(requirements使用参见 https://blog.csdn.net/qq_42623386/article/details/124658336)
(虚拟环境详见 https://www.cnblogs.com/bonheur/p/12315575.html)

三、快速创建虚拟环境
