# Python枚举类定义和使用（详解版） #

在Python中没有内置的枚举方法，起初模仿实现枚举属性的方式是

	class Directions:
	    NORTH = 1
	    EAST = 2
	    SOUTH = 3
	    WEST = 4
使用成员：

	Direction.EAST 
	Direction.SOUTH 
检查成员：

	>>> print("North的类型：", type(Direction.NORTH))
	>>> print(isinstance(Direction.EAST, Direction))
	North的类型： <class 'int'>
	False
成员NORTH的类型是int，而不是Direction，这个做法只是简单地将属性定义到类中

Python标准库enum实现了枚举属性的功能，接下来介绍enum的在实际工作生产中的用法

## 1.为什么要用enum，什么时候使用enum? ##
enum规定了一个有限集合的属性，限定只能使用集合内的值，明确地声明了哪些值是合法值，，如果输入不合法的值会引发错误，只要是想要从一个限定集合取值使用的方式就可以使用enum来组织值。

## 2.enum的定义/声明 ##

	from enum import Enum
	
	
	class Directions(Enum):
	    NORTH = 1
	    EAST = 2
	    SOUTH = 3
	    WEST = 4

使用和类型检查：

	>>> Directions.EAST
	<Directions.EAST: 2>
	>>> Directions.SOUTH
	<Directions.SOUTH: 3>
	>>> Directions.EAST.name
	'EAST'
	>>> Directions.EAST.value
	2
	>>> print("South的类型：", type(Directions.SOUTH))
	South的类型： <enum 'Directions'>
	>>> print(isinstance(Directions.EAST, Directions))
	True
	>>> 

检查示例South的的类型，结果如期望的是Directions。name和value是两个有用的附加属性。

## 下面程序演示了如何定义一个枚举类： ##

	from enum import Enum
	class Color(Enum):
	    # 为序列值指定value值
	    red = 1
	    green = 2
	    blue = 3

如果想将一个类定义为枚举类，只需要令其继承自 enum 模块中的 Enum 类即可。例如在上面程序中，Color 类继承自 Enum 类，则证明这是一个枚举类。

## 枚举类成员之间不能比较大小，但可以用 == 或者 is 进行比较是否相等 ##，例如：

	print(Color.red == Color.green)
	print(Color.red.name is Color.green.name)
输出结果为：

	Flase
	Flase

枚举类还提供了一个 __members__ 属性，该属性是一个包含枚举类中所有成员的字典，通过遍历该属性，也可以访问枚举类中的各个成员。例如：

	for name,member in Color.__members__.items():
	    print(name,"->",member)
输出结果为：

	red -> Color.red
	green -> Color.green
	blue -> Color.blue

## 值得一提的是，Python 枚举类中各个成员必须保证 name 互不相同，但 value 可以相同 ##，举个例子：

	from enum import Enum
	class Color(Enum):
	    # 为序列值指定value值
	    red = 1
	    green = 1
	    blue = 3
	print(Color['green'])
输出结果为：

	Color.red
可以看到，Color 枚举类中 red 和 green 具有相同的值（都是 1），Python 允许这种情况的发生，它会将 green 当做是 red 的别名，因此当访问 green 成员时，最终输出的是 red。

在实际编程过程中，如果想避免发生这种情况，可以借助 @unique 装饰器，这样当枚举类中出现相同值的成员时，程序会报 ValueError 错误。例如：
	
	#引入 unique
	from enum import Enum,unique
	#添加 unique 装饰器
	@unique
	class Color(Enum):
	    # 为序列值指定value值
	    red = 1
	    green = 1
	    blue = 3
	print(Color['green'])
运行程序会报错：

	Traceback (most recent call last):
	  File "D:\python3.6\demo.py", line 3, in <module>
	    class Color(Enum):
	  File "D:\python3.6\lib\enum.py", line 834, in unique
	    (enumeration, alias_details))
	ValueError: duplicate values found in <enum 'Color'>: green -> red
除了通过继承 Enum 类的方法创建枚举类，还可以使用 Enum() 函数创建枚举类。例如：

	from enum import Enum
	#创建一个枚举类
	Color = Enum("Color",('red','green','blue'))
	
	#调用枚举成员的 3 种方式
	print(Color.red)
	print(Color['red'])
	print(Color(1))
	#调取枚举成员中的 value 和 name
	print(Color.red.value)
	print(Color.red.name)
	#遍历枚举类中所有成员的 2 种方式
	for color in Color:
	    print(color)

Enum() 函数可接受 2 个参数，第一个用于指定枚举类的类名，第二个参数用于指定枚举类中的多个成员。

如上所示，仅通过一行代码，即创建了一个和前面的 Color 类相同的枚举类。运行程序，其输出结果为：

	Color.red
	Color.red
	Color.red
	1
	red
	Color.red
	Color.green
	Color.blue
