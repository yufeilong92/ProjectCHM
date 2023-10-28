
# Python自带    #

## 文件写入 write() 方法 ##
write() 方法是其中之一，用于将数据写入文件。
	# 打开一个文件
	file = open("newfile.txt", "w")
	
	# 写入一行数据
	file.write("Hello World, Python 3!")
	
	# 关闭文件
	file.close()
### 如何使用 write() 方法向文件写入多行数据，并使用换行符分隔它们： ###
	# 打开一个文件
	file = open("newfile.txt", "w")
	
	# 写入多行数据
	lines = ["First line.\n", "Second line.\n", "Third line.\n"]
	file.writelines(lines)
	
	# 关闭文件
	file.close()
在这个例子中，我们使用了 writelines() 方法，将多行数据写入文件。请注意每一行数据末尾的换行符 “\n”，以确保每行数据都放在单独的一行上。

如果您希望在写入多行数据时，每个数据之间都有一些分隔符，则可以使用 join() 方法，将数据列表中的数据连接为一个字符串，然后再向文件写入该字符串。
	# 打开一个文件
	file = open("newfile.txt", "w")
	
	# 写入多行数据
	lines = ["First line", "Second line", "Third line"]
	file.write("\n".join(lines))
	
	# 关闭文件
	file.close()
在这个例子中，我们将数据列表中的数据使用 “\n” 连接为一个字符串，然后在写入该字符串时，确保字符串末尾有一个换行符。


## 文件的close()方法 ##
#打开文件
	f = open('file.txt', 'r')
	print(f.read())
	
	#关闭文件
	f.close()
	
	#再次调用read方法会报错
	# print(f.read())  #此行代码会抛出如下异常:
	"""
	Traceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	ValueError: I/O operation on closed file.
	"""
### 文件操作模式的描述： ###
- r : 以只读方式打开文件。文件指针放在文件开头。 如果文件不存在，则会发生异常。
- w : 以写入方式打开文件。如果文件存在则覆盖，文件不存在则创建文件。文件指针放在文件开头。
- a : 以追加方式打开文件。如果文件存在，文件指针会放到文件结尾位置。如果文件不存在，则会创建一个新文件

### 对应于不同的文件操作模式，close()方法的行为可能略有不同： ###
- r模式下，close()方法功能相对简单，只是关闭文件，内部状态基本不受影响。
- w模式下，close()方法的作用是将写入缓冲区中的数据刷新到磁盘文件中，并关闭文件。
- a模式下，close()方法的行为类似于w模式，在关闭文件之前会将追加写入缓冲区中的数据刷新到磁盘文件中

### 演示文件操作模式为w和a时，使用close()方法的正确方式 ###
# 文件操作模式为 w
	f = open('test.txt', 'w')
	f.write('hello world')
	f.close()
	
	# 文件操作模式为 a
	f = open('test.txt', 'a')
	f.write('\nappend string!')
	f.close()

### 文件 next() 方法 ###

使用文件对象的next()方法逐行读取文件内容。该方法会从文件中读取下一行数据，直到到达文件结尾。

	# 打开文件
	f = open("test.txt", "r")
	
	# 逐行读取文件内容
	line = f.readline()
	while line:
	    print(line)
	    line = f.readline()
	
	#关闭文件
	f.close()

上述代码中，我们首先以只读模式打开了一个名为“test.txt”的文件。然后，我们使用 while 循环逐行读取文件内容并将其打印出来，直到文件结束。最后，我们关闭文件。

除了 readline() 方法外，我们还可以使用 fileinput 模块来实现逐行遍历文件内容的功能。

下面是一个使用 fileinput 模块实现逐行读取文件的示例代码：
	import fileinput
	
	# 打开文件
	with fileinput.input(files=('test.txt')) as f:
	    # 逐行处理文件内容
	    for line in f:
	        print(line, end='')
上述代码中，我们首先读取文件并使用 with 语句创建一个文件输入对象。通过 for 循环逐行处理文件内容并将其打印出来。此时，end=” 参数可以防止 print() 函数在每行末尾添加换行符。

### 文件读取（read()）方法 ###

#### read()方法用于读取文件内容 ####
    file.read([size])

