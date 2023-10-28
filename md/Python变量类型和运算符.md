# Python变量类型和运算符 #

## Python变量的定义和使用 ##

### 1.变量的赋值 ###
Python 使用等号=作为赋值运算符，具体格式为：

    name = value

### 2) 对引号进行转义 ###
在引号前面添加反斜杠\就可以对引号进行转义，让 Python 把它作为普通文本对待，例如：

	str1 = 'I\'m a great coder!'
	str2 = "引文双引号是\"，中文双引号是“"
	print(str1)
	print(str2)
运行结果：

    I'm a great coder!
    引文双引号是"，中文双引号是“

# Python input()函数 #
input() 函数总是以字符串的形式来处理用户输入的内容，所以用户输入的内容可以包含任何字符。

input() 函数的用法为：

    str = input(tipmsg)

字符串转换成想要的类型


- int(string) 将字符串转换成 int 类型；


- float(string) 将字符串转换成 float 类型；


- bool(string) 将字符串转换成 bool 类型。

# Python格式化字符串（格式化输出） #

print() 函数使用以%开头的转换说明符对各种类型的数据进行格式化输出，具体请看下表：
<br />
<table>
<caption>
表 1 Python 转换说明符</caption>
<tbody>
<tr>
<th>
转换说明符</th>
<th>
解释</th>
</tr>
<tr>
<td>
%d、%i</td>
<td>
转换为带符号的十进制整数</td>
</tr>
<tr>
<td>
%o</td>
<td>
转换为带符号的八进制整数</td>
</tr>
<tr>
<td>
%x、%X</td>
<td>
转换为带符号的十六进制整数</td>
</tr>
<tr>
<td>
%e</td>
<td>
转化为科学计数法表示的浮点数（e 小写）</td>
</tr>
<tr>
<td>
%E</td>
<td>
转化为科学计数法表示的浮点数（E 大写）</td>
</tr>
<tr>
<td>
%f、%F</td>
<td>
转化为十进制浮点数</td>
</tr>
<tr>
<td>
%g</td>
<td>
智能选择使用 %f 或 %e 格式</td>
</tr>
<tr>
<td>
%G</td>
<td>
智能选择使用 %F 或 %E 格式</td>
</tr>
<tr>
<td>
%c</td>
<td>
格式化字符及其 ASCII 码</td>
</tr>
<tr>
<td>
%r</td>
<td>
使用 repr() 函数将表达式转换为字符串</td>
</tr>
<tr>
<td>
%s</td>
<td>
使用 str() 函数将表达式转换为字符串</td>
</tr>
</tbody>
</table>
<br />

转换说明符（Conversion Specifier）只是一个占位符，它会被后面表达式（变量、常量、数字、字符串、加减乘除等各种形式）的值代替。

【实例】输出一个整数：

	age = 8
	print("C语言中文网已经%d岁了！" % age)
运行结果：
C语言中文网已经8岁了！

在 print() 函数中，由引号包围的是格式化字符串，它相当于一个字符串模板，可以放置一些转换说明符（占位符）。本例的格式化字符串中包含一个%d说明符，它最终会被后面的 age 变量的值所替代。

中间的%是一个分隔符，它前面是格式化字符串，后面是要输出的表达式。

当然，格式化字符串中也可以包含多个转换说明符，这个时候也得提供多个表达式，用以替换对应的转换说明符；多个表达式必须使用小括号( )包围起来。

	name = "C语言中文网"
	age = 8
	url = "http://c.biancheng.net/"
	print("%s已经%d岁了，它的网址是%s。" % (name, age, url))
运行结果：
C语言中文网已经8岁了，它的网址是http://c.biancheng.net/。
## 指定最小输出宽度 ##

当使用表1中的转换说明符时，可以使用下面的格式指定最小输出宽度（至少占用多少个字符的位置）：


- %10d 表示输出的整数宽度至少为 10；


- %20s 表示输出的字符串宽度至少为 20。

请看下面的演示：

	n = 1234567
	print("n(10):%10d." % n)
	print("n(5):%5d." % n)
	
	url = "http://c.biancheng.net/python/"
	print("url(35):%35s." % url)
	print("url(20):%20s." % url)
