# Python list列表详解 #
从形式上看，列表会将所有元素都放在一对中括号[ ]里面，相邻元素之间用逗号,分隔，如下所示：

	[element1, element2, element3, ..., elementn]

从内容上看，列表可以存储整数、小数、字符串、列表、元组等任何类型的数据，并且同一个列表中元素的类型也可以不同。比如说：

    ["http://c.biancheng.net/python/", 1, [2,3,4] , 3.0]

## 1. Python创建列表 ##
创建列表的方法可分为两种，
### 1.1) 使用 [ ] 直接创建列表 ###

使用[ ]创建列表后，一般使用=将它赋值给某个变量，具体格式如下：

	listname = [element1 , element2 , element3 , ... , elementn]

其中，listname 表示变量名，element1 ~ elementn 表示列表元素。

### 1.2) 使用 list() 函数创建列表 ###

除了使用[ ]创建列表外，Python 还提供了一个内置的函数 list()，使用它可以将其它数据类型转换为列表类型。例如：

	#将字符串转换成列表
	list1 = list("hello")
	print(list1)
	
	#将元组转换成列表
	tuple1 = ('Python', 'Java', 'C++', 'JavaScript')
	list2 = list(tuple1)
	print(list2)
	
	#将字典转换成列表
	dict1 = {'a':100, 'b':42, 'c':9}
	list3 = list(dict1)
	print(list3)
	
	#将区间转换成列表
	range1 = range(1, 6)
	list4 = list(range1)
	print(list4)
	
	#创建空列表
	print(list())

运行结果：

	['h', 'e', 'l', 'l', 'o']
	['Python', 'Java', 'C++', 'JavaScript']
	['a', 'b', 'c']
	[1, 2, 3, 4, 5]
	[]

## 访问列表元素 ##

使用索引访问列表元素的格式为：

	listname[i]

其中，listname 表示列表名字，i 表示索引值。列表的索引可以是正数，也可以是负数。

使用切片访问列表元素的格式为：

	listname[start : end : step]
其中，listname 表示列表名字，start 表示起始索引，end 表示结束索引，step 表示步长。

## Python删除列表 ##
对于已经创建的列表，如果不再使用，可以使用del关键字将其删除。

实际开发中并不经常使用 del 来删除列表，因为 Python 自带的垃圾回收机制会自动销毁无用的列表，即使开发者不手动删除，Python 也会自动将其回收。

del 关键字的语法格式为：

	del listname
其中，listname 表示要删除列表的名称。

	intlist = [1, 45, 8, 34]
	print(intlist)
	del intlist
	print(intlist)

运行结果：
	[1, 45, 8, 34]
	Traceback (most recent call last):
	    File "C:\Users\mozhiyan\Desktop\demo.py", line 4, in <module>
	        print(intlist)
	NameError: name 'intlist' is not defined

## Python list列表添加元素的3种方法 ##

使用+运算符可以将多个序列连接起来；列表是序列的一种，所以也可以使用+进行连接，这样就相当于在第一个列表的末尾添加了另一个列表。

	language = ["Python", "C++", "Java"]
	birthday = [1991, 1998, 1995]
	info = language + birthday
	
	print("language =", language)
	print("birthday =", birthday)
	print("info =", info)

运行结果：
	language = ['Python', 'C++', 'Java']
	birthday = [1991, 1998, 1995]
	info = ['Python', 'C++', 'Java', 1991, 1998, 1995]

从运行结果可以发现，使用+会生成一个新的列表，原有的列表不会被改变。


> +更多的是用来拼接列表，而且执行效率并不高，如果想在列表中插入元素，应该使用下面几个专门的方法。

## Python append()方法添加元素 ##

append() 方法用于在列表的末尾追加元素，该方法的语法格式如下：

	listname.append(obj)
其中，listname 表示要添加元素的列表；obj 表示到添加到列表末尾的数据，它可以是单个元素，也可以是列表、元组等。

	l = ['Python', 'C++', 'Java']
	#追加元素
	l.append('PHP')
	print(l)
	
	#追加元组，整个元组被当成一个元素
	t = ('JavaScript', 'C#', 'Go')
	l.append(t)
	print(l)
	
	#追加列表，整个列表也被当成一个元素
	l.append(['Ruby', 'SQL'])
	print(l)

