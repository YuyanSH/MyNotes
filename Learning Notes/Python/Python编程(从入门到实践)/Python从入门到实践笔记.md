
## 第二章 变量和数据结构
### 2.3 字符串
1. 修改字符串大小写
```python
name = 'furina'
name.title() # 以首字母大写的方式显示每一个单词
name.upper() # 全大写
name.lower() # 全小写
```
2. f字符串
```python
first_name = "Furina"
mid_name = "De"
last_name = "Fontaine"
name = f"{first_name}{mid_name}{last_name}"
print(name)
```
3. 空白
```python
# \t添加制表符
# \n添加换行符
```
```python
favorite_language = ' python '
favorite_language.strip() # 删除所有空白
favorite_language.rstrip() # 删除右边空白
favorite_language.lstrip() # 删除左边空白
```
4. 前后缀
```python
nostarch_url = 'http://nostarch.com'
nostarch_url.removeprefix('http://') # 删除前缀
file_name = 'python_notes.txt'
file_name.removesuffix('.txt') # 删除后缀
```
## 第三章 列表简介
### 3.2 修改添加删除元素
#### 3.2.2 在列表中添加元素
1. 在列表末尾添加元素
```python
names = ['renzheng', 'jack', 'andrew', 'hao']
for name in names:
    print(f"hello, {name}")
names.append('furina')
print(names)
```
2. 在列表中插入元素
```python
names.insert(1, ''asuka)
```
#### 3.2.3 从列表中删除元素
1. 使用del
```python
names = ['renzheng', 'jack', 'andrew', 'hao']
del names[0]
```
2. 使用pop
pop表示弹出列表末尾的元素并且能够使用它
```python
pop_name = names.pop()
print(names)
print(pop_name)
first_name = names.pop(0) # 弹出任意一个元素
```
3. 使用remove根据元素值删除元素
```python
names = ['renzheng', 'jack', 'andrew', 'hao']
names.remove('hao')
print(names)
```

### 3.3 管理列表
1. 对列表进行排序
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.sort()
print(cars)
cars.sort(reverse=True)
print(cars)
```
2. 临时排序
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
print(sorted(cars, reverse=True))
print(cars)
```
3. 反向打印列表
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
cars.reverse()
print(cars)
```
4. 确定列表长度
```python
cars = ['bmw', 'audi', 'toyota', 'subaru']
length = len(cars)
print(length)
```

## 第四章 操作列表
### 4.3 创建数值列表
#### 4.3.3 简单统计
```python
squares = []
for value in range(1, 11):
    squares.append(value**2)
print(squares)
print(min(squares))
print(max(squares))
print(sum(squares))
```
#### 4.3.4 列表推导式
```python
squares = [value**2 for value in range(1, 11)]
print(squares)
```
### 4.4 使用列表的一部分
#### 4.4.1 切片
```python
tiwate = ['mengde', 'liyue', 'daoqi', 'fengdan', 'xumi', 'nata', 'zhidong']
print(tiwate[1:5])
print(tiwate[:4])
print(tiwate[4:])
print(tiwate[-1:])
print(tiwate[2:-3])
```
### 4.5 元组
- 元组(tuple): 不可变的列表
```python
dimensions = (200, 50)
print(dimensions)
# dimensions[0] = 250 会报错，因为元组不可修改
```

## 第五章 if语句
### 5.2 条件
#### 5.2.5 检查多个条件
- and
```python
age_0 = 22
age_1 = 18
print(age_0 >=21 and age_1 >= 21)
```
- or
```python
age_0 = 22
age_1 = 18
print(age_0 >=21 or age_1 >= 21)
```

#### 5.2.6 检查列表中特定值存不存在
```python
tiwate = ['mengde', 'liyue', 'daoqi', 'xumi', 'fengdan', 'nata', 'zhidong']
print('mengde' in tiwate)
print('jinjihai' in tiwate)
```
```python
banned_users = ['andrew', 'carolina', 'david']
user = 'marie'
  
if user not in banned_users:
    print(f"{user.title()}, you can post a response if you wish")
```

### 5.3 if 语句
#### 5.3.2 if-else 语句
```python
age = 17
if age >= 18:
    print("Y")
else:
    print("N")
```
#### 5.3.3 if-elif-else
```python
age = 12
if age < 4:
    price = 0
elif age < 18:
    price = 25
elif age < 65:
    price = 40
else:
    price = 20

print(f"Your admission cost is ${price}")
```
##### 练习
```python
alien_color_1 = 'green'
alien_color_2 = 'yellow'
alien_color_3 = 'red'

alien_color = alien_color_3
if alien_color == 'green':
    print("+ 5")
elif alien_color == 'yellow':
    print("+ 10")
elif alien_color == 'red':
    print("+ 15")
