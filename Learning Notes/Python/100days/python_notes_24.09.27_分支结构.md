一、分支结构
1、关键词：if、elif、else。
例：
`username = input('请输入用户名：')`
`password = input('请输入口令：')`
`用户名是admin，密码是123456`
`if username != 'admin' and password != '123456':`
    `print('用户名和密码错误')`
`elif username == 'admin' and password !='123456':`
        `print('密码错误')`
`elif username != 'admin' and password '123456':`
        `print('用户名错误')`
`else:`
    `print('验证成功')`

Python中使用缩进的方式来表示代码的层次结构，如果if条件成立的情况下需要执行多条语句，只需要保持多条语句具有相同的缩进就可以了。即如果连续的代码有相同的缩进那么他们属于同一个代码块，相当于是一个执行的整体。缩进可以使用任意数量的空格，但通常使用4个空格。

`x = float(input('x = '))`
`if x > 1:`
    `y = 3 * x - 5`
`elif x < -1:`
    `y = 5 * x + 3`
`else:`
    `y = x + 2`
`print('f(%.2f) = %.2f' % (x, y))`

当然，分支结构是可以嵌套的，例如：

`x = float(input('x = '))`
`if x > 1:`
    `y = 3 * x - 5`
`else:`
    `if x >= -1:`
        `y = x + 2`
    `else:`
        `y = 5 * x + 3`
`print('f(%.2f) = %.2f' % (x, y))`

自然前者更好