运行结果：

	n(10):   1234567.
	n(5):1234567.
	url(35):     http://c.biancheng.net/python/.
	url(20):http://c.biancheng.net/python/.

# Python转义字符及用法 #

Python 支持的转义字符

<br />
<table>
<caption>
表 1 Python 支持的转义字符</caption>
<tbody>
<tr>
<th>
转义字符</th>
<th>
说明</th>
</tr>
<tr>
<td>
\n</td>
<td>
换行符，将光标位置移到下一行开头。</td>
</tr>
<tr>
<td>
\r</td>
<td>
回车符，将光标位置移到本行开头。</td>
</tr>
<tr>
<td>
\t</td>
<td>
水平制表符，也即 Tab 键，一般相当于四个空格。</td>
</tr>
<tr>
<td>
\a</td>
<td>
蜂鸣器响铃。注意不是喇叭发声，现在的计算机很多都不带蜂鸣器了，所以响铃不一定有效。</td>
</tr>
<tr>
<td>
\b</td>
<td>
退格（Backspace），将光标位置移到前一列。</td>
</tr>
<tr>
<td>
\\</td>
<td>
反斜线</td>
</tr>
<tr>
<td>
\&#39;</td>
<td>
单引号</td>
</tr>
<tr>
<td>
\&quot;</td>
<td>
双引号</td>
</tr>
<tr>
<td>
\</td>
<td>
在字符串行尾的续行符，即一行未完，转到下一行继续写。</td>
</tr>
</tbody>
</table>
<br />
转义字符在书写形式上由多个字符组成，但 Python 将它们看作是一个整体，表示一个字符。<br />
<br />

#使用\t排版
	str1 = '网站\t\t域名\t\t\t年龄\t\t价值'
	str2 = 'C语言中文网\tc.biancheng.net\t\t8\t\t500W'
	str3 = '百度\t\twww.baidu.com\t\t20\t\t500000W'
	print(str1)
	print(str2)
	print(str3)
	
	print("--------------------")
	
	# \n在输出时换行，\在书写字符串时换行
	info = "Python教程：http://c.biancheng.net/python/\n\
	C++教程：http://c.biancheng.net/cplus/\n\
	Linux教程：http://c.biancheng.net/linux_tutorial/"
	print(info)

运行结果：

	网站        域名                年龄    价值
	C语言中文网 c.biancheng.net     8       500W
	百度        www.baidu.com       20      500000W
	--------------------
	Python教程：http://c.biancheng.net/python/
	C++教程：http://c.biancheng.net/cplus/
	Linux教程：http://c.biancheng.net/linux_tutorial/

# Python数据类型转换函数大全 #

<br />
<table>
<caption>
表 1 常用数据类型转换函数</caption>
<tbody>
<tr>
<th>
函 数</th>
<th>
作 用</th>
</tr>
<tr>
<td>
int(x)</td>
<td>
将 x 转换成整数类型</td>
</tr>
<tr>
<td>
float(x)</td>
<td>
将 x 转换成浮点数类型</td>
</tr>
<tr>
<td>
complex(real，[,imag])</td>
<td>
创建一个复数</td>
</tr>
<tr>
<td>
str(x)</td>
<td>
将 x 转换为字符串</td>
</tr>
<tr>
<td>
repr(x)</td>
<td>
将 x 转换为表达式字符串</td>
</tr>
<tr>
<td>
eval(str)</td>
<td>
计算在字符串中的有效 Python 表达式，并返回一个对象</td>
</tr>
<tr>
<td>
chr(x)</td>
<td>
将整数 x 转换为一个字符</td>
</tr>
<tr>
<td>
ord(x)</td>
<td>
将一个字符 x 转换为它对应的整数值</td>
</tr>
<tr>
<td>
hex(x)</td>
<td>
将一个整数 x 转换为一个十六进制字符串</td>
</tr>
<tr>
<td>
oct(x)</td>
<td>
将一个整数 x 转换为一个八进制的字符串</td>
</tr>
</tbody>
</table>
<br />

# Python算术运算符及用法详解 #