```
### 5.4 使用if处理列表
#### 5.4.2 确定列表非空
```python
requested_toppings_1 = ['mushrooms', 'green peppers', 'extra cheese']
requested_toppings_2 = []

requested_toppings = requested_toppings_2
if requested_toppings:
    for requested_topping in requested_toppings:
        print(f"Adding {requested_topping}")
    print("\nFinished making your pizza")
else:
    print("Are you sure you want a plain pizza?")
```
- 在if语句中将列表名用作条件表达式时，Python在列表至少包含一个元素时返回True，在列表为空时返回False。
- 对于数值0，空值None，单引号空字符串''，双引号空字符串""，空列表[]，空字典{}，Python都会返回False。

## 第六章 字典
### 6.2 使用字典
### 6.2.2 添加键值对
```python
alien_0 = {'color': 'green', 'points': 5}
print(alien_0)
alien_0['x_position'] = 0
alien_0['y_position'] = 25
print(alien_0)
```
### 6.2.5 删除键值对
```python
alien_0 = {'color': 'green', 'points': 5}
del alien_0['color']
print(alien_0)
```
### 6.2.7 使用get()来访问值
```python
alien_0 = {'color': 'green', 'points': 5}
point_value = alien_0.get('points', 'No point value assigned')
print(point_value)
```
### 6.3 遍历字典
#### 6.3.1 遍历所有键值对
```python
points = {'A': 1, 'B': 2, 'C': 3, 'D': 4}
for key, value in points.items():
    print(f"key:{key},value:{value}")
```
- items()方法返回一个键值对列表
#### 6.3.2 遍历键
```python
points = {'A': 1, 'B': 2, 'C': 3, 'D': 4}
for key in points.keys():
    print(key)
# 在遍历字典时，会默认遍历所有键
points = {'A': 1, 'B': 2, 'C': 3, 'D': 4}
for key in points:
    print(key)
# 两段代码作用相同
```
- keys()方法返回一个包含键的列表
#### 6.3.4 遍历字典中的所有值
```python
points = {'A': 1, 'B': 2, 'C': 3, 'D': 3}
for point in points.values():
    print(point)
# 使用set()剔除重复项
for point in set(points.values()):
    print(point)
```
- 为了剔除重复项，可以使用**集合**(set)。集合中的每个元素都是独一无二的，可以使用一对花括号直接创建集合
```python
languages = {'python', 'rust', 'python', 'C'}
```

## 第七章 用户输入和while循环
### 7.1 input()函数
- input()接受一个参数，即要向用户显示的提示(prompt)。
#### 7.1.2 获取数值输入
- input()函数，python会将用户的输入解读为字符串，可以用int()将输入的字符串转换为数值。
```python
age = input("How old are you? ")
age = int(age)
print(age >= 18)
```

#### 7.1.3 求模运算
- **求模运算符**(%)将两个数相除并返回余数
```python
print(4 % 3)
```
### 7.2 while循环
#### 7.2.4 使用break
```python
prompt = "\nEnter 'quit' to end the program"
active = True
while active:
    message = input(prompt)

    if message == 'quit':
        active = False
        break
    else:
        print(message)
print("结束嘞")
```
#### 7.2.5 使用continue
```python
current_number = 0
while current_number < 10:
    current_number += 1
    if current_number % 2 == 0:
        continue
    print(current_number)
```
#### 7.2.6 避免无限循环
- 要结束无限循环，可在输出区域中单击鼠标，再按Ctrl + C
### 7.3 使用while循环处理列表和字典
#### 7.3.1 在列表之间移动元素
```python
unconfirmed_users = ['alice', 'brain', 'candace']
confirmed_users = []

while unconfirmed_users:
    current_user = unconfirmed_users.pop()
    print(f"Verifying user : {current_user.title()}")
print("\nThe following users have been confirmed")
for user in confirmed_users:
    print(user.title())
```


## 第八章 函数
### 8.2 传递实参
#### 8.2.1 位置实参
- 在调用函数时，Python将函数调用中的每一个实参关联到函数定义中的一个形参，最简单的方式是基于实参的顺序进行关联。
```python
def describe_pet(animal_type, pet_name):
    """显示宠物信息"""
    print(f"\nI have a {animal_type}")
    print(f"My {animal_type}'s name is {pet_name.title()}")

describe_pet('dog', 'xiaomeng')
describe_pet('hamster', 'harry')
```
#### 8.2.2 关键字实参
```python
def describe_pet(animal_type, pet_name):
    """显示宠物信息"""
    print(f"\nI have a {animal_type}")
    print(f"My {animal_type}'s name is {pet_name.title()}")