运行结果为：

	['Python', 'C++', 'Java', 'PHP']
	['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go')]
	['Python', 'C++', 'Java', 'PHP', ('JavaScript', 'C#', 'Go'), ['Ruby', 'SQL']]

## Python extend()方法添加元素 ##

extend() 和 append() 的不同之处在于：extend() 不会把列表或者元祖视为一个整体，而是把它们包含的元素逐个添加到列表中。

extend() 方法的语法格式如下：

	listname.extend(obj)
其中，listname 指的是要添加元素的列表；obj 表示到添加到列表末尾的数据，它可以是单个元素，也可以是列表、元组等，但不能是单个的数字。
	
	l = ['Python', 'C++', 'Java']
	#追加元素
	l.extend('C')
	print(l)
	
	#追加元组，元祖被拆分成多个元素
	t = ('JavaScript', 'C#', 'Go')
	l.extend(t)
	print(l)
	
	#追加列表，列表也被拆分成多个元素
	l.extend(['Ruby', 'SQL'])
	print(l)

运行结果：

	['Python', 'C++', 'Java', 'C']
	['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go']
	['Python', 'C++', 'Java', 'C', 'JavaScript', 'C#', 'Go', 'Ruby', 'SQL']

## Python insert()方法插入元素 ##

append() 和 extend() 方法只能在列表末尾插入元素，如果希望在列表中间某个位置插入元素，那么可以使用 insert() 方法。

insert() 的语法格式如下：

	listname.insert(index , obj)

其中，index 表示指定位置的索引值。insert() 会将 obj 插入到 listname 列表第 index 个元素的位置。

当插入列表或者元祖时，insert() 也会将它们视为一个整体，作为一个元素插入到列表中，这一点和 append() 是一样的。

	l = ['Python', 'C++', 'Java']
	#插入元素
	l.insert(1, 'C')
	print(l)
	
	#插入元组，整个元祖被当成一个元素
	t = ('C#', 'Go')
	l.insert(2, t)
	print(l)
	
	#插入列表，整个列表被当成一个元素
	l.insert(3, ['Ruby', 'SQL'])
	print(l)
	
	#插入字符串，整个字符串被当成一个元素
	l.insert(0, "http://c.biancheng.net")
	print(l)

输出结果为：

	['Python', 'C', 'C++', 'Java']
	['Python', 'C', ('C#', 'Go'), 'C++', 'Java']
	['Python', 'C', ('C#', 'Go'), ['Ruby', 'SQL'], 'C++', 'Java']
	['http://c.biancheng.net', 'Python', 'C', ('C#', 'Go'), ['Ruby', 'SQL'], 'C++', 'Java']

## Python list列表删除元素（4种方法） ##

在 Python 列表中删除元素主要分为以下 3 种场景：

- 根据目标元素所在位置的索引进行删除，可以使用 del 关键字或者 pop() 方法；
- 根据元素本身的值进行删除，可使用列表（list类型）提供的 remove() 方法；
- 将列表中所有元素全部删除，可使用列表（list类型）提供的 clear() 方法。
### del：根据索引值删除元素 ###

del 可以删除列表中的单个元素，格式为：

    del listname[index]

其中，listname 表示列表名称，index 表示元素的索引值。

del 也可以删除中间一段连续的元素，格式为：

    del listname[start : end]

其中，start 表示起始索引，end 表示结束索引。del 会删除从索引 start 到 end 之间的元素，不包括 end 位置的元素。

### pop()：根据索引值删除元素 ###

Python pop() 方法用来删除列表中指定索引处的元素，具体格式如下：

	listname.pop(index)

其中，listname 表示列表名称，index 表示索引值。如果不写 index 参数，默认会删除列表中的最后一个元素，类似于数据结构中的“出栈”操作。
	
	nums = [40, 36, 89, 2, 36, 100, 7]
	nums.pop(3)
	print(nums)
	nums.pop()
	print(nums)
运行结果：

	[40, 36, 89, 36, 100, 7]
	[40, 36, 89, 36, 100]