其中，size参数可选，表示要从文件中读取的字节数。如果不设置size，则默认读取整个文件。read()方法返回的是字符串类型。
另外，如果使用read()方法读取的字节数多于文件本身包含的实际字节数，则会返回文件中所有内容。

下面我们通过示例代码来演示如何使用read()方法。
	# 打开文件
	file = open("test.txt", "r")
	
	# 读取整个文件内容
	content = file.read()
	
	# 输出读取到的字符串
	print(content)
	
	# 关闭文件
	file.close()

#### 可以尝试使用size参数来读取文件指定长度的内容 ####

	# 打开文件
	file = open("test.txt", "r")
	
	# 读取前15个字节的内容
	content = file.read(15)
	
	# 输出读取到的字符串
	print(content)
	
	# 关闭文件
	file.close()
上述代码中，我们使用read()方法读取了test.txt的前15个字节的内容，并将它们存储在变量content中.

#### 文件readlines()方法 ####

readlines()方法是其中的一个常用方法，可以读取整个文件并返回一个列表，列表中的每个元素代表文件中的一行。

#### readlines()方法 ####

    file.readlines(sizehint=-1, /)
其中，file表示要读取的文件名或文件对象，sizehint表示读取多少字节（以字节为单位）。sizehint默认为-1，表示读取整个文件。

返回值是一个列表，列表中的每个元素代表文件中的一行。

使用readlines()方法读取整个文件的示例代码：

	
	# 打开文件
	with open('example.txt', 'r') as f:
	  # 读取整个文件
	  lines = f.readlines()
	  # 输出文件内容
	  for line in lines:
	    print(line)
这段代码中，我们打开了名为example.txt的文件，并将其作为一个文件对象f打开。使用f.readlines()方法读取整个文件，并返回一个列表lines。接着，我们将列表中的每一行逐一输出。

#### 读取指定大小的内容 ####
同时，您也可以使用readlines()方法来读取指定大小的内容。sizehint参数控制读取的字节数，即使文件中不止一行，读取的字节数也不会超过sizehint指定的大小。例如，下面的代码只会读取文件的前10个字节

	with open('example.txt', 'r') as f:
	  lines = f.readlines(10)
	  for line in lines:
	    print(line)
This is a 


# os.access() 方法 #
os.access()用于检测文件或目录是否具有指定的访问权限。该方法返回True或False。

    os.access(path, mode)

**参数**

- path：要检测的路径。
- mode：文件访问模式，它是一个由以下访问模式组成的组合：os.F_OK（用于测试路径的存在），os.R_OK（测试路径是否可读），os.W_OK（测试路径是否可写），os.X_OK（测试路径是否可执行）。

**返回值**



# os.fdopen() 方法 #
用于将文件描述符fd打开为文件对象，mode标志为读写。

**语法**
os.fdopen(fd, mode=’r’, buffering=-1, *, opener=None)

- fd – 打开的文件描述符。该描述符必须以读或写模式打开。
- mode – 要使用的模式标志。默认为“ r”（读取）。其他可用模式为w、a、r+、w+和a+。
- buffering – 可选参数，用于设置缓冲区的大小。默认情况下，缓冲区大小为-1，表示缓冲区的大小由系统自动决定。
- opener – 可选参数，用于在打开文件时安装自定义打开器。默认为None。


**参数说明**

- fd – 一个代表已打开的文件的文件描述符。在 Unix 系统中，一个文件描述符是一个小整数，表示内核为每个进程维护的打开文件之一的引用。在 Windows 系统中，它代表了一个文件句柄。打开的文件描述符必须以读或写模式打开。
- mode – 一个用于描述文件的开放模式的字符串。mode可以包含以下字符串中的一个或多个。
	- r – 读取
	- w – 写
	- a – 追加
	- r+ – 读写
	- w+ – 读写
	- a+ – 读写
- buffering – 如果 buffering 的值被设为 0，就不会有寄存。如果 buffering 的值取 1，访问文件时会寄存行。如果将 buffering 的值设为大于 1 的整数，表示这就是的寄存区的缓冲大小。如果取负值，则会使用系统默认寄存区缓冲大小。通常,二进制模式下缺省为全缓冲,文本模式下则行缓冲。
- opener – 如果文件无法被打开，则调用默认的 opener()函数。如果需要指定另外的函数，则可以使用该参数指定。该函数必须接受两个参数。

