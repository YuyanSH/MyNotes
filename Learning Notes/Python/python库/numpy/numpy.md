https://realpython.com/numpy-tutorial/#getting-into-shape-array-shapes-and-axes
https://www.numpy.org.cn/user/basics/types.html
np.dtype:https://numpy.org/doc/stable/reference/arrays.dtypes.html
np.recarray:https://numpy.org/doc/stable/reference/generated/numpy.recarray.html
np.ndarray:https://numpy.org/doc/stable/reference/arrays.classes.html
使用pandas与numpy进行数据清理：https://realpython.com/python-data-cleaning-numpy-pandas/

一、安装numpy

二、Hello Numpy小例子
1、核心概念：
（1）使用创建数组numpy.array()
（2）将完整数组视为单个值，使矢量化计算更具可读性
（3）使用内置 NumPy 函数修改和聚合数据

2、
```python
import numpy as np

curve_center = 80
grades = np.array(72, 35, 64, 88, 51, 90, 74, 12)

def curve(grades):
    average = grades.mean()
    change = curve_center - average
    new_grades = grades + change
    return np.clip(new_grades, grades, 100)

curve(grades)
```


使用别名导入`numpy：import numpy as np`

创建一个一维的numpy数组：`grades = np.array( )`

数组取平均值：`average = grades.mean()`

重要概念：
（1）矢量化(vectorization):以相同方式对数组中的每个元素执行相同的操作，可替代for循环
（2）广播(broadcasting):扩展两个不同形状的数组并确定如何在他们之间执行矢量化操作的过程。new_grades = grades + change中，grades是一个形状为(8, )的数组即是一个矢量，change是一个标量单个数字本质上具有形状(1, )。Numpy将标量添加到数组中的每个项目中，并且返回一个包含新结果的数组。

numpy.clip ( a， min， max， out = None， ** kwargs )：给定一个区间，区间外的值将被截断到区间边缘，如指定区间2,5小于2的值变为2，大于5的值变为5。确保min<max。a为给定的数组，返回一个新数组，包含a的元素，其中小于min的值被替换为min，大于max的值被替换为max。当min>max时，clip返回一个所有值都等于max的数组。
https://numpy.org/doc/2.0/reference/generated/numpy.clip.html#numpy.clip
 return np.clip(new_grades, grades, 100)，又是一个广播示例。对于 的第二个参数clip()，您传递grades，确保每个新弯曲的成绩不会低于原始成绩。但对于第三个参数，您传递一个值：100。NumPy 会获取该值并将其广播到 中的每个元素new_grades，确保新弯曲的成绩都不会超过满分。

三、数组形状和轴
1、掌握形状
In 1: `import numpy as np`

In 2: `temperatures = np.array(`
   ...:     `29.3, 42.1, 18.8, 16.1, 38.0, 12.5,`
   ...:     `12.6, 49.9, 38.6, 31.3, 9.2, 22.2
   ...: ]`).reshape(2, 2, 3)`

In 3: `temperatures.shape
Out3: (2, 2, 3)

In 4: temperatures
Out4:`
`array([[29.3, 42.1, 18.8],
        `16.1, 38. , 12.5],

       [[12.6, 49.9, 38.6],
        [31.3,  9.2, 22.2]]])`

In 5: np.swapaxes(temperatures, 1, 2)
Out5:
array([[29.3, 16.1],
        42.1, 38. ,
        18.8, 12.5],

       [[12.6, 31.3],
        [49.9,  9.2],
        [38.6, 22.2]]])
使用.reshape()的方法形成一个223的数据块，想象成一个长方体array:( [1 ,2 ,3 ], [4 ,5 ,6 ] ,  [7 ,8 ,9 ], [9 ,10 ,11 ] )，三维空间。
np.swapaxes(temperatures, 1 , 2 )，相当于，交换x轴与y轴的位置与数据。详细见PAD笔记。

2、理解轴
axes:轴，axis:轴线

在Numpy数组中，轴从0开始索引，并标识哪个维度是哪个维度。例如二维数组中有一个垂直轴轴0和一个水平轴轴1。

此示例将展示.max()默认情况下不带axis参数的行为方式，以及它如何根据axis您在提供参数时指定的内容更改功能：
In 1: import numpy as np

In 2: table = np.array(
   ...:     5, 3, 7, 1,
   ...:     2, 6, 7 ,9,
   ...:     1, 1, 1, 1,
   ...:     4, 3, 2, 0,
   ...: ])

In 3: table.max()
Out3: 9

In 4: table.max(axis=0)
Out4: array(5, 6, 7, 9)

In 5: table.max(axis=1)
Out5: array(7, 9, 1, 4)
默认情况下，.max()无论有多少维，都会返回整个数组中的最大值。但是，一旦您指定了轴，它就会针对该特定轴上的每组值执行该计算。例如，使用 参数axis=0，.max()选择 中的四个垂直值集中的最大值table，并返回已展平或聚合为一维数组的数组。
事实上，NumPy 的许多函数都是这样的：如果没有指定轴，那么它们将对整个数据集执行操作。否则，它们将以轴方式执行操作。