### remove()：根据元素值进行删除 ###

除了 del 关键字，Python 还提供了 remove() 方法，该方法会根据元素本身的值来进行删除操作。

需要注意的是，remove() 方法只会删除第一个和指定值相同的元素，而且必须保证该元素是存在的，否则会引发 ValueError 错误。

	nums = [40, 36, 89, 2, 36, 100, 7]
	#第一次删除36
	nums.remove(36)
	print(nums)
	#第二次删除36
	nums.remove(36)
	print(nums)
	#删除78
	nums.remove(78)
	print(nums)
运行结果：

	[40, 89, 2, 36, 100, 7]
	[40, 89, 2, 100, 7]
	Traceback (most recent call last):
	    File "C:\Users\mozhiyan\Desktop\demo.py", line 9, in <module>
	        nums.remove(78)
	ValueError: list.remove(x): x not in list

最后一次删除，因为 78 不存在导致报错，所以我们在使用 remove() 删除元素时最好提前判断一下。

### clear()：删除列表所有元素 ###

Python clear() 用来删除列表的所有元素，也即清空列表，请看下面的代码：

	url = list("http://c.biancheng.net/python/")
	url.clear()
	print(url)

运行结果：

	[]

## Python list列表修改元素 ##

### 1.修改单个元素 ###
修改单个元素非常简单，直接对元素赋值即可。

	nums = [40, 36, 89, 2, 36, 100, 7]
	nums[2] = -26  #使用正数索引
	nums[-3] = -66.2  #使用负数索引
	print(nums)
运行结果：

	[40, 36, -26, 2, -66.2, 100, 7]

使用索引得到列表元素后，通过=赋值就改变了元素的值。

### 2.修改一组元素 ###

Python 支持通过切片语法给一组元素赋值。在进行这种操作时，如果不指定步长（step 参数），Python 就不要求新赋值的元素个数与原来的元素个数相同；这意味，该操作既可以为列表添加元素，也可以为列表删除元素。

	nums = [40, 36, 89, 2, 36, 100, 7]

	#修改第 1~4 个元素的值（不包括第4个元素）
	nums[1: 4] = [45.25, -77, -52.5]
	print(nums)

运行结果：

	[40, 45.25, -77, -52.5, 36, 100, 7]

如果对空切片（slice）赋值，就相当于插入一组新的元素：

	nums = [40, 36, 89, 2, 36, 100, 7]
	#在4个位置插入元素
	nums[4: 4] = [-77, -52.5, 999]
	print(nums)
运行结果：

	[40, 36, 89, 2, -77, -52.5, 999, 36, 100, 7]

## Python list列表查找元素 ##

Python 列表（list）提供了 index() 和 count() 方法，它们都可以用来查找元素。

### index() 方法 ###

index() 方法用来查找某个元素在列表中出现的位置（也就是索引），如果该元素不存在，则会导致 ValueError 错误，所以在查找之前最好使用 count() 方法判断一下。

index() 的语法格式为：

	listname.index(obj, start, end)

其中，listname 表示列表名称，obj 表示要查找的元素，start 表示起始位置，end 表示结束位置。

start 和 end 参数用来指定检索范围：

- start 和 end 可以都不写，此时会检索整个列表；
- 如果只写 start 不写 end，那么表示检索从 start 到末尾的元素；
- 如果 start 和 end 都写，那么表示检索 start 和 end 之间的元素。

index() 方法会返回元素所在列表中的索引值。

### count()方法 ###

count() 方法用来统计某个元素在列表中出现的次数，基本语法格式为：

	listname.count(obj)

其中，listname 代表列表名，obj 表示要统计的元素。

如果 count() 返回 0，就表示列表中不存在该元素，所以 count() 也可以用来判断列表中的某个元素是否存在。

	nums = [40, 36, 89, 2, 36, 100, 7, -20.5, 36]
	#统计元素出现的次数
	print("36出现了%d次" % nums.count(36))
	#判断一个元素是否存在
	if nums.count(100):
	    print("列表中存在100这个元素")
	else:
	    print("列表中不存在100这个元素")

运行结果：

	36出现了3次
	列表中存在100这个元素
