# C++ 学习笔记
- C++ : C Plus Plus
- 编译 + 链接 过程 连接完才是完整的可执行文件了
- 静态链接 VS 动态链接
- got 共享内存  地址无关代码

# Python 学习
- 缩进 大小写敏感
- input() print() 输入输出
- 整数 浮点数 字符串 布尔值 控制None 变量
- list 有序集合列表: classmates = ['zhangsan', 'wangwu', 'lisi']
    - len() 个数
    - 下标访问 classmates[0] classmates[-1] 最后一个元素
    - append() 追加元素到末尾
    - insert(i, xxx)  指定下标插入
    - pop() 删除末尾元素
    - pop(i) 删除指定索引位置
- tuple 不可变有序列表 元组
-  循环
    - for x in xxxx
    - while n > 0 :  break continue
- dict 全称dictionary, 对应其他语言中的map 
    - d = {'Michael': 95, 'bob': 75, 'Tracy': 85}
    - d['bob']
    - 如果key 不存在 dict会报错
    - get() 方法如果key 不存在可以返回None
- set
- 函数
    - help(abs) 查看帮助文档
    - abs(100) 函数调用
    - 函数定义: def my_abs(x):
    - 函数的参数：
        - 位置参数 def power(x):
        - 默认参数 不传的时候取默认参数  -- 默认参数必须指向不  变对象  如果没有参数的情况下多次调用出问题
            - def power(x, n=2):
        - 可变参数 *numbers tuple 接收  (1,2,3)  加*传递list
            - def calc(*numbers): calc(1,2,3)
        - 关键字参数：**kw  自动组装为dict 同样可以 ** 传递dict 参数
            - def person(name, age, **kw): 
        - 命名关键字参数
            - def person(name, age, *, city, job) * 之后的位命名关键字
            - def person(name, age, *, city='Beijing', job):  person('Jack', 24, job='Engineer')
- Slice
    - L[0:3]
- 内置模块引用
    - import sys
    - `__name__` 命令行模式下该名称为 `__main__` 为了 在命令行中测试
    - 特殊变量可以直接被引用 `__xx__`
    - 非公开的 _xx 和 _xxx
- 安装第三方模块
    - pip install Pillow 
- 面向对象
    - 类
        - `__init__` 类中函数第一个参数永远是self 变量
    - 继承与多态
    - 动态语言堕胎  鸭子类型 有对应方法能跑方法就行了 file-like object
    - type() 获取对象类型
    - isinstance() 继承链上的都可以
    - dir()
    - getattr() setattr() hasattr()
- 面向对象高级
    - 动态绑定 属性，实例方法，类方法
    - `__slots__` 限定实例能添加的属性
    - @property
    - 多重继承: class Dog(Mammal, Runnable)
    - MixIn  class Dog(Mammal, RunnableMixIn)
    - `__str__`
    - `__iter__`
    - `__getitem__`
    - metaclass
- 多进程 & 多线程
    - multiprocessing 模块
    - 子进程要执行的代码 & Process 方法 创建Process 实例
    - start() 启动子进程
    - join() 等待子进程执行结束后执行  用于进程间同步
    - Pool() p.close() close 后不能继续添加新的Process
    - 进程间通信
        - Queue
        - 