3、广播(broadcasting)
 it functions around one rule: arrays can be broadcast against each other if their dimensions match or if one of the arrays has a size of 1.
即如果数组的尺寸匹配，或者其中一个数组的尺寸为1（前面的例子），则这两个数组可以相互广播。
如果数组在某个轴上大小匹配，则将对元素逐个操作，如果其中一个数组在某个轴上尺寸为1，则该值将沿该轴广播，或根据需要重复多次以匹配另一个数组中沿该轴的元素数量。

例子：
In 1: import numpy as np

In 2: A = np.arange(32).reshape(4, 1, 8)

In 3: A
Out3:
array([[ 0,  1,  2,  3,  4,  5,  6,  7]],

       [[ 8,  9, 10, 11, 12, 13, 14, 15]],

       16, 17, 18, 19, 20, 21, 22, 23]],

       [[24, 25, 26, 27, 28, 29, 30, 31]]])

In 4]: B = np.arange(48).reshape(1, 6, 8)

In 5: B
Out5:
array([[ 0,  1,  2,  3,  4,  5,  6,  7],
         8,  9, 10, 11, 12, 13, 14, 15,
        16, 17, 18, 19, 20, 21, 22, 23,
        24, 25, 26, 27, 28, 29, 30, 31,
        32, 33, 34, 35, 36, 37, 38, 39,
        40, 41, 42, 43, 44, 45, 46, 47]])
A有4个平面，每个平面有1行8列，B有1个平面，每个平面有6行8列。
将两个数组相加：
In 7: A + B
Out7:
```python
array([[ 0,  2,  4,  6,  8, 10, 12, 14],
         8, 10, 12, 14, 16, 18, 20, 22,
        16, 18, 20, 22, 24, 26, 28, 30,
        24, 26, 28, 30, 32, 34, 36, 38,
        32, 34, 36, 38, 40, 42, 44, 46,
        40, 42, 44, 46, 48, 50, 52, 54],

       [[ 8, 10, 12, 14, 16, 18, 20, 22],
        [16, 18, 20, 22, 24, 26, 28, 30],
        [24, 26, 28, 30, 32, 34, 36, 38],
        [32, 34, 36, 38, 40, 42, 44, 46],
        [40, 42, 44, 46, 48, 50, 52, 54],
        [48, 50, 52, 54, 56, 58, 60, 62]],

       [[16, 18, 20, 22, 24, 26, 28, 30],
        [24, 26, 28, 30, 32, 34, 36, 38],
        [32, 34, 36, 38, 40, 42, 44, 46],
        [40, 42, 44, 46, 48, 50, 52, 54],
        [48, 50, 52, 54, 56, 58, 60, 62],
        [56, 58, 60, 62, 64, 66, 68, 70]],

       [[24, 26, 28, 30, 32, 34, 36, 38],
        [32, 34, 36, 38, 40, 42, 44, 46],
        [40, 42, 44, 46, 48, 50, 52, 54],
        [48, 50, 52, 54, 56, 58, 60, 62],
        [56, 58, 60, 62, 64, 66, 68, 70],
        [64, 66, 68, 70, 72, 74, 76, 78]])
A:(4, 1, 8), B:(1, 6, 8)
```
所以平面B复制3次与A匹配，再将A中的行数复制5次与B匹配，A变成（4，6，8），B也变成（4， 6，8），再相加。

注意，arange()这是一个使用!从某个范围创建数组的好方法。
range(start, stop, step)，返回一个数字序列。

四、数据科学操作：Filter（过滤）, Order（排序）, Aggregate（聚合）
1、索引
索引使用了许多与普通 Python 代码相同的惯用语。您可以使用正索引或负索引从数组的前面或后面进行索引。您可以使用冒号 ( :) 来指定“其余”或“全部”，甚至可以像使用常规 Python 列表一样使用两个冒号来跳过元素。
区别在于：NumPy 数组在轴之间使用逗号，因此您可以在一组方括号中索引多个轴。


In 1: import numpy as np

In 2: square = np.array(
   ...:     16, 3, 2, 13,
   ...:     5, 10, 11, 8,
   ...:     9, 6, 7, 12,
   ...:     4, 15, 14, 1
   ...: ])

In 3: for i in range(4):
   ...:     assert square:, i.sum() == 34
   ...:     assert squarei, :.sum() == 34
   ...:

In 4: assert square:2, :2.sum() == 34

In 5: assert square2:, :2.sum() == 34

In 6: assert square:2, 2:.sum() == 34

In 7: assert square2:, 2:.sum() == 34
(assert 关键字，能在表达式条件为false的时候返回错误，不必等待程序崩溃)

2、屏蔽和过滤（masking and filtering）
基于索引的选择很棒，但是如果您想根据更复杂的非均匀或非连续标准过滤数据，该怎么办？这就是掩码概念发挥作用的地方。
掩码是一个与数据形状完全相同的数组，但它保存的是布尔值，而不是值：要么True要么False。您可以使用此掩码数组以非线性和复杂的方式索引数据数组。它将返回布尔数组具有True值的所有元素。
例：
In 1: import numpy as np

