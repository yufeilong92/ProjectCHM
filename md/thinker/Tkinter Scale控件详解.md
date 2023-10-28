# Tkinter Scale控件详解 #

Scale 控件，即滑块控件或标尺控件，该控件可以创建一个类似于标尺式的滑动条对象，用户通过操作它可以直接设置相应的数值（刻度值)。

Scale 控件同样有许多应用场景，并且在我们日常工作中也会经常用到，比如电脑上调节音量的滑动条（数值范围 0-100），如下图所示：

![1](http://c.biancheng.net/uploads/allimg/220105/11123J549-0.gif)

Scale 控件常用的基本属性如下所示：

<br />
<table border="1">
<tbody>
<tr>
<th>
参数</th>
<th>
说明</th>
</tr>
<tr>
<td>
activebackground</td>
<td>
指定当鼠标在上方飘过的时候滑块的背景颜色</td>
</tr>
<tr>
<td>
bigincrement</td>
<td>
1. 设置&ldquo;大&rdquo;增长量<br />
2. 该选项设置增长量的大小<br />
3. 默认值是 0，增长量为范围的 1/10</td>
</tr>
<tr>
<td>
borderwidth</td>
<td>
1. 指定边框宽度<br />
2. 默认值是 2</td>
</tr>
<tr>
<td>
command</td>
<td>
1. 指定一个函数，每当滑块发生改变的时候都会自动调用该函数<br />
2. 该函数有一个唯一的参数，就是最新的滑块位置<br />
3. 如果滑块快速地移动，函数可能无法获得每一个位置，但一定会获得滑块停下时的最终位置</td>
</tr>
<tr>
<td>
digits</td>
<td>
1. 设置最多显示多少位数字<br />
2. 补充注释：例如设置 from 选项为 0，to 选项为 20，digits 选项设置为 5，那么滑块的范围就是在 0.000 ~ 20.000 直接滑动<br />
3. 默认值是 0（不开启）</td>
</tr>
<tr>
<td>
font</td>
<td>
1. 指定滑块左侧的 Label 和刻度的文字字体<br />
2. 默认值由系统指定</td>
</tr>
<tr>
<td>
from_</td>
<td>
1. 设置滑块最顶（左）端的位置<br />
2. 默认值是 0</td>
</tr>
<tr>
<td>
highlightcolor</td>
<td>
1. 指定当 Scale 获得焦点的时候高亮边框的颜色<br />
2. 默认值由系统指定</td>
</tr>
<tr>
<td>
label</td>
<td>
1. 你可以在垂直的 Scale 组件的顶端右侧（水平的话是左端上方）显示一个文本标签<br />
2. 默认值是不显示标签</td>
</tr>
<tr>
<td>
length</td>
<td>
1. Scale 组件的长度，默认值是 100 像素</td>
</tr>
<tr>
<td>
orient</td>
<td>
1. 设置&nbsp;Scale 控件是水平放置（HORIZONTAL）还是垂直放置（VERTICAL）<br />
2. 默认值是 VERTICAL（垂直放置）</td>
</tr>
<tr>
<td>
repeatdelay</td>
<td>
1. 该选项指定鼠标左键点击滚动条凹槽的响应时间<br />
2. 默认值是 300（毫秒）</td>
</tr>
<tr>
<td>
repeatinterval</td>
<td>
1. 该选项指定鼠标左键紧按滚动条凹槽时的响应间隔<br />
2. 默认值是 100（毫秒）</td>
</tr>
<tr>
<td>
resolution</td>
<td>
1. 指定 Scale 组件的分辨率（每点击一下移动的步长）<br />
示例： 比如 resolution 选项设置为 0.1 的话，那么每点击一下鼠标就是在 0.0 ~ 20.0 之间以 0.1 的步长移动<br />
2. 该参数的默认值是 1</td>
</tr>
<tr>
<td>
showvalue</td>
<td>
1. 设置是否显示滑块旁边的数字<br />
2. 默认值为 True</td>
</tr>
<tr>
<td>
sliderlength</td>
<td>
1. 设置滑块的长度<br />
2. 默认值是 30 像素</td>
</tr>
<tr>
<td>
state</td>
<td>
1. 默认情况下 Scale 组件支持鼠标事件和键盘事件，可以通过设置该选项为 DISABLED 来禁用此功能<br />
2. 默认值是 NORMAL</td>
</tr>
<tr>
<td>
takefocus</td>
<td>
1. 指定使用 Tab 键是否可以将焦点移动到该 Scale 组件上<br />
2. 默认是开启的，可以通过将该选项设置为 False 避免焦点落在此组件上</td>
</tr>
<tr>
<td>
tickinterval</td>
<td>
1. 设置显示的刻度，如果设置一个值，那么就会按照该值的倍数显示刻度<br />
2. 默认值是不显示刻度</td>
</tr>
<tr>
<td>
to</td>
<td>
1. 设置滑块最底（右）端的位置<br />
2. 默认值是 100</td>
</tr>
<tr>
<td>
troughcolor</td>
<td>
1. 设置凹槽的颜色<br />
2. 默认值由系统指定</td>
</tr>
<tr>
<td>
variable</td>
<td>
1. 指定一个与 Scale 组件相关联的 Tkinter 变量，该变量存放滑块最新的位置<br />
2. 当滑块移动的时候，该变量的值也会发生相应的变化</td>
</tr>
<tr>
<td>
width</td>
<td>
1. 指定 Scale 组件的宽度<br />
2. 默认值是 15 像素</td>
</tr>
</tbody>
</table>
<br />
Scale 常用方法有如下四个，见下表所示：<br />
<br />
<table>
<tbody>
<tr>
<th>
方法</th>
<th>
说明</th>
</tr>
<tr>
<td>
coords(value=None)</td>
<td>
1. 获得当前滑块位置相对于&nbsp;Scale 控件左上角位置的相对坐标，<br />
2. 如果设置了 value 值，则返回当滑块位于该位置时与左上角的相对坐标</td>
</tr>
<tr>
<td>
get()</td>
<td>
获得当前滑块的位置（即当前数值），返回值可以为整型或者浮点型</td>
</tr>
<tr>
<td>
identify(x, y)</td>
<td>
返回一个字符串表示指定位置下的 Scale 控件</td>
</tr>
<tr>
<td>
set(value)</td>
<td>
设置 Scale 控件的值，即滑块的位置，默认为初始位置</td>
</tr>
</tbody>
</table>
<br />

创建一个 Scale 控件：

	from tkinter import *
	# 创建主窗口
	win =Tk()
	win.title("控制管理界面")
	win.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	win.geometry('400x250')
	# 添加一个 Scale 控件，默认垂直方向，步长设置为 5，长度为200，滑动块的大小为 50，最后使用label参数文本
	s=Scale(win, from_ =100, to =0,resolution =5,length =200,sliderlength= 20,label ='音量控制' )
	s.pack()
	# 设置滑块的位置
	s.set(value=15)
	# 显示窗口
	mainloop()

程序运行结果如下：

![1](http://c.biancheng.net/uploads/allimg/220105/11123J096-1.gif)

下面看一个稍微复杂点的应用示例，代码如下：

	import tkinter as tk
	
	window = tk.Tk()
	window.title("购物车界面")
	window.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	window.geometry('450x200+450+250')
	window.resizable(0,0)
	# 创建一个文本标签
	label = tk.Label(window, bg='#9FB6CD',width=18, text='')
	label.grid(row =2)
	# 创建执行函数
	def select_price(value):
	    label.config(text='您购买的数量是 ' + value)
	# 创建 Scale控件
	scale = tk.Scale(window,
	             label='选择您要购买的数量',
	             from_=1,
	             to= 100,
	             orient=tk.HORIZONTAL,   # 设置Scale控件平方向显示
	             length=400,
	             tickinterval=9,       # 设置刻度滑动条的间隔
	             command=select_price)  # 调用执行函数，是数值显示在 Label控件中
	scale.grid(row =1)
	
	# 显示窗口
	window.mainloop()

程序运行结果如下：

![1](http://c.biancheng.net/uploads/allimg/220105/11123KY8-2.gif)