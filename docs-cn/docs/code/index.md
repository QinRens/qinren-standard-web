# 基本代码管理规范

## Python

### 环境管理

Python环境管理有几种方式：

1. [Anaconda](https://www.anaconda.com)
2. [virtualenv](https://virtualenv.pypa.io/en/latest/)
3. 直接在user安装全部依赖包

下面以virtualenv为例说明：

1.安装virtualenv
```bash
$ pip install virtualenv
```
2.生成环境
```bash
$ virtualenv venv
```
3.激活环境
```bash
$ source venv/bin/activate
```
4.关闭环境
```bash
(venv)$ deactive
```
5.生成该环境下的requirements.txt文件
```bash
(venv)$ pip freeze -l > requirements.txt
```
6.从requirements.txt中安装所有文件到```venv```
```bash
(venv)$ pip install -r requirements.txt
```

### 代码注释规范

所有代码注释 __全部使用英文__ 。

#### 代码文件头注释

模板如下：

```python
'''
# ------>Basic information of the author
Author: Yadong Zhang

Date: 11-08-2018

Email: ydup@foxmail.com

# ------>What does this script implement?

# ------>Brief introduction of your idea and the reference.

# ------>The steps/work flow for the implementation and the warning points.
# For example:
Steps:
1. Data preparation
    + Data transformation into spectrum of 0 to 1
    + 
2. Feature engineering

3. Machine learning model initialization
    + Hyperparameters initialization
    + 
4. ...
5. Result visualization
6. Statistic Analysis

# ------> If it is needed, a table of terms should be here:
Terms Declaration:
| ----------Term Name----------- | ---------------Meaning-----------------|
            Term - 1                           Meaning - 1

# ------> List the bugs you have fixed and you gonna fixed
Fixed:

TODO:

```

#### 函数注释

模板如下：

```python
def template(inputParam_1, inputParam_2):
    '''
    Function description
    :param inputParam_1: description of input parameter - 1; type: 
    :param inputParam_2: description of input parameter - 2; type:
    return: outputParam, description of outputParam

    Example:
    >>> template(inputParam_1, inputParam_2)
    >>> outputParam

    Note: 

    '''
    # body

    return outputParam

```

### Python 模块规范


1. 包的引用
	+ 不同的包引用最好分行写:

	        Yes:  import os
	              import sys
	        No:   import os, sys

	+ 如果是从同一个包中引用多个方法，可以写成一行：
        
        	Yes:  from subprocess import Popen, PIPE

	+ 其他：

			Yes: import package as package_name
			No: from package import *
	
	       	Yes: import mypkg.sibling
	             from mypkg import sibling
	             from mypkg.sibling import example
        	No: from . import sibling
             	from .sibling import example




2. 包的引用按照以下类别排序：

    1. 标准库
    
    2. 第三方库
    
    3. 本地库（例如工程中library下的库函数）
    
            import sys
            import os
        
            import matplotlib
            from matplotlib import pyplot as plt
    
            import DCW
            from DCW import EDA
        

 
## Matlab

参考：http://www.datatool.com/downloads/matlab_style_guidelines.pdf

### 变量名和函数名命名原则

1. 以小写字母开头的英文单词命名，若变量由多个单词组成，使用大写分割，如：qualityOfLife
2. 减少变量名中下划线的使用，避免在某些情况下matlab识别为下标
3. 表示数量时，以n开头命名变量，如：nFiles
4. 第3条的特例，由于matlab中矩阵一般为m*n，所以可用mRows代表行数
5. 考虑到matlab中有时使用i，j作为复数的表示，因此循环变量可以选择如iFiles等方式命名
6. 常量全部大写，多个单词间使用下划线分开，如：COLOR_RED
7. 使用新的变量名前检查工作区中别的m文件是否已经使用过该变量名，避免程序出现bug
8. 只有一个返回值的函数的用它的返回值含义命名，如：mean()
9. 没有返回值的函数用它具体做的事情命名，如：plot()
10. 返回值是布尔值的函数用is作为前缀

### 代码整体书写规范

1. 缩进规范
2. 代码模块化，将一些经常使用的代码部分封装成函数
3. 如果一个函数只被一个m文件里的函数调用，不必封装成单独的m文件
4. input和output与计算部分的模块分开，output部分需要简洁易懂
5. 想要实现某一功能时，先查阅官方文档，寻找有没有现成的函数可以调用。以此减少重复劳动，提高代码效率

### 注释规范

1. m文件开头注明程序或函数实现的功能
2. m文件开头注明一些可能的报错和解决方法
2. 如果变量是数组，注明数组各维度含义
3. simulink的参数文件写清各参数的含义
4. 如果参数的值可以调整，注明建议调整的范围

### Simulink建模规范

1. 将模型中需要的所有参数写在一个m文件中，方便修改
2. 连线整齐，模块布局合理
3. 建模模块化，将实现一些特定功能的部件封装成子模块
4. 保留一些建模中间变量的观察窗口，方便运行时观察结果是否正确

