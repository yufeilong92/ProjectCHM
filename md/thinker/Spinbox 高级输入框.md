# Spinbox 高级输入框 #
<table><thead><tr><th align="left">属性参数</th><th align="left">描述</th></tr></thead><tbody><tr><td align="left">activebackground</td><td align="left">设置当Spinbox处于ACTIVE状态下的背景颜色</td></tr><tr><td align="left">borderwidth<br />bd</td><td align="left">设置边框宽度。默认值是1或2像素</td></tr><tr><td align="left">buttonbackground</td><td align="left">设置调节箭头的背景颜色</td></tr><tr><td align="left">buttoncursor</td><td align="left">指定当鼠标在调节箭头上方的鼠标样式</td></tr><tr><td align="left">buttondownrelief</td><td align="left">指定向下调节箭头的样式<br />默认值是RAISED<br />还可以设置为FLAT&#xff0c;SUNKEN&#xff0c;GROOVE和RIDGE</td></tr><tr><td align="left">buttonuprelief</td><td align="left">指定向上调节箭头的样式<br />默认值是RAISED<br />还可以设置为FLAT&#xff0c;SUNKEN&#xff0c;GROOVE和RIDGE</td></tr><tr><td align="left">command</td><td align="left">指定一个函数&#xff0c;当用户点击调节箭头的时候将自动调用该函数<br />注意&#xff1a;当用户直接在输入框中输入数据时并不会触发该函数</td></tr><tr><td align="left">cursor</td><td align="left">指定当鼠标在Spinbox上面的时候鼠标样式。默认值由系统指定</td></tr><tr><td align="left">disabledbackground</td><td align="left">设置当Spinbox处于DISABLED状态下的背景颜色</td></tr><tr><td align="left">disabledforeground</td><td align="left">设置当Spinbox处于DISABLED状态下的前景颜色</td></tr><tr><td align="left">exportselection</td><td align="left">指定选中的文本是否可以被自动复制到剪贴板<br />默认值是True<br />可以修改为False表示不会自动复制文本到剪贴板</td></tr><tr><td align="left">font</td><td align="left">指定Spinbox中文本的字体<br />默认值由系统指定</td></tr><tr><td align="left">foreground<br />fg</td><td align="left">设置前景&#xff08;文本&#xff09;颜色<br />默认值由系统指定</td></tr><tr><td align="left">format</td><td align="left">使用该选项设置选择数值的样式&#xff08;from_和to指定范围&#xff0c;用户自行输入的不算&#xff09;例如使用format&#61;&#39;%10.4f’表示显示的数值占10位&#xff0c;小数点后保留4位</td></tr><tr><td align="left">from_</td><td align="left">该选项和to选项共同指定一个范围内的数值</td></tr><tr><td align="left">highlightbackground</td><td align="left">指定当Spinbox没有获得焦点的时候高亮边框的颜色<br />默认值由系统指定&#xff0c;通常是标准背景颜色</td></tr><tr><td align="left">highlightcolor</td><td align="left">指定当Spinbox获得焦点的时候高亮边框的颜色<br />默认值由系统指定</td></tr><tr><td align="left">highlightthickness</td><td align="left">指定高亮边框的宽度<br />increment 该选项指定当用户每次点击调节箭头的时候递增递减的精度<br />例如from_&#61;1, to&#61;10, increment&#61;0.5&#xff0c;那么每次用户点击调节箭头的时候&#xff0c;输入框中的数字递增递减0.5</td></tr><tr><td align="left">insertbackground</td><td align="left">指定输入光标的颜色</td></tr><tr><td align="left">insertborderwidth</td><td align="left">指定输入光标的边框高度<br />如果被设置为非0值&#xff0c;光标样式会被设置为RAISED<br />提示&#xff1a;将insertborderwidth设置的大一点才能看到效果</td></tr><tr><td align="left">insertofftime</td><td align="left">该选项控制光标的闪烁频率&#xff08;灭&#xff09;。单位是毫秒</td></tr><tr><td align="left">insertontime</td><td align="left">该选项控制光标的闪烁频率&#xff08;亮&#xff09;。单位是毫秒</td></tr><tr><td align="left">insertwidth</td><td align="left">指定光标的宽度。默认值是1或2像素</td></tr><tr><td align="left">invalidcommand<br />invcmd</td><td align="left">指定当输入框的内容“非法”时调用的函数<br />也就是指定当validateCommand选项指定的函数返回False时的函数<br />详见Entry组件</td></tr><tr><td align="left">justify</td><td align="left">定义如何对齐多行文本。使用LEFT&#xff0c;RIGHT或CENTER。默认值是ENTER</td></tr><tr><td align="left">readonlybackground</td><td align="left">设置当Spinbox处于“readonly”状态下的背景颜色</td></tr><tr><td align="left">relief</td><td align="left">指定边框样式<br />默认值是FLAT<br />另外你还可以设置SUNKEN&#xff0c;RAISED&#xff0c;GROOVE或RIDGE</td></tr><tr><td align="left">repeatdelay</td><td align="left">该选项指定鼠标左键点击上下箭头并保持&#xff0c;到输入框数值开始连续调整的延迟时间。默认值是300&#xff08;毫秒&#xff09;</td></tr><tr><td align="left">repeatinterval</td><td align="left">该选项指定鼠标左键紧按滚动条凹槽的响应间隔。默认值是100&#xff08;毫秒&#xff09;</td></tr><tr><td align="left">selectbackground</td><td align="left">指定输入框的文本被选中时的背景颜色<br />默认值由系统指定</td></tr><tr><td align="left">selectborderwidth</td><td align="left">指定输入框的文本被选中时的边框宽度</td></tr><tr><td align="left">selectforeground</td><td align="left">指定输入框的文本被选中时的文本颜色</td></tr><tr><td align="left">state</td><td align="left">Spinbox组件可以设置的状态&#xff1a;NORMAL&#xff0c;DISABLED或“readonly”&#xff08;注意&#xff0c;这个是字符串。它跟DISABLED相似&#xff0c;但他支持选中和拷贝&#xff0c;只是不能修改&#xff0c;而DISABLED是完全禁止&#xff09;<br />默认值是NORMAL<br />注意&#xff0c;如果此选项设置为DISABLED或”readonly”&#xff0c;那么调用insert()和delete()方法都会被忽略</td></tr><tr><td align="left">takefocus</td><td align="left">指定使用Tab键可以将焦点移动到输入框中<br />默认是开启的&#xff0c;可以将该选项设置为False避免焦点在此输入框中</td></tr><tr><td align="left">textvariable</td><td align="left">指定一个与输入框内容相关联的tkinter变量&#xff08;通常是StringVar&#xff09;<br />当输入框的内容发生改变时&#xff0c;该变量的值也会相应发生改变</td></tr><tr><td align="left">to</td><td align="left">该选项和from_选项共同指定一个范围的数值<br />increment选项设置每次点击调节箭头递增递减的精度</td></tr><tr><td align="left">validate</td><td align="left">该选项设置是否启用内容验证</td></tr><tr><td align="left">validatecommand<br />vcmd</td><td align="left">该选项指定一个验证函数&#xff0c;用于验证输入框内容是否合法<br />验证函数需要返回True或False表示验证结果<br />注意&#xff0c;该选项只有当validate的值非’none’时才有效</td></tr><tr><td align="left">values</td><td align="left">提供两个方法限定用户输入的内容&#xff0c;一种是通过from_和to选项设置范围&#xff0c;另一种则是将可选值以元组的形式赋给values选项<br />例如values&#61;(“ds”, “sad”, “aesf”)则允许用户在这四个字符串中选择</td></tr><tr><td align="left">width</td><td align="left">设置输入框的宽度&#xff0c;以字符为单位<br />默认值是20。对于变宽字体来说&#xff0c;组件的实际宽度等于字体的平均宽度乘以width选项的值</td></tr><tr><td align="left">wrap</td><td align="left">默认情况下&#xff08;False&#xff09;&#xff0c;当输入框中的值是第一个&#xff08;最后一个&#xff09;的时候&#xff0c;再点击向上&#xff08;向下&#xff09;调节箭头&#xff0c;内容不会改变。<br />当该选项的值设置为True&#xff0c;则当输入框中的值是第一个&#xff08;最后一个&#xff09;的时候&#xff0c;再点击向上&#xff08;向下&#xff09;调节箭头&#xff0c;内容将回到最后一个&#xff08;第一个&#xff09;。<br />提示&#xff1a;其实就是开启循环的意思</td></tr><tr><td align="left">xscrollcommand</td><td align="left">与scrollbar&#xff08;滚动条&#xff09;组件相关联<br />如果你觉得用户输入的内容会超过该组件的输入框宽度&#xff0c;那么可以考虑设置该选项</td></tr><tr><td align="left"><strong>13.1.1 activebackground</strong></td><td align="left"></td></tr><tr><td align="left">鼠标经过Spinbox的背景颜色。不过无效。</td><td align="left"></td></tr><tr><td align="left"><strong>13.1.2 background(bg)</strong></td><td align="left"></td></tr><tr><td align="left">设置Spinbox的背景颜色。</td><td align="left"></td></tr></tbody></table> 



	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,bg='red')
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/20190912224735417.png)
## borderwidth(bd) ##
设置Spinbox的边框。

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,bd=20)
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/20190912224823393.png)

