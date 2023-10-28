# Tkinter Event事件处理 #

事件处理，是 GUI 程序中不可或缺的重要组成部分，相比来说，控件只是组成一台机器的零部件， 而事件处理则是驱动这台机器“正常”运转的关键所在，它能够将零部件之间“优雅”的贯穿起来，因此“事件处理”可谓是 GUI 程序的“灵魂”，同时它也是实现人机交互的关键。
> 对于“事件”这一名词，在讲解控件时也偶尔提及过，在本节我们将对 Tkinter 中的事件处理机制做更为详细的介绍。

在一款 GUI 程序中，我们将用户对软件的操作统称为“事件”，比如鼠标点击按钮、键盘输入文本以及窗口管理器触发的重绘事件等，这些事件有一个共同的特点，即都是由用户直接或者间接触发的。

## 事件绑定方法 ##

Tkinter 提供的事件处理机制允许我们为“控件”绑定相应的事件和事件处理函数（即 callback函数），从而实现控件与用户的交互，其语法格式如下：

    widget.bind("<event>",func)
上述语法中，widget 代表控件的实例对象，之后，采用 bind() 方法进行事件绑定，该函数有两个参数：


- <event>：一个字符串参数，表示事件的类型，并使用“尖括号”的形式进行包裹；


- func：表示事件的处理函数（callback，即回调函数），当触发事件时，Tk 会携带事件对象（Event）去调用 func 方法。

注意：bind() 方法可以完成事件与处理函数绑定，而使用 unbind() 方法可以将事件与处理函数解绑。

## 常用事件类型 ##

事件类型（也称事件码）是 Tkinter 模块规定的，主要包括鼠标、键盘、光标等相关事件，Tkinter 为其规定了相应的语法格式：

    <modifier-type-detail>

上述语法由三部分组成，说明如下：


- <>：事件类型必须包含在“尖括号”内；


- modifier：可选项，事件类型的修饰符，通常用于描述组合键、双击<Double-

- Button-1>、大写锁定键<Lock>以及<Alt-Shift>等；


- type：是必不可少的一项，表示事件的具体类型；


- detail：可选项，通常用于描述具体的哪个按键，比如 <Button-1> 表示鼠标左键；

这里有必要对经常使用的 modifier 修饰符做简单的介绍，修饰符可以修改事件的激活条件，比如双击鼠标或者需要同时按下某个键才触发事件，常用的修饰符如下
<br />
<table>
<tbody>
<tr>
<th>
修饰符</th>
<th>
说明</th>
</tr>
<tr>
<td>
Control</td>
<td>
事件发生时需按下 Control 键</td>
</tr>
<tr>
<td>
Alt</td>
<td>
事件发生时需按下 Alt 键</td>
</tr>
<tr>
<td>
Shift</td>
<td>
事件发生时需按下 Shift 键</td>
</tr>
<tr>
<td>
Lock</td>
<td>
事件发生时需处于大写锁定状态</td>
</tr>
<tr>
<td>
Double</td>
<td>
事件连续发生两次，比如双击鼠标</td>
</tr>
<tr>
<td>
Triple</td>
<td>
事件连续发生三次</td>
</tr>
<tr>
<td>
Quadruple</td>
<td>
事件连续发生四次</td>
</tr>
</tbody>
</table>
<br />
下述表格中介绍了 Tkinter 中经常使用的事件类型，如下所示：<br />
<br />
<table>
<tbody>
<tr>
<th>
事件码</th>
<th>
说明</th>
</tr>
<tr>
<td>
&lt;ButtonPress-1&gt;</td>
<td>
单击鼠标左键，简写为&lt;Button-1&gt;，后面的数字可以是1/2/3，分别代表左键、中间滑轮、右键</td>
</tr>
<tr>
<td>
&lt;ButtonRelease-1&gt;</td>
<td>
释放鼠标左键，后面数字可以是1/2/3，分别代表释放左键、滑轮、右键</td>
</tr>
<tr>
<td>
&lt;B1-Motion&gt;</td>
<td>
按住鼠标左键移动，&lt;B2-Motion&gt;和&lt;B3-Motion&gt;分别表示按住鼠标滑轮移动、右键移动</td>
</tr>
<tr>
<td>
&lt;MouseWheel&gt;</td>
<td>
转动鼠标滑轮</td>
</tr>
<tr>
<td>
&lt;Double-Button-1&gt;</td>
<td>
双击鼠标左键</td>
</tr>
<tr>
<td>
&lt;Enter&gt;</td>
<td>
鼠标光标进入控件实例</td>
</tr>
<tr>
<td>
&lt;Leave&gt;</td>
<td>
鼠标光标离开控件实例</td>
</tr>
<tr>
<td>
&lt;Key&gt;</td>
<td>
按下键盘上的任意键</td>
</tr>
<tr>
<td>
&lt;KeyPress-字母&gt;/&lt;KeyPress-数字&gt;</td>
<td>
按下键盘上的某一个字母或者数字键</td>
</tr>
<tr>
<td>
&lt;KeyRelease&gt;</td>
<td>
释放键盘上的按键</td>
</tr>
<tr>
<td>
&lt;Return&gt;</td>
<td>
回车键，其他同类型键有&lt;Shift&gt;/&lt;Tab&gt;/&lt;Control&gt;/&lt;Alt&gt;</td>
</tr>
<tr>
<td>
&lt;Space&gt;</td>
<td>
空格键</td>
</tr>
<tr>
<td>
&lt;UP&gt;/&lt;Down&gt;/&lt;Left&gt;/&lt;Right&gt;</td>
<td>
方向键</td>
</tr>
<tr>
<td>
&lt;F1&gt;...&lt;F12&gt;</td>
<td>
常用的功能键</td>
</tr>
<tr>
<td>
&lt;Control-Alt&gt;</td>
<td>
组合键，再比如&lt;Control-Shift-KeyPress-T&gt;，表示用户同时点击 Ctrl + Shift + T</td>
</tr>
<tr>
<td>
&lt;FocusIn&gt;</td>
<td>
当控件获取焦点时候触发，比如鼠标点击输入控件输入内容，可以调用 focus_set() 方法使控件获得焦点</td>
</tr>
<tr>
<td>
&lt;FocusOut&gt;</td>
<td>
当控件失去焦点时激活，比如当鼠标离开输入框的时候</td>
</tr>
<tr>
<td>
&lt;Configure&nbsp;&gt;</td>
<td>
控件的发生改变的时候触发事件，比如调整了控件的大小等</td>
</tr>
<tr>
<td>
&lt;Deactivate&gt;</td>
<td>
当控件的状态从&ldquo;激活&rdquo;变为&ldquo;未激活&rdquo;时触发事件</td>
</tr>
<tr>
<td>
&lt;Destroy&gt;</td>
<td>
当控件被销毁的时候触发执行事件的函数</td>
</tr>
<tr>
<td>
&lt;Expose&gt;</td>
<td>
当窗口或组件的某部分不再被覆盖的时候触发事件</td>
</tr>
<tr>
<td>
&lt;Visibility&gt;</td>
<td>
当应用程序至少有一部分在屏幕中是可见状态时触发事件</td>
</tr>
</tbody>
</table>
<h2>
Event事件对象</h2>
当事件触发后，Tkinter 会自动将事件对象交给回调函数进行下步的处理，Event 对象包含了以下常用属性：<br />
<br />
<table>
<tbody>
<tr>
<th>
属性</th>
<th>
说明</th>
</tr>
<tr>
<td>
widget</td>
<td>
发生事件的是哪一个控件</td>
</tr>
<tr>
<td>
x,y</td>
<td>
相对于窗口的左上角而言，当前鼠标的坐标位置</td>
</tr>
<tr>
<td>
x_root,y_root</td>
<td>
相对于屏幕的左上角而言，当前鼠标的坐标位置</td>
</tr>
<tr>
<td>
char</td>
<td>
用来显示所按键相对应的字符</td>
</tr>
<tr>
<td>
keysym</td>
<td>
按键名，比如 Control_L 表示左边的 Ctrl 按键</td>
</tr>
<tr>
<td>
keycode</td>
<td>
按键码，一个按键的数字编号，比如 Delete 按键码是107</td>
</tr>
<tr>
<td>
num</td>
<td>
1/2/3中的一个，表示点击了鼠标的哪个按键，按键分为左、中、右</td>
</tr>
<tr>
<td>
width,height</td>
<td>
控件的修改后的尺寸，对应着 &lt;Configure&gt;事件</td>
</tr>
<tr>
<td>
type</td>
<td>
事件类型</td>
</tr>
</tbody>
</table>
<br />