describe_pet(animal_type='dog', pet_name='xiaomeng')
describe_pet(pet_name='harry', animal_type='hamster')
```
#### 8.2.3 默认值
```python
def describe_pet(pet_name, animal_type='dog'):
    """显示宠物信息"""
    print(f"\nI have a {animal_type}")
    print(f"My {animal_type}'s name is {pet_name.title()}")

describe_pet('xiaomeng')
describe_pet('harry', animal_type='hamster')
```
- 当使用默认值定义函数时，必须先列出无默认值的形参，再列出有默认值的形参，例如不能
```python
def describe_pet(animal_type='dog', pet_name):
```
### 8.3 返回值
#### 8.3.1 返回简单的值
```python
def get_formatted_name(first_name, last_name):
    """返回标准格式的姓名"""
    full_name = f"{first_name} {last_name}"
    return full_name.title()

musician = get_formatted_name('jimi', 'hendrix')
print(musician)
```
#### 8.3.2 让实参变成可选的
- 使用默认值可以让实参变成可选的
```python
def get_formatted_name(first_name, last_name, middle_name=''):
    """返回标准格式的姓名"""
    if middle_name:
        full_name = f"{first_name}, {middle_name}, {last_name}"
    else:
        full_name = f"{first_name}, {last_name}"
    return full_name.title()

musician = get_formatted_name('john', 'hooker')
print(musician)
```
#### 8.3.3 返回字典
```python
def build_person(first_name, last_name, age=None):
    """返回一个字典，其中包含一个人的信息"""
    person = {'first': first_name, 'last': last_name}
    if age:
        person['age'] = age
    return person
musician = build_person('jimi', 'hendrix')
print(musician)
```
#### 8.3.4结合函数与while循环
```python
def get_formatted_name(first_name, last_name, middle_name=''):
    """返回标准格式的姓名"""
    full_name = f"{first_name} {last_name}"
    return full_name.title()

while True:
    print("\nTell me your name")
    print("(enter 'q' at any time to quit)")

    f_name = input("First name: ")
    if f_name == 'q':
        break

    l_name = input("Last name: ")
    if l_name == 'q':
        break

    formatted_name = get_formatted_name(f_name, l_name)
    print(f"\nHello, {formatted_name}")
```
### 8.4 传递列表
### 8.5 传递任意数量的实参
```python
def make_pizza(*toppings):
    print(toppings)
make_pizza('pepperoni')
make_pizza('mushroon', 'green peppers', 'extra cheese')
```
- 形参名`*toppings`中的星号让Python创建一个名为toppings的元组。
#### 8.5.1 结合位置实参和任意数量的实参
```python
def make_pizza(size, *toppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings")
    for topping in toppings:
        print(topping)
make_pizza(16, 'pepperoni')
make_pizza(12, 'mushroon', 'green peppers', 'extra cheese')
```
- 经常会看到通用形参名`*args`, 收集任意数量的位置实参。
#### 8.5.2 使用任意数量的关键字实参
```python
def build_profile(first, last, **user_info):
    user_info['first_name'] = first
    user_info['last_name'] = last
    return user_info
user_profile = build_profile('albert', 'einstein',
                            location='princeton',
                              field='physics')
print(user_profile)
```
- `build_profile()`函数的定义要求提供名和姓，同时允许提供任意数量的名值对。形参`**user_info`中的两个星号让Python创建一个名为user_info的字典，该字典包含函数收到的其他所有名值对。
- 经常会看到形参名`**kwargs`，用于收集任意数量的关键字实参。
### 8.6 将函数存储在模块中
`pizza.py`
```python
def make_pizza(size, *toppings):
    """概述要制作的披萨"""
    print(f"\nMaking a {size}-inch pizza with the following toppings")
    for topping in toppings:
        print(f"- {topping}")
```
#### 8.6.1 导入整个模块
```python
import pizza
import os

print(os.getcwd())

pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushroon', 'green peppers', 'extra cheese')
```
#### 8.6.2 导入特定函数
- 还可以只导入模块中的特定函数，语法如下：
```python
from module_name import function_name
```
- 导入任意数量的函数：
```python
from module_name import function_0, function_1, function_2
```
```python
from pizza import make_pizza

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushroon', 'green peppers', 'extra cheese')
```
#### 8.6.3 使用as给函数指定别名
```python
from pizza import make_pizza as mp

mp(16, 'pepperoni')
mp(12, 'mushroon', 'green peppers', 'extra cheese')
```
#### 8.6.4 使用as给模块指定别名
```python
import pizza as p

p.make_pizza(16, 'pepperoni')
p.make_pizza(12, 'mushroon', 'green peppers', 'extra cheese')
```
#### 8.6.5 导入模块中的所有函数
```python
from pizza import *

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushroon', 'green peppers', 'extra cheese')
```
### 8.7 函数编写指南