## 1.4 buttonbackground ##
设置上下箭头的背景颜色

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,buttonbackground='blue')
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/20190912224849803.png)

## 1.5 buttoncursor ##
设置鼠标位于上下按键上方时，鼠标的形状

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,buttoncursor='spider')
	b1.pack()
	root.mainloop()

## 1.6 buttondownrelief 和buttonuprelief ##
设置上下按键的3D效果。不过在我的windows系统中不起作用

## 1.7 command ##
上下按钮的回调函数。在输入框中的内容发生变化时，不是触发该函数

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	def updown(*args):
	    print(b1.get())
	b1=tk.Spinbox(root,command=updown,from_=0,to=10)
	b1.pack()
	root.mainloop()

## 1.8 cursor ##
鼠标在Spinbox中输入框上面时候的光标形状。

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,cursor='spider')
	b1.pack()
	root.mainloop()

## 1.9 disabledbackground 和disabledforeground ##
Spinbox的状态为DISABLED状态时候的背景和前景颜色

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	b1=tk.Spinbox(root,from_=10,to=20,
	              disabledforeground='red',
	              state=tk.DISABLED,
	              disabledbackground ='blue')
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/20190912225012413.png)

## 1.11 foreground(fg) ##
指定Spinbox的文本和上下箭头颜色。

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,from_=10,to=20,fg='red')
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/2019091222510511.png)