打开文件的模式的含义稍微解释一下。读取模式为’r’,写入模式为’w’,追加模式为’a’,读写模式为’r+’,读写模式为’w+’，读写模式为’a+’。
	
	# 打开一个文件
	fd = os.open( "foo.txt", os.O_CREAT|os.O_RDWR )
	
	# 将一个描述符关闭
	os.close( fd )
	
	# 打开 foo.txt 文件
	fo = os.fdopen(fd, "w+")
	print ("文件名为: ", fo.name)
	
	# 写入内容
	fo.write( "Python IO 实例之 os.fdopen3" )
	
	# 关闭文件
	os.close( fd )
	print ("关闭文件成功!!")






如果文件或目录具有访问权限，则返回True，否则返回False。
    import os
    
    # 检测文件是否存在
    f_exist = os.access('/home/user/test.txt', os.F_OK)
    print(f_exist)
    
    # 检测文件是否可读
    f_read = os.access('/home/user/test.txt', os.R_OK)
    print(f_read)
    
    # 检测文件是否可写
    f_write = os.access('/home/user/test.txt', os.W_OK)
    print(f_write)


<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">属性</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>
	<tr style="background-color: aqua;">
		<td>os.path.exists()</td>
		<td>False 不存在；True 存在</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>os.listdir()</td>
		<td>显示出路径下所有文件名称</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>os.makedirs()</td>
		<td>用于递归创建目录。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>os.access()</td>
		<td>检测文件或目录是否具有指定的访问权限。该方法返回True或False。</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>xxxx</td>
		<td>xxxx</td>
	</tr>

	<tr style="background-color: aquamarine;">
		<td>xxx</td>
		<td>xxxx</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>xxxx</td>
		<td>xxxx</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>xxx</td>
		<td>xxxx</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>xxxx</td>
		<td>xxxx</td>
	</tr>

</table>



#  列出目录中的文件的方法

##使用os.listdir()

    import os
    os.listdir()
### 如果我们想基于特定路径来打印结果，只需传递给函数os.listdir() 相应的参数，举例如下：
    >>> os.listdir(myPath)
###  如果我们只想打印所有文件不包含目录，那么我们可以使用os.path.isfile() 来进行相应的过滤，
    >>> import os
    >>> files = [f for f in os.listdir() if os.path.isfile(f)]
###当然，对于目录，同样可以使用函数os.path.isdir() 进行过滤，代码如下：
    import os
    files = [f for f in os.listdir() if os.path.isdir(f)]
##使用os.walk()
os模块中还有另一个方法 os.walk() 。顾名思义，它可以一层一层地“遍历”目录树。当我们调用os.walk() 函数时，它将返回一个生成器。此时每次调用next() 方法生成下一个值时，它都会进入到一个layer ，结果是一个包含3个项的元组：(dirpath、dirname、filename) 。

如果要获取第二层中所有文件夹的名称，
    from os import walk
    
    f = []
    layer = 1
    w = walk("/Users/zhao")
    for (dirpath, dirnames, filenames) in w:
    if layer == 2:
    f.extend(dirnames)
    break
    layer += 1
##使用pathlib
从Python 3.4开始，有一个名为pathlib 的模块也很有用。
借助列表生成式的技巧，我们只需使用一行代码即可生成当前路径的所有文件名：
    import pathlib
    
    files = [f for f in pathlib.Path().iterdir() if f.is_file()]
令人奇怪的是，Path() 还附带了glob() 函数。（无需在Python文件顶部显式导入glob模块）
    import pathlib
    
    files = [f for f in pathlib.Path().glob("/sys/*.log")]
##使用os.scandir()
经典的os.listdir() 函数很直观，但对于包含大量文件的大型目录来说效率并不高。因此，Python 3.5引入了一个新的功能类似的函数os.scandir() 。
    >>> a=os.scandir()
    >>> next(a)
    <DirEntry 'test1.py'>
    >>> next(a)
    <DirEntry 'test2.py'>
