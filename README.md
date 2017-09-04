# Style Guide for Python Code

## 1.缩进

###1)使用 space（空格）来表示缩进，而不要用 tab（制表符）。

###2)和语法相关的每一层缩进都用 4 个空格来表示。

   每行的字符数不应超过 79。

###3)要么垂直对齐换行的元素或者使用4空格的悬挂式缩进(这时第一行不应该有参数)**

```python
# 与起始定界符对齐（垂直对齐换行）
# Aligned with opening delimiter
foo = long_function_name(var_one, var_two,
                        var_three, var_four)
# 悬挂时，应该增加一级缩进
# 4-space hanging indent; nothing on first line
foo = long_function_name(
   var_one, var_two, var_three,
   var_four)
```

###4)对于占据多行的长表达式来说，除了首行之外的其余各行都应该在通常的缩进级别之上再加 4 个空格。

```python
# 使用更多的缩进，以区别于其他代码
def long_function_name(
        var_one, var_two, var_three,
        var_four):
    print(var_one)
```


## 2.换行
   二元运算符首选的换行位置在操作符后面，但是为了可读性，可以考虑在操作符前面。
   注意，**换行时，若有括号，则直接换，若无使用\\说明。**

```python
# 坏的: 操作符远离它们的操作数
income = (gross_wages +
          taxable_interest +
          (dividends - qualified_dividends) -
          ira_deduction -
          student_loan_interest)

# 好的: 易于匹配操作数和操作符
income = (gross_wages
          + taxable_interest
          + (dividends - qualified_dividends)
          - ira_deduction
          - student_loan_interest)

#二元运算符首选的换行位置在操作符后面
class Rectangle(Blob):
    def __init__(self, width, height,
                 color='black', emphasis=None, highlight=0):
        if width == 0 and height == 0 and \
                color == 'red' and emphasis == 'strong' or \
                highlight > 100):
            raise ValueError("sorry, you lose")
        if width == 0 and height == 0 and (color == 'red' or
                                           emphasis is None):
            raise ValueError("I don't think so -- values are %s, %s" %
                               (width, height))
        Blob.__init__(self, width, height,
                      color, emphasis, highlight)
```


## 3.空行
   **顶级定义之间空两行，方法定义之间空一行**。
   顶级定义之间空两行，比如函数或者类定义。方法定义，类定义与第一个方法之间，都应该空一行。 函数或方法中，某些地方要是你觉得合适，就空一行。


## 4.空格   
###1)括号内不要有空格。
```
Yes: spam(ham[1], {eggs: 2}, [])

No:  spam( ham[ 1 ], { eggs: 2 }, [ ] )
```

###2)不要在逗号，分号，冒号前面加空格，但应该在它们后面加(除了在行尾)。

```
Yes: if x == 4:
         print x, y
     x, y = y, x

No:  if x == 4 :
         print x , y
     x , y = y , x
```

###3)参数列表，索引或切片的左括号前不应加空格。

```
Yes: spam(1)
no: spam (1)
```

###4)在二元操作符两边都加上一个空格，比如赋值(=)，比较(==, <, >, !=, <>, <=, >=, in, not in, is, is not), 布尔(and, or, not)。至于算术操作符两边的空格该如何使用，需要你自己好好判断。不过两侧务必要保持一致。

```
Yes: x == 1
No:  x<1
```

###5)当’=’用于指示关键字参数或默认参数值时，不要在其两侧使用空格。

```
Yes: def complex(real, imag=0.0): return magic(r=real, i=imag)
No:  def complex(real, imag = 0.0): return magic(r = real, i = imag)
```

###6)不要用空格来垂直对齐多行间的标记，因为这会成为维护的负担(适用于:, #, =等)：

```
Yes:
     foo = 1000  # comment
     long_name = 2  # comment that should not be aligned

     dictionary = {
         "foo": 1,
         "long_name": 2,
         }

No:
     foo       = 1000  # comment
     long_name = 2     # comment that should not be aligned

     dictionary = {
         "foo"      : 1,
         "long_name": 2,
         }
```

