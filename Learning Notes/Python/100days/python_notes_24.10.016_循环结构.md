循环结构

1、for in循环

自己定义的一个写文档的函数
`def save_txt(lst):`
    `with Path('bad_file_names.txt').open('w') as bf:`
        `for bfn in lst:`
            `print(bfn)`
            `bf.write(f"  {bfn}\n")`

`sum = 0`
`for x in range(101):`
    `sum += x`
`print(sum)`

ps: range 用法：
range(n):  产生0到(n-1)范围的整数，取不到n；
range(1, 101): 产生1到100范围的整数。其实就是前面闭区间，后面开区间；
range(a, b, c): 其中a是前面界限，b是后面界限，c是步长可为复数。


2、while循环

`sum_list =` 
        `while True:`
            `file_list = read_files(zip_file, t)`
            `print(f"t = {t}")`
            `print(set(file_list) - set(sum_list))`
            `input_result = input("Do you want to continue? (y/n)")`
            `if input_result == "n":`
                `save_txt(file_list)`
                `delete_files(zip_file, sum_list)`
                `break`
            `else:`
                `sum_list.extend(file_list)`
                `t -= 1`

通过bool值来控制循环，break是提前终止循环，需要注意，break只能终止它所在的那个循环，这一点在嵌套的循环结构中需要引起注意。continue可以放弃本次循环后续的代码直接让循环进入下一轮。