In 2: numbers = np.linspace(5, 50, 24, dtype=int).reshape(4, -1)

In 3: numbers
Out3:
array([ 5, 6,  8, 10, 12, 14],
       16, 18, 20, 22, 24, 26,
       28, 30, 32, 34, 36, 38,
       40, 42, 44, 46, 48, 50])

In 4: mask = numbers % 4 == 0

In 5: mask
Out5:
array([False, False,  True, False,  True, False],
        True, False,  True, False,  True, False,
        True, False,  True, False,  True, False,
        True, False,  True, False,  True, False])

In 6: numbersmask
Out6: array( 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48)

In 7: by_four = numbersnumbers % 4 == 0

In 8: by_four
Out8: array( 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48)

其中numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None, axis=0, , device=None)，与arrange()类似，但是使用样本数而不是步长，这对于科学绘图中的均匀分布采样很有用。

array.reshape()可以将其-1作为其维度大小之一。这意味着 NumPy 应该根据其他轴的大小来确定该特定轴需要多大。在本例中，轴 0 中的24值和大小为4，轴 1 最终的大小为6

3、转置（transposing）、排序（sorting）和连接（concatenating）
转置数组
a = np.array(
    1, 2,
    3, 4,
    5, 6,
])
b = a.T
c = a.transpose() 这两句都是行列转置

排序
data = np.array(
    7, 1, 4,
    8, 6, 5,
    1, 2, 3
])
b = np.sort(data) # 省略axis参数会自动选择最内层的维度，即本例中的行进行排序
print(f'b = {b}')
c = np.sort(data, axis=None)# 全局排序
print(f'c = {c}')
d = np.sort(data, axis=0)# 对0轴即列轴排序
print(f'd = {d}')

连接
a = np.array(
    4, 8,
    6, 1
])
b = np.array(
    3, 5,
    7, 2
])
c = np.hstack((a, b))# 连接行，轴1
print(c)
d = np.vstack((b, a))# 连接列，轴0
e = np.concatenate((a, b))# 更通用的连接，可指定轴，默认为0轴，即纵向列轴
f = np.concatenate((a, b), axis=None)# 展开

聚合
包括.sum()、.max()、.mean()、.std()

五、实例1实现麦克劳林级数

六、优化存储：数据类型

1、数值类型：int, bool, float, complex

姓名	          位数	Python 类型	NumPy 类型
整数	             64	      int	         np.int-
布尔值	       8	     bool	        np.bool-_
漂浮	             64	      float	        np.float-
复杂的	   128	    complex	np.complex-_
(用-表示下划线)

数值类型
a = np.array(1, 3, 5.5, 7.7, 9.2, dtype=np.single)#平台定义的单精度浮点数：通常为符号位，8位指数，23位尾数
b = np.array(1, 3, 5.5, 7.7, 9.2, dtype=np.uint8)#整数，范围从0-255

2、字符串类型：unicode大小
字符串类型
names = np.array('bob', 'amy', 'han', dtype=str)# three 4-byte Unicode characters
names2 = 'jamima'#将会阶段数值，使其变为U3的大小
print(names, names.itemsize)

3、结构化数组

结构化数组
data = np.array(
    ("joe", 32, 6),
    ("mary", 15, 20),
    ("felipe", 80, 100),
    ("beyonce", 38, 9001)
], dtype=("name", str, 10), ("age", int), ("power", int))#对于dtype提供的是一个元组列表，name是10字符的Unicode字段
a = data0
b = data"name"
c = datadata["power"] > 9000"name"#基于字段的掩码过滤和基于字段的选择的超强大组合
d = np.sort(datadata["age"] > 20, order="power")"name"#掩码，还有基于order by 的排序
print(d)

七、下一步学习
1、pandas
pandas是一个采用结构化数组概念的库，它使用大量便捷方法、开发人员体验改进和更好的自动化来构建它。如果您需要从任何地方导入数据、清理数据、重塑数据、完善数据，然后将其导出为任何格式，那么 pandas 就是您的最佳选择。在某个时候，您很可能会import pandas as pd同时import numpy as np……
快速上手pandas:https://pandas.pydata.org/pandas-docs/stable/user_guide/10min.html

2、scikit-learn（科学学习）

scikit-learn:https://scikit-learn.org/stable/
数据科学：https://realpython.com/learning-paths/math-data-science/
机器学习：https://realpython.com/learning-paths/machine-learning-python/

3、matplotlib
https://matplotlib.org/
https://realpython.com/python-matplotlib-guide/

八、实例二：使用matplotlib处理图像
```python
import numpy as np
import matplotlib.image as mpimg

img = mpimg.imread("kitty.jpg")
print(type(img))
print(img.shape)

output = img.copy()  # The original image is read-only!
output:, :, :2 = 0
mpimg.imsave("blue.jpg", output)
```