## 5.导入
   Import通常被放置在文件的顶部，仅在模块注释和文档字符串之后，在模块的全局变量和常量之前。
   **引入模块的时候，总是应该使用绝对名称，而不应该根据当前模块的路径来使用相对名称。例如，引入 bar 包中的 foo 模块时，应该完整地写出 from bar import foo，而不应该简写为 import foo。**
   **Imports 应该有顺序地成组安放，你应该在每组导入之间放置一个空行**。
   标准库的导入(Imports )
   相关的第三方导入(即所有的email包在随后导入)
   特定的本地应用/库导入(imports)


## 6.注释
   **单行用#+空格，批量用两组"""前后框住**
   如果注释很短，最好省略末尾的句号。注释块通常由一个或多个由完整句子构成的段落组成，每个句子都应该以句号结尾。
   行内注释：一个行内注释是和语句在同一行的注释。**行内注释应该至少用两个空格和语句分开。它们应该以'#'和单个空格开始。**

```python
"""
this is annotation block.
so we use this to express.
"""
x = x + 1  # for change the border
```


## 7.命名
###1)永远不要用字符'l'(小写字母el(就是读音,下同)),'O'(大写字母oh),或'I'(大写字母eye)作为单字符的变量名。在某些字体中,这些字符不能与数字1和0分开.当想要使用'l'时，用'L'代替它.
###2)常量通常在模块级别定义，并且**常量所有的字母都是大写，单词用下划线分开**。例如: MAX_OVERFLOW 和 TOTAL。
###3)**函数名、变量名及属性应该为小写，可以将单词用下划线分开以增加可读性**。
###4)**对类名使用大写字母开头的单词**(如CapWords, 即Pascal风格)。
  - 类中的实例方法（instance method），应该把首个参数命名为 self，以表示该对象自身。
  - 类方法（class method）的首个参数，应该命名为 cls，以表示该类自身。
  - 受保护的实例属性，应该以单个下划线开头，例如，\_leading_underscore。用单下划线(_)开头表示模块变量或函数是protected的(使用import * from时不会包含)。
  - 私有的实例属性，应该以两个下划线开头，例如，\__double_leading_underscore。用双下划线(__)开头的实例变量或方法表示类内私有。
###5)**模块名应该用小写加下划线的方式**(如lower_with_under.py)。尽管已经有很多现存的模块使用类似于CapWords.py这样的命名，但现在已经不鼓励这样做，因为如果模块名碰巧和类名一致，这会让人困扰。
###6)Python之父Guido推荐的规范


| Type                       | Public             | Internal                                 |
| -------------------------- | ------------------ | ---------------------------------------- |
| Modules                    | lower_with_under   | _lower_with_under                        |
| Packages                   | lower_with_under   |                                          |
| Classes                    | CapWords           | _CapWords                                |
| Exceptions                 | CapWords           |                                          |
| Functions                  | lower_with_under() | _lower_with_under()                      |
| Global/Class Constants     | CAPS_WITH_UNDER    | _CAPS_WITH_UNDER                         |
| Global/Class Variables     | lower_with_under   | _lower_with_under                        |
| Instance Variables         | lower_with_under   | _lower_with_under (protected) or __lower_with_under (private) |
| Method Names               | lower_with_under() | _lower_with_under() (protected) or __lower_with_under() (private) |
| Function/Method Parameters | lower_with_under   |                                          |
| Local Variables            | lower_with_under   |                                          |


## 8.python特性
   **即使是一个打算被用作脚本的文件，也应该是可导入的，并且简单的导入不应该导致这个脚本的主功能(main functionality)被执行，这是一种副作用。主功能应该放在一个main()函数中。**
   在Python中，pydoc以及单元测试要求模块必须是可导入的。你的代码应该在执行主程序前总是检查 if __name__ == '__main__'，这样当模块被导入时主程序就不会被执行。

```python
def main():
      ...

if __name__ == '__main__':
    main()
```


# Reference
https://www.python.org/dev/peps/pep-0008/ 官网文档
http://www.jianshu.com/p/28f191f97e6f 对官网的翻译，以此为主
http://www.codebelief.com/article/2017/02/pep-8-style-guid-for-python-code-summary/ 简单的总结
http://zh-google-styleguide.readthedocs.io/en/latest/google-python-styleguide/python_style_rules/ 很好的分类总结
