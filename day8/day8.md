## day8

> 一、错误与异常

* 错误：语法错误，多记多练

```python
print("python)
# 输出结果：
"""
报错：语法错误，引号需要成双出现
"""
```

* 异常：没有语法错误，程序运行期间出错

```python
def func(a,b):
    print(a/b)
func(10,0)
# 输出结果：
"""
报错：被除数不能为0
"""
```

* 异常类继承关系

```
BaseException       # 所有异常的基类 
+-- SystemExit         # 解释器请求退出 
+-- KeyboardInterrupt  # 用户中断执行(通常是输入^C) 
+-- GeneratorExit      # 生成器(generator)发生异常来通知退出 
+-- Exception          # 常规异常的基类      
	+-- StopIteration         # 迭代器没有更多的值      
	+-- StopAsyncIteration    # 必须通过异步迭代器对象的__anext__()方法引发以停止迭代      
	+-- ArithmeticError       # 各种算术错误引发的内置异常的基类      
	|    +-- FloatingPointError   # 浮点计算错误 	  
	|	 +-- OverflowError        # 数值运算结果太大无法表示      
	|    +-- ZeroDivisionError    # 除(或取模)零 (所有数据类型)      
	+-- AssertionError    # 当assert语句失败时引发      
	+-- AttributeError    # 属性引用或赋值失败      
	+-- BufferError       # 无法执行与缓冲区相关的操作时引发      
	+-- EOFError          # 当input()函数在没有读取任何数据的情况下达到文件结束条件(EOF)时引发      
	+-- ImportError       # 导入模块/对象失败      
	|    +-- ModuleNotFoundError  # 无法找到模块或在在sys.modules中找到None      
	+-- LookupError        # 映射或序列上使用的键或索引无效时引发的异常的基类      
	|    +-- IndexError    # 序列中没有此索引(index)      
	|    +-- KeyError      # 映射中没有这个键      
	+-- MemoryError        # 内存溢出错误(对于Python 解释器不是致命的)      
	+-- NameError          # 未声明/初始化对象 (没有属性)      
	|    +-- UnboundLocalError  # 访问未初始化的本地变量      
	+-- OSError  # 操作系统错误，EnvironmentError，IOError，WindowsError，socket.error，select.error和mmap.error已合并到OSError中，构造函数可能返回子类      
	|    +-- BlockingIOError      # 操作将阻塞对象(e.g. socket)设置为非阻塞操作      
	|    +-- ChildProcessError    # 在子进程上的操作失败      
	|    +-- ConnectionError      # 与连接相关的异常的基类
	|    |    +-- BrokenPipeError  		  # 另一端关闭时尝试写入管道或试图在已关闭写入的套接字上写入      
	|    |    +-- ConnectionAbortedError  # 连接尝试被对等方中止      
	|    |    +-- ConnectionRefusedError  # 连接尝试被对等方拒绝      
	|    |    +-- ConnectionResetError    # 连接由对等方重置      
	|    +-- FileExistsError      # 创建已存在的文件或目录      
	|    +-- FileNotFoundError    # 请求不存在的文件或目录      
	|    +-- InterruptedError     # 系统调用被输入信号中断      
	|    +-- IsADirectoryError    # 在目录上请求文件操作(例如 os.remove())      
	|    +-- NotADirectoryError   # 在不是目录的事物上请求目录操作(例如 os.listdir())      
	|    +-- PermissionError      # 尝试在没有足够访问权限的情况下运行操作      
	|    +-- ProcessLookupError   # 给定进程不存在      
	|    +-- TimeoutError         # 系统函数在系统级别超时      
	+-- ReferenceError  	# weakref.proxy()函数创建的弱引用试图访问已经垃圾回收了的对象      
	+-- RuntimeError        # 在检测到不属于任何其他类别的错误时触发      
	|    +-- NotImplementedError  # 在用户定义的基类中，抽象方法要求派生类重写该方法或者正在开发的类指示仍然需要添加实际实现      
	|    +-- RecursionError   	  # 解释器检测到超出最大递归深度      
	+-- SyntaxError		   # Python 语法错误      
	|    +-- IndentationError  	  # 缩进错误      
	|         +-- TabError  	  # Tab和空格混用      
	+-- SystemError  	  # 解释器发现内部错误      
	+-- TypeError    	  # 操作或函数应用于不适当类型的对象      
	+-- ValueError   	  # 操作或函数接收到具有正确类型但值不合适的参数：如：int("99 years ago.")      
	|    +-- UnicodeError  		  # 发生与Unicode相关的编码或解码错误      
	|         +-- UnicodeDecodeError  	 # Unicode解码错误      
	|         +-- UnicodeEncodeError  	 # Unicode编码错误      
	|         +-- UnicodeTranslateError  # Unicode转码错误      
	+-- Warning  					# 警告的基类           
	+-- DeprecationWarning  		# 有关已弃用功能的警告的基类           
	+-- PendingDeprecationWarning   # 有关不推荐使用功能的警告的基类           
	+-- RuntimeWarning   		    # 有关可疑的运行时行为的警告的基类           
	+-- SyntaxWarning  	 			# 关于可疑语法警告的基类           
	+-- UserWarning  	 			# 用户代码生成警告的基类           
	+-- FutureWarning  	 			# 有关已弃用功能的警告的基类           
	+-- ImportWarning  	 			# 关于模块导入时可能出错的警告的基类           
	+-- UnicodeWarning   			# 与Unicode相关的警告的基类           
	+-- BytesWarning  	 			# 与bytes和bytearray相关的警告的基类           
	+-- ResourceWarning  			# 与资源使用相关的警告的基类。被默认警告过滤器忽略
```

> 二、异常捕获

* 捕获异常：使用try	except捕获异常
	* try：将可能报错的代码放入try的子句中
	* except：捕获指定异常，返回给上一层
	* finally：无论是否发生异常，都执行子句

```python
def func(a):
    try:
		a = int(a)
    except ValueError:
        print("输入的数据异常，请检查后再次输入")
    else:
        print(type(a))
    finally:
        print("继续运行")
func("qwe")
# 输出结果：输入的数据异常，请检查后再次输入
```

> 三、主动抛异常

- 抛异常：主动抛出异常，反馈消息给上层调用者情况

```python
def func(x, y):
	if y == 0:
		raise ZeroDivisionError("0不能做分母")
	return x/y
func(10, 0)
# 输出结果：ZeroDivisionError: 0不能做分母
```

- 异常信息收集：当抛出异常后，将错误的详细信息（包括第几行，什么错误）存放到日志中
	- 导入模块：import traceback