<br />
<table>
<caption>
表 1 Python 常用算术运算符</caption>
<tbody>
<tr>
<th>
运算符</th>
<th>
说明</th>
<th>
实例</th>
<th>
结果</th>
</tr>
<tr>
<td>
+</td>
<td>
加</td>
<td>
12.45 + 15</td>
<td>
27.45</td>
</tr>
<tr>
<td>
-</td>
<td>
减</td>
<td>
4.56 - 0.26</td>
<td>
4.3</td>
</tr>
<tr>
<td>
*</td>
<td>
乘</td>
<td>
5 * 3.6</td>
<td>
18.0</td>
</tr>
<tr>
<td>
/</td>
<td>
除法（和数学中的规则一样）</td>
<td>
7 / 2</td>
<td>
3.5</td>
</tr>
<tr>
<td>
//</td>
<td>
整除（只保留商的整数部分）</td>
<td>
7 // 2</td>
<td>
3</td>
</tr>
<tr>
<td>
%</td>
<td>
取余，即返回除法的余数</td>
<td>
7 % 2</td>
<td>
1</td>
</tr>
<tr>
<td>
**</td>
<td>
幂运算/次方运算，即返回 x 的 y 次方</td>
<td>
2 ** 4</td>
<td>
16，即 2<sup>4</sup></td>
</tr>
</tbody>
</table>
<br />

# Python赋值运算符 #

## 连续赋值 ##
Python 中的赋值表达式也是有值的，它的值就是被赋的那个值，或者说是左侧变量的值；如果将赋值表达式的值再赋值给另外一个变量，这就构成了连续赋值。请看下面的例子：
a = b = c = 100

=具有右结合性，我们从右到左分析这个表达式：


- c = 100 表示将 100 赋值给 c，所以 c 的值是 100；同时，c 

- = 100 这个子表达式的值也是 100。


- b = c = 100 表示将 c = 100 的值赋给 b，因此 b 的值也是 100。


- 以此类推，a 的值也是 100。

最终结果就是，a、b、c 三个变量的值都是 100。

= 和 ==

= 和 == 是两个不同的运算符，= 用来赋值，而 == 用来判断两边的值是否相等，千万不要混淆。

## 扩展后的赋值运算符 ##

=还可与其他运算符（包括算术运算符、位运算符和逻辑运算符）相结合，扩展成为功能更加强大的赋值运算符，如表 1 所示。扩展后的赋值运算符将使得赋值表达式的书写更加优雅和方便。

<br />
<table>
<caption>
表 1 Python 扩展赋值运算符</caption>
<tbody>
<tr>
<th>
运算符</th>
<th>
说 明</th>
<th>
用法举例</th>
<th>
等价形式</th>
</tr>
<tr>
<td>
=</td>
<td>
最基本的赋值运算</td>
<td>
x = y</td>
<td>
x = y</td>
</tr>
<tr>
<td>
+=</td>
<td>
加赋值</td>
<td>
x += y</td>
<td>
x = x + y</td>
</tr>
<tr>
<td>
-=</td>
<td>
减赋值</td>
<td>
x -= y</td>
<td>
x = x - y</td>
</tr>
<tr>
<td>
*=</td>
<td>
乘赋值</td>
<td>
x *= y</td>
<td>
x = x * y</td>
</tr>
<tr>
<td>
/=</td>
<td>
除赋值</td>
<td>
x /= y</td>
<td>
x = x / y</td>
</tr>
<tr>
<td>
%=</td>
<td>
取余数赋值</td>
<td>
x %= y</td>
<td>
x = x % y</td>
</tr>
<tr>
<td>
**=</td>
<td>
幂赋值</td>
<td>
x **= y</td>
<td>
x = x ** y</td>
</tr>
<tr>
<td>
//=</td>
<td>
取整数赋值</td>
<td>
x //= y</td>
<td>
x = x // y</td>
</tr>
<tr>
<td>
&amp;=</td>
<td>
按位与赋值</td>
<td>
x &amp;= y</td>
<td>
x = x &amp; y</td>
</tr>
<tr>
<td>
|=</td>
<td>
按位或赋值</td>
<td>
x |= y</td>
<td>
x = x | y</td>
</tr>
<tr>
<td>
^=</td>
<td>
按位异或赋值</td>
<td>
x ^= y</td>
<td>
x = x ^ y</td>
</tr>
<tr>
<td>
&lt;&lt;=</td>
<td>
左移赋值</td>
<td>
x &lt;&lt;= y</td>
<td>
x = x &lt;&lt; y，这里的 y 指的是左移的位数</td>
</tr>
<tr>
<td>
&gt;&gt;=</td>
<td>
右移赋值</td>
<td>
x &gt;&gt;= y</td>
<td>
x = x &gt;&gt; y，这里的 y 指的是右移的位数</td>
</tr>
</tbody>
</table>
<br />