下面看一组关于“键盘事件”的使用示例：

	from tkinter import *
	# 定义事件函数，必须用event参数
	def show_key(event):
	    # 查看触发事件的按钮
	    s=event.keysym
	    # 将其显示在按钮控件上
	    lb.config(text=s)
	
	root=Tk()
	root.config(bg='#87CEEB')
	root.title("C语言中文网")
	root.geometry('450x350+300+200')
	root.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	# 添加一个按钮控件
	lb=Label(root,text='请按键',fg='blue',font=('微软雅黑',15))
	# 给按钮控件绑定事件，按下任意键，然后调用事件处理函数。注意，此处需要在英文状态下进行输入
	lb.bind('<Key>',show_key)
	# 设置按钮获取焦点
	lb.focus_set()
	lb.pack()
	# 显示窗口
	root.mainloop()

程序运行结果如下：

![1](http://c.biancheng.net/uploads/allimg/220105/113R05F1-0.gif)

> 注意：在上述示例中，只有当 Label 控件获取焦点后才能接收键盘事件，因此在给控件绑定事件和回调函数后，需要使用 focus_set() 方法来获取焦点。

下面再看一组关于“鼠标事件”的相关示例：

	# 定义事件函数
	from tkinter import *
	
	def handleMotion(event):
	    lb1['text'] = '你移动了光标的所在位置'
	    lb2['text'] = '目前光标位置：x ='+ str(event.x)+';y='+str(event.y)
	    print('光标当前位置',event.x,event.y)
	
	# 创建主窗口
	win = Tk()
	win.config(bg='#87CEEB')
	win.title("C语言中文网")
	win.geometry('450x350+300+200')
	win.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
	# 创建一个窗体容器frame
	frame = Frame (win, relief=RAISED, borderwidth=2, width=300,height=200)
	frame.bind('<Motion>',handleMotion)
	lb1 = Label(frame,text='没有任何事件触发', bg='purple', )
	# 使用place进行位置布局，下一节会介绍
	lb1.place (x=20,y=20)
	lb2 = Label(frame,text='')
	lb2.place (x=16,y=60)
	frame.pack(side=TOP)
	# 显示窗口
	win.mainloop()

程序运行结果如下:


![1](http://c.biancheng.net/uploads/allimg/220105/113R0D29-1.gif)