## 1.12 format ##
格式化Spinbox控件中输入框的内容。比如format=’%4.2f’就表示数字显示长度为4，其中小数部分占2位。

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,from_=10,to=20,format='%4.2f')
	b1.pack()
	root.mainloop()

说明：如果不设置format，正常的显示是没有小数部分的。设置了format，会根据设置的格式显示数值

## .1.13 highlightbackground，highlightcolor和highlightthickness ##
设置Spinbox失去输入焦点和获得输入焦点时候的边框，此边框的宽度由highlightthickness设置

## 1.14 increment ##
定义Spinbox每次调整的步长。比如increment=0.3，表示每次增加或者减少0.3的数值。

	import tkinter as tk
	root=tk.Tk()
	root.geometry('300x240')
	
	b1=tk.Spinbox(root,from_=10,to=20,increment='0.3')
	b1.pack()
	root.mainloop()

![](https://img-blog.csdnimg.cn/20190912225155596.png)







Spinbox 是 Entry 控件的升级版，它是 Tkinter 8.4 版本后新增的控件，该控件不仅允许用户直接输入内容，还支持用户使用微调选择器（即上下按钮调节器）来输入内容。

	import tkinter as tk
	
	root = tk.Tk()
	root.title("C语言中文网")
	root.geometry('300x200+300+300')
	root.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	# 如果是数字使用 from_和to参数，范围 0-20,并且与2步长递增或递减
	w = tk.Spinbox(root,from_=0,to=20, increment=2,width = 15,bg='#9BCD9B')
	w.pack()
	# 显示窗口
	root.mainloop()

程序运行结果：

![结果](http://c.biancheng.net/uploads/allimg/220105/110G51039-5.gif)

若不是数字，而是字符串形式的选项值，则采用values参数以元组的形式进行传参，如下所示：

	import tkinter as tk
	
	root = tk.Tk()
	root.title("C语言中文网")
	root.geometry('300x200+300+300')
	root.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	# 使用 values 参数以元组的形式进行传参
	strings = tk.Spinbox(root,values=('Python','java','C语言','PHP'))
	strings.pack()
	# 开启事件循环
	root.mainloop()

程序运行结果：

![结果](http://c.biancheng.net/uploads/allimg/220105/110G5O56-6.gif)