# Python比较运算符（关系运算符） #

Python 支持的比较运算符如表 1 所示。

<br />
<table>
<caption>
表 1 Python 比较运算符汇总</caption>
<tbody>
<tr>
<th>
比较运算符</th>
<th>
说明</th>
</tr>
<tr>
<td>
&gt;</td>
<td>
大于，如果<code>&gt;</code>前面的值大于后面的值，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
&lt;</td>
<td>
小于，如果<code>&lt;</code>前面的值小于后面的值，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
==</td>
<td>
等于，如果<code>==</code>两边的值相等，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
&gt;=</td>
<td>
大于等于（等价于数学中的 &ge;），如果<code>&gt;=</code>前面的值大于或者等于后面的值，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
&lt;=</td>
<td>
小于等于（等价于数学中的 &le;），如果<code>&lt;=</code>前面的值小于或者等于后面的值，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
!=</td>
<td>
不等于（等价于数学中的 &ne;），如果<code>!=</code>两边的值不相等，则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
is</td>
<td>
判断两个变量所引用的对象是否相同，如果相同则返回 True，否则返回 False。</td>
</tr>
<tr>
<td>
is not</td>
<td>
判断两个变量所引用的对象是否不相同，如果不相同则返回 True，否则返回 False。</td>
</tr>
</tbody>
</table>
<br />

## == 和 is 的区别 ##
== 用来比较两个变量的值是否相等，而 is 则用来比对两个变量引用的是否是同一个对象，例如：

	import time  #引入time模块
	
	t1 = time.gmtime() # gmtime()用来获取当前时间
	t2 =  time.gmtime()
	
	print(t1 == t2) #输出True
	print(t1 is t2) #输出False

运行结果：
	True
	False

time 模块的 gmtime() 方法用来获取当前的系统时间，精确到秒级，因为程序运行非常快，所以 t1 和 t1 得到的时间是一样的。== 用来判断 t1 和 t2 的值是否相等，所以返回 True。

虽然 t1 和 t2 的值相等，但它们是两个不同的对象（每次调用 gmtime() 都返回不同的对象），所以t1 is t2返回 False。这就好像两个双胞胎姐妹，虽然她们的外貌是一样的，但它们是两个人。

那么，如何判断两个对象是否相同呢？答案是判断两个对象的内存地址。如果内存地址相同，说明两个对象使用的是同一块内存，当然就是同一个对象了；这就像两个名字使用了同一个身体，当然就是同一个人了。

# Python逻辑运算符及其用法 #

 逻辑运算符及功能

<br />
<table>
<caption>
表 1 Python 逻辑运算符及功能</caption>
<tbody>
<tr>
<th width="90">
逻辑运算符</th>
<th>
含义</th>
<th width="90">
基本格式</th>
<th>
说明</th>
</tr>
<tr>
<td>
and</td>
<td>
逻辑与运算，等价于数学中的&ldquo;且&rdquo;</td>
<td>
a and b</td>
<td>
当 a 和 b 两个表达式都为真时，a and b 的结果才为真，否则为假。</td>
</tr>
<tr>
<td>
or</td>
<td>
逻辑或运算，等价于数学中的&ldquo;或&rdquo;</td>
<td>
a or b</td>
<td>
当 a 和 b 两个表达式都为假时，a or b 的结果才是假，否则为真。</td>
</tr>
<tr>
<td>
not</td>
<td>
逻辑非运算，等价于数学中的&ldquo;非&rdquo;</td>
<td>
not a</td>
<td>
如果 a 为真，那么 not a 的结果为假；如果 a 为假，那么 not a 的结果为真。相当于对 a 取反。</td>
</tr>
</tbody>
</table>
<br />


# Python三目运算符（三元运算符）用法详解 #

