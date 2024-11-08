###### 1、连接谷歌云盘，多个文件之间有联系时
 - 连接google drive
```python
from google.colab import drive
drive.mount('/content/drive')
```
一般工作目录都在/content/目录下

- 使用下面命令查看当前工作目录
```python
import os
os.getcwd()
```
运行结果如下
`/content`

- 使用下面切换到drive所在文件目录下工作
```python
%cd /content/drive/MyDrive/Colab Notebooks/wandb_hydra_pytorchlightning_version
```
运行结果：
`/content/drive/MyDrive/Colab Notebooks/wandb_hydra_pytorchlightning_version`

- 使用下面的命令可以运行一次模块中的文件，如果在colab中修改了某个.py文件的内容，然后在.ipynb文件中用这个模块，一般还是没修改后的结果，此时运行下面的命令便可以返回修改后的结果了
```python
%run "/content/drive/MyDrive/Colab Notebooks/wandb_hydra_pytorchlightning_version/policies/mouse_sleepness_classifiction.py"
```

- colab中模块的引用路径要注意，容易出错，最好把模块的目录也加上，如：
```python
from policies.base_transform import BaseTransform
from policies.mouse_sleepness_classifiction import BaselineTransform
```

- colab中的模块包，最好用.py文件上传到drive上使用，.ipynb文件不支持引用