假设现在有两个数字，我们希望获得其中较大的一个，那么可以使用 if else 语句，例如：


	if a>b:
	    max = a;
	else:
	    max = b;
但是 Python 提供了一种更加简洁的写法，如下所示：

	max = a if a>b else b

这是一种类似于其它编程语言中三目运算符? :的写法。Python 是一种极简主义的编程语言，它没有引入? :这个新的运算符，而是使用已有的 if else 关键字来实现相同的功能。

使用 if else 实现三目运算符（条件运算符）的格式如下：

	exp1 if contion else exp2

condition 是判断条件，exp1 和 exp2 是两个表达式。如果 condition 成立（结果为真），就执行 exp1，并把 exp1 的结果作为整个表达式的结果；如果 condition 不成立（结果为假），就执行 exp2，并把 exp2 的结果作为整个表达式的结果。

前面的语句max = a if a>b else b的含义是：


- 如果 **a>b 成立**，就把 **a**作为整个表达式的值，并赋给变量 max；


- 如果 **a> b 不成立**，就把 **b** 作为整个表达式的值，并赋给变量 max

# Python 运算符优先级 #

<br />
<table>
<caption>
表 1 Python 运算符优先级和结合性一览表</caption>
<tbody>
<tr>
<th>
运算符说明</th>
<th>
Python运算符</th>
<th>
优先级</th>
<th>
结合性</th>
<th>
优先级顺序</th>
</tr>
<tr>
<td>
小括号</td>
<td>
( )</td>
<td>
19</td>
<td>
无</td>
<td colspan="1" rowspan="19">
高<br />
︿<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|<br />
&nbsp;|&nbsp;<br />
&nbsp;|<br />
&nbsp;|<br />
低</td>
</tr>
<tr>
<td>
索引运算符</td>
<td>
x[i] 或 x[i1: i2 [:i3]]</td>
<td>
18</td>
<td>
左</td>
</tr>
<tr>
<td>
属性访问</td>
<td>
x.attribute</td>
<td>
17</td>
<td>
左</td>
</tr>
<tr>
<td>
乘方</td>
<td>
**</td>
<td>
16</td>
<td>
右</td>
</tr>
<tr>
<td>
按位取反</td>
<td>
~</td>
<td>
15</td>
<td>
右</td>
</tr>
<tr>
<td>
符号运算符</td>
<td>
+（正号）、-（负号）</td>
<td>
14</td>
<td>
右</td>
</tr>
<tr>
<td>
乘除</td>
<td>
*、/、//、%</td>
<td>
13</td>
<td>
左</td>
</tr>
<tr>
<td>
加减</td>
<td>
+、-</td>
<td>
12</td>
<td>
左</td>
</tr>
<tr>
<td>
位移</td>
<td>
&gt;&gt;、&lt;&lt;</td>
<td>
11</td>
<td>
左</td>
</tr>
<tr>
<td>
按位与</td>
<td>
&amp;</td>
<td>
10</td>
<td>
右</td>
</tr>
<tr>
<td>
按位异或</td>
<td>
^</td>
<td>
9</td>
<td>
左</td>
</tr>
<tr>
<td>
按位或</td>
<td>
|</td>
<td>
8</td>
<td>
左</td>
</tr>
<tr>
<td>
比较运算符</td>
<td>
==、!=、&gt;、&gt;=、&lt;、&lt;=&nbsp;</td>
<td>
7</td>
<td>
左</td>
</tr>
<tr>
<td>
is 运算符</td>
<td>
is、is not</td>
<td>
6</td>
<td>
左</td>
</tr>
<tr>
<td>
in 运算符</td>
<td>
in、not in</td>
<td>
5</td>
<td>
左</td>
</tr>
<tr>
<td>
逻辑非</td>
<td>
not</td>
<td>
4</td>
<td>
右</td>
</tr>
<tr>
<td>
逻辑与</td>
<td>
and</td>
<td>
3</td>
<td>
左</td>
</tr>
<tr>
<td>
逻辑或</td>
<td>
or</td>
<td>
2</td>
<td>
左</td>
</tr>
<tr>
<td>
逗号运算符</td>
<td>
exp1, exp2</td>
<td>
1</td>
<td>
左</td>
</tr>
</tbody>
</table>
<br />