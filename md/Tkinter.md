# tkinter #
tkinter(Tk interface)是Python的标准GUl库，支持跨平台的GUl程序开发。tkinter适合小型的GUl程序编写，也特别适合初学者学习GUl编程。
# [官网](https://docs.python.org/3/library/tkinter.html "官网") #

## 使用 ##
	pip install tk    
	from tkinter import *

#主窗口

<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">函数</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>

    <tr style="background-color: aqua;">
		<td>window.title("my title")</td>
		<td>接受一个字符串参数，为窗口起一个标题。</td>
	</tr>

	<tr style="background-color: aquamarine;">
		<td>window.resizable()</td>
		<td>是否允许用户拉伸主窗口大小，默认为可更改，当设置为 resizable(0,0)或者resizable(False,False)时不可更改。</td>
	</tr>


    <tr style="background-color: aqua;">
		<td>window.geometry()</td>
		<td>设定主窗口的大小以及位置，当参数值为 None 时表示获取窗口的大小和位置信息。。</td>
	</tr>

	<tr style="background-color: aquamarine;">
		<td>window.quit()</td>
		<td>关闭当前窗口。</td>
	</tr>


    <tr style="background-color: aqua;">
		<td>window.update()</td>
		<td>刷新当前窗口。</td>
	</tr>

	<tr style="background-color: aquamarine;">
		<td>window.mainloop()</td>
		<td>设置窗口主循环，使窗口循环显示（一直显示，指导窗口被关闭）</td>
	</tr>

    <tr style="background-color: aqua;">
		<td>window.iconbitmap()</td>
		<td>设置窗口左上角的图标（图标是.ico文件类型）</td>
	</tr>

		<tr style="background-color: aquamarine;">
		<td>window.config(background ="red")</td>
		<td>设置窗口的背景色为红色，也可以接受 16 进制的颜色值</td>
	</tr>

    	<tr style="background-color: aqua;">
		<td>window.minsize(50,50)</td>
		<td>设置窗口被允许调整的最小范围，即宽和高各50/td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>window.maxsize(400,400)</td>
		<td>设置窗口被允许调整的最大范围，即宽和高各400</td>
	</tr>

    <tr style="background-color: aqua;">
		<td>window.attributes("-alpha",0.5)	</td>
		<td>用来设置窗口的一些属性，比如透明度（-alpha）、是否置顶（-topmost）即将主屏置于其他图标之上、是否全屏（-fullscreen）全屏显示等</td>
	</tr>

		<tr style="background-color: aquamarine;">
		<td>window.state("normal")</td>
		<td>用来设置窗口的显示状态，参数值 normal（正常显示），icon（最小化），zoomed（最大化）</td>
	</tr>

   	 <tr style="background-color: aqua;">
		<td>window.withdraw()</td>
		<td>用来隐藏主窗口，但不会销毁窗口。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>window.iconify()</td>
		<td>设置窗口最小化</td>
	</tr>

    <tr style="background-color: aqua;">
		<td>window.deiconify()</td>
		<td>将窗口从隐藏状态还原</td>
	</tr>

		<tr style="background-color: aquamarine;">
		<td>window.winfo_screenwidth()
window.winfo_screenheight()</td>
		<td>获取电脑屏幕的分辨率（尺寸）</td>
	</tr>

   	<tr style="background-color: aqua;">
		<td>window.winfo_width()
window.winfo_height() </td>
		<td>获取窗口的大小，同样也适用于其他控件，但是使用前需要使用 window.update() 刷新屏幕，否则返回值为1</td>
	</tr>
    

    	<tr style="background-color: aquamarine;">
        	<td>window.protocol("协议名",回调函数)</td>
 			<td>启用协议处理机制，常用协议有 WN_DELETE_WINDOW，当用户点击关闭窗口时，窗口不会关闭，而是触发回调函数。</td>
		</tr>
	 <tr style="background-color: aqua;">
        	<td>xxx</td>
 			<td>xxx</td>
		</tr>

    	<tr style="background-color: aquamarine;">
        	<td>xxx</td>
 			<td>xxx</td>
		</tr>
	 <tr style="background-color: aqua;">
        	<td>xxx</td>
 			<td>xxx</td>
		</tr>

</table>


    import tkinter as tk
    window =tk.Tk()
    #设置窗口title
    window.title('C语言中文网')
    #设置窗口大小:宽x高,注,此处不能为 "*",必须使用 "x"
    window.geometry('450x300')
    # 获取电脑屏幕的大小
    print("电脑的分辨率是%dx%d"%(window.winfo_screenwidth(),window.winfo_screenheight()))
    # 要求窗口的大小，必须先刷新一下屏幕
    window.update()
    print("窗口的分辨率是%dx%d"%(window.winfo_width(),window.winfo_height()))
    # 如使用该函数则窗口不能被拉伸
    # window.resizable(0,0)
    # 改变背景颜色
    window.config(background="#6fb765")
    # 设置窗口处于顶层
    window.attributes('-topmost',True)
    # 设置窗口的透明度
    window.attributes('-alpha',1)
    # 设置窗口被允许最大调整的范围，与resizble()冲突
    window.maxsize(600,600)
    # 设置窗口被允许最小调整的范围，与resizble()冲突
    window.minsize(50,50)
    #更改左上角窗口的的icon图标,加载C语言中文网logo标
    window.iconbitmap('C:/Users/Administrator/Desktop/favicon.ico')
    #添加文本内容,并对字体添加相应的格式 font(字体,字号,"字体类型")
    text=tk.Label(window,text="C语言中文网，网址：c.biancheng.net",bg="yellow",fg="red",font=('Times', 15, 'bold italic underline'))
    #将文本内容放置在主窗口内
    text.pack()
    # 添加按钮，以及按钮的文本，并通过command 参数设置关闭窗口的功能
    button=tk.Button(window,text="关闭",command=window.quit)
    # 将按钮放置在主窗口内
    button.pack(side="bottom")
    #进入主循环，显示主窗口
    window.mainloop()

#窗口关闭监听
    from tkinter import Tk
    # 导入 对话框控件
    from tkinter import messagebox
    # 创建主窗口
    root = Tk()
    # 定义回调函数，当用户点击窗口x退出时，执行用户自定义的函数
    def QueryWindow():
    # 显示一个警告信息，点击确后，销毁窗口
    if messagebox.showwarning("警告","出现了一个错误"):
    # 这里必须使用 destory()关闭窗口
    root.destroy()
    # 使用协议机制与窗口交互，并回调用户自定义的函数
    root.protocol('WM_DELETE_WINDOW', QueryWindow)
    root.mainloop()


##标签 Labal ##

</table>

============
<table>
	<tbody>
		<tr>
			<th>属性名称</th>
			<th>说明</th>
		</tr>
		<tr>
		<td>anchor</td>
		<td>控制文本（或图像）在 Label 中显示的位置（方位），通过方位的英文字符串缩写（n、ne、e、se、s、sw、w、nw、center）实现定位，默认为居中（center）</td>
		</tr>
		<tr>
		<td>
bg</td>
<td>
用来设置背景色</td>
</tr>
<tr>
<td>
bd</td>
<td>
即 borderwidth 用来指定 Label 控件的边框宽度，单位为像素，默认为 2 个像素</td>
</tr>
<tr>
<td>
bitmap</td>
<td>
指定显示在 Label 控件上的位图，若指定了 image 参数，则该参数会被忽略</td>
</tr>
<tr>
<td>
compound</td>
<td>
控制 Lable 中文本和图像的混合模式，若选项设置为 CENTER，则文本显示在图像上，如果将选项设置为 BOTTOM、LEFT、RIGHT、TOP，则图像显示在文本旁边。</td>
</tr>
<tr>
<td>
cursor</td>
<td>
指定当鼠标在 Label 上掠过的时候，鼠标的的显示样式，参数值为 arrow、circle、cross、plus</td>
</tr>
<tr>
<td>
disableforeground</td>
<td>
指定当 Label 设置为不可用状态的时候前景色的颜色</td>
</tr>
<tr>
<td>
font</td>
<td>
指定 Lable 中文本的 (字体,大小,样式）元组参数格式，一个 Lable 只能设置一种字体</td>
</tr>
<tr>
<td>
fg</td>
<td>
设置 Label 的前景色</td>
</tr>
<tr>
<td>
height/width</td>
<td>
设置 Lable 的高度/宽度，如果 Lable 显示的是文本，那么单位是文本单元，如果 Label 显示的是图像，那么单位就是像素，如果不设置，Label 会自动根据内容来计算出标签的高度</td>
</tr>
<tr>
<td>
highlightbackground</td>
<td>
当 Label 没有获得焦点的时候高亮边框的颜色，系统的默认是标准背景色</td>
</tr>
<tr>
<td>
highlightcolor</td>
<td>
指定当 Lable 获得焦点的话时候高亮边框的颜色，系统默认为0，不带高亮边框</td>
</tr>
<tr>
<td>
image</td>
<td>
指定 Label 显示的图片，一般是 PhotoImage、BitmapImage 的对象</td>
</tr>
<tr>
<td>
justify</td>
<td>
表示多行文本的对齐方式，参数值为&nbsp;left、right、center，注意文本的位置取决于 anchor 选项</td>
</tr>
<tr>
<td>
padx/pady</td>
<td>
padx 指定 Label 水平方向上的间距（即内容和边框间），pady 指定 Lable 水平方向上的间距（内容和边框间的距离）</td>
</tr>
<tr>
<td>
relief</td>
<td>
指定边框样式，默认值是 &quot;flat&quot;，其他参数值有 &quot;groove&quot;、&quot;raised&quot;、&quot;ridge&quot;、&quot;solid&quot;或者&quot;sunken&quot;</td>
</tr>
<tr>
<td>
state</td>
<td>
该参数用来指定 Lable 的状态，默认值为&quot;normal&quot;（正常状态），其他可选参数值有&quot;active&quot;和&quot;disabled&quot;</td>
</tr>
<tr>
<td>
takefocus</td>
<td>
默认值为False，如果是 True，表示该标签接受输入焦点</td>
</tr>
<tr>
<td>
text</td>
<td>
用来指定 Lable 显示的文本，注意文本内可以包含换行符</td>
</tr>
<tr>
<td>
underline</td>
<td>
给指定的字符添加下划线，默认值为 -1 表示不添加，当设置为 1 时，表示给第二个文本字符添加下划线。</td>
</tr>
<tr>
<td>
wraplength</td>
<td>
将 Label 显示的文本分行，该参数指定了分行后每一行的长度，默认值为 0</td>
</tr>
</tbody>
</table>

一个控件主要由背景和前景两部分组成。其中背景由三部分构成分别是内容区域、填充区、边框，这三个区域的大小通过以下属性进行控制，如下所示：



- width/height


- padx/pady


- borderwidth
<img alt="Label控件组成" src="http://c.biancheng.net/uploads/allimg/220105/1104134631-0.gif" /></div>
============
============
#Button
它同样可以包含文本、图像、位图，并通过command参数回调函数。当然按钮也并非一定要执行回调函数（callback function），它也只可以当一个“摆设”，不过这样的按钮是没有“灵魂的”，Button 控件的使用流程如下所示：
    import tkinter as tk
    
    # 创建窗口
    window =tk.Tk()
    
    # 设置回调函数
    def callback():
    print ("click me!")
    # 使用按钮控件调用函数
    b = tk.Button(window, text="点击执行回调函数", command=callback).pack()
    # 显示窗口
    tk.mainloop()

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
anchor</td>
<td>
控制文本所在的位置，默认为中心位置（CENTER）</td>
</tr>
<tr>
<td>
activebackground</td>
<td>
当鼠标放在按钮上时候，按妞的背景颜色</td>
</tr>
<tr>
<td>
activeforeground</td>
<td>
当鼠标放在按钮上时候，按钮的前景色</td>
</tr>
<tr>
<td>
bd</td>
<td>
按钮边框的大小，默认为 2 个像素</td>
</tr>
<tr>
<td>
bg</td>
<td>
按钮的背景色</td>
</tr>
<tr>
<td>
command</td>
<td>
用来执行按钮关联的回调函数。当按钮被点击时，执行该函数</td>
</tr>
<tr>
<td>
fg</td>
<td>
按钮的前景色</td>
</tr>
<tr>
<td>
font</td>
<td>
按钮文本的字体样样式</td>
</tr>
<tr>
<td>
height</td>
<td>
按钮的高度</td>
</tr>
<tr>
<td>
highlightcolor</td>
<td>
按钮控件高亮处要显示的颜色</td>
</tr>
<tr>
<td>
image</td>
<td>
按钮上要显示的图片</td>
</tr>
<tr>
<td>
justify</td>
<td>
按钮显示多行文本时，用来指定文本的对齐方式，参数值有 LEFT/RIGHT/CENTER</td>
</tr>
<tr>
<td>
padx/pady</td>
<td>
padx 指定 x 轴（水平方向）的间距大小，pady 则表示 y轴（垂直方向）的间距大小</td>
</tr>
<tr>
<td>
ipadx/ipady</td>
<td>
ipadx 指标签文字与标签容器之间的横向距离；ipady 则表示标签文字与标签容器之间的纵向距离</td>
</tr>
<tr>
<td>
state</td>
<td>
设置按钮的可用状态，可选参数有NORMAL/ACTIVE/DISABLED，默认为 NORMAL</td>
</tr>
<tr>
<td>
text</td>
<td>
按钮控件要显示的文本</td>
</tr>
</tbody>
</table>


#扩展：按钮的布局

按钮在主窗口中的布局，通常使用 grid() 函数来完成，该函数以网格状的形式（即行和列）来管理窗口的布局。

grid() 布局管理器提供了一个sticky参数，通过该参数可以设置按钮的方位，该参数默认将控件设置居中，其他参数值有 N/S/W/E（上/下/左/右），而且可以组合在一起使用，比如 NW/WE/SE/SW/NE 等，这与anchor参数控制文本的显示位置，有着异曲同工之妙。如下图所示：

<img alt="tk button方位" src="http://c.biancheng.net/uploads/allimg/220105/1106303229-2.gif" /><br />


============

#Entry输入控件
Entry 控件使用起来非常简单允许用户输入内容，下面对该控件做简单的介绍。基本语法格式如下：
    tk_entry = Entry( master, option, ... )
Entry 控件除了具备一些共有属性之外，还有一些自身的特殊属性，如下表所示：
<table>
<tbody>
<tr>
<th>
属性名称</th>
<th>
说明</th>
</tr>
<tr>
<td>
exportselection</td>
<td>
默认情况下，如果在输入框中选中文本会复制到粘贴板，如果要忽略这个功能，可以设置为 exportselection=0</td>
</tr>
<tr>
<td>
selectbackground</td>
<td>
选中文字时的背景颜色</td>
</tr>
<tr>
<td>
selectforeground</td>
<td>
选中文字时的前景色</td>
</tr>
<tr>
<td>
show</td>
<td>
指定文本框内容以何种样式的字符显示，比如密码可以将值设为 show=&quot;*&quot;</td>
</tr>
<tr>
<td>
textvariable</td>
<td>
输入框内值，也称动态字符串，使用&nbsp;<strong>StringVar()</strong> 对象来设置，而 text 为静态字符串对象</td>
</tr>
<tr>
<td>
xscrollcommand</td>
<td>
设置输入框内容滚动条，当输入的内容大于输入框的宽度时使用户</td>
</tr>
</tbody>
</table>

Entry 控件还提供了一些常用的方法，如下所示：

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
delete()</td>
<td>
根据索引值删除输入框内的值</td>
</tr>
<tr>
<td>
get()</td>
<td>
获取输入框内的是</td>
</tr>
<tr>
<td>
set()</td>
<td>
设置输入框内的值</td>
</tr>
<tr>
<td>
insert()</td>
<td>
在指定的位置插入字符串</td>
</tr>
<tr>
<td>
index()</td>
<td>
返回指定的索引值</td>
</tr>
<tr>
<td>
select_clear()</td>
<td>
取消选中状态</td>
</tr>
<tr>
<td>
select_adujst()</td>
<td>
确保输入框中选中的范围包含 index 参数所指定的字符，选中指定索引和光标所在位置之前的字符</td>
</tr>
<tr>
<td>
select_from (index)</td>
<td>
设置一个新的选中范围，通过索引值 index 来设置</td>
</tr>
<tr>
<td>
select_present()</td>
<td>
返回输入框是否有处于选中状态的文本，如果有则返回 true，否则返回 false。</td>
</tr>
<tr>
<td>
select_to()</td>
<td>
选中指定索引与光标之间的所有值</td>
</tr>
<tr>
<td>
select_range()</td>
<td>
选中指定索引与光标之间的所有值，参数值为 start,end，要求 start 必须小于 end。</td>
</tr>
</tbody>
</table>
<br />
注意：在 Entry 控件中，我们可以通过以下方式来指定字符的所在位置：
<ul>
<li>
数字索引：表示从 0 开始的索引数字；</li>
<li>
&quot;ANCHOE&quot;：在存在字符的情况下，它对应第一个被选中的字符；</li>
<li>
&quot;END&quot;：对应已存在文本中的最后一个位置；</li>
<li>
&quot;insert(index,&#39;字符&#39;)：将字符插入到 index 指定的索引位置。</li>
</ul>
<br />

    import tkinter as tk
    
    win = tk.Tk()
    # 设置主窗口
    win.geometry('250x100')
    win.title("C语言中文网")
    win.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
    win.resizable(0,0)
    # 创建输入框控件
    entry1 = tk.Entry(win)
    # 放置输入框，并设置位置
    entry1.pack(padx=20, pady=20)
    
    entry1.delete(0, "end")
    # 插入默认文本
    entry1.insert(0,'C语言中文网，网址：c.biancheng.net')
    # 得到输入框字符串
    print(entry1.get())
    # 删除所有字符
    # entry1.delete(0, tk.END)
    win.mainloop()

#Entry控件验证功能

Entry 控件也提供了对输入内容的验证功能，比如要求输入英文字母，你却输入了数字，这就属于非法输入，Entry 控件通过以下参数实现对内容的校验：

<table>
<tbody>
<tr>
<th>
参数</th>
<th>
说明</th>
</tr>
<tr>
<td>
validate</td>
<td>
指定验证方式，字符串参数，参数值有 focus、focusin、focusout、key、all、none。&nbsp;</td>
</tr>
<tr>
<td>
validatecommand</td>
<td>
指定用户自定义的验证函数，该函数只能返回 True 或者 Fasle</td>
</tr>
<tr>
<td>
invalidcommand</td>
<td>
当 validatecommand 指定的验证函数返回 False 时，可以使用该参数值再指定一个验证函数。</td>
</tr>
</tbody>
</table>
<br />
下面对 validate 的参数值做简单的介绍：<br />
<br />
<table>
<tbody>
<tr>
<th>
参数值</th>
<th>
说明</th>
</tr>
<tr>
<td>
focus</td>
<td>
当 Entry 组件获得或失去焦点的时候验证</td>
</tr>
<tr>
<td>
focusin</td>
<td>
当 Entry 组件获得焦点的时候验证</td>
</tr>
<tr>
<td>
focuson</td>
<td>
当 Entry 组件失去焦点的时候验证</td>
</tr>
<tr>
<td>
key</td>
<td>
当输入框被编辑的时候验证</td>
</tr>
<tr>
<td>
all</td>
<td>
当出现上边任何一种情况的时候验证</td>
</tr>
<tr>
<td>
none</td>
<td>
&nbsp;默认不启用验证功能，需要注意的是这里是字符串的 &#39;none&#39;</td>
</tr>
</tbody>
</table>

##案例
    import tkinter as tk
    from tkinter import messagebox
    
    win = tk.Tk()
    # 设置主窗口
    win.geometry('250x200+250+200')
    win.title("C语言中文网")
    win.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
    win.resizable(0,0)
    
    # 创建验证函数
    def check():
    if entry1.get() == "C语言中文网":
    messagebox.showinfo("输入正确")
    return True
    else:
    messagebox.showwarning("输入不正确")
    entry1.delete(0,tk.END)
    return False
    # 新建文本标签
    labe1 = tk.Label(win,text="账号：")
    labe2 = tk.Label(win,text="密码：")
    labe1.grid(row=0)
    labe2.grid(row=1)
    # 创建动字符串
    Dy_String = tk.StringVar()
    # 使用验证参数 validata,参数值为 focusout 当失去焦点的时候，验证输入框内容是否正确
    entry1 = tk.Entry(win,textvariable =Dy_String,validate ="focusout",validatecommand=check)
    entry2 = tk.Entry(win)
    
    # 对控件进行布局管理，放在文本标签的后面
    entry1.grid(row=0, column=1)
    entry2.grid(row=1, column=1)
    
    win.mainloop()

<img alt="tkinter entry控件" src="http://c.biancheng.net/uploads/allimg/220105/110G56144-3.gif" />

不仅如此，Tkinter 还为验证函数提供可一些额外的选项，不过想要使用这些额外选项，需要提前使用 register() 方法对验证函数进行注册，。常用的选项如下所示：

<table>
<tbody>
<tr>
<th>
选项</th>
<th>
说明</th>
</tr>
<tr>
<td>
%d</td>
<td>
有 3 个参数值，其中 0 表示删除操作；1 表示插入操作；2 表示获得、失去焦点或 textvariable 变量的值被修改导</td>
</tr>
<tr>
<td>
%i</td>
<td>
当用户进行插入或者删除操作的时，该选项不爱哦是插入或者删除的索引位置，若是其他的情况则选项值为 -1</td>
</tr>
<tr>
<td>
%P</td>
<td>
该选项值指定了输入框内的文本内容，只有当输入框的值允许改变的时候，该选项值才会生效。</td>
</tr>
<tr>
<td>
%s</td>
<td>
改值为调用验证函数钱输入框内的文本内容</td>
</tr>
<tr>
<td>
%S</td>
<td>
该选项值，只有插入或者删除操作触发验证函数的时候才会生效，它表示了被删除或者插入的内容</td>
</tr>
<tr>
<td>
%v</td>
<td>
表示当前 Entry 控件的 validate 参数的值</td>
</tr>
<tr>
<td>
%V</td>
<td>
表示触发验证函数的原因，值为 focus、focusin 、focusout、all、key.. 中的一个。</td>
</tr>
<tr>
<td>
%W</td>
<td>
该选项表示控件类型，即控件的名字（Entry）</td>
</tr>
</tbody>
</table>

    import tkinter as tk
    from tkinter import messagebox
    
    win = tk.Tk()
    # 设置主窗口
    win.geometry('250x200+250+200')
    win.title("C语言中文网")
    win.iconbitmap('C:/Users/Administrator/Desktop/C语言中文网logo.ico')
    win.resizable(0,0)
    # 新建文本标签
    labe1 = tk.Label(win,text="账号：")
    labe2 = tk.Label(win,text="密码：")
    labe1.grid(row=0)
    labe2.grid(row=1)
    # 创建动字符串
    Dy_String = tk.StringVar()
    
    # 创建验证函数
    def check(strings,reason, id):
    if entry1.get() == "C语言中文网":
    messagebox.showinfo("输入正确")
    print(strings,reason,id)
    return True
    else:
    messagebox.showwarning("输入不正确")
    print(strings,reason,id)
    return False
    # 对验证函数进行注册
    CheckTest = win.register(check)
    
    # 使用验证参数 validata,参数值为 focusout 当失去焦点的时验证输入框内容是否正确
    entry1 = tk.Entry(win,textvariable =Dy_String,validate ="focusout",validatecommand=(CheckTest,'%P','%V','%W'))
    entry2 = tk.Entry(win)
    
    # 对控件进行布局管理，放在文本标签的后面
    entry1.grid(row=0, column=1)
    entry2.grid(row=1, column=1)
    win.mainloop()
程序输出结果：
    C语言中文网 focusout .!entry
    C focusout .!entry


============

##Spinbox 高级输入框
Spinbox 是 Entry 控件的升级版，它是 Tkinter 8.4 版本后新增的控件，该控件不仅允许用户直接输入内容，还支持用户使用微调选择器（即上下按钮调节器）来输入内容。在一般情况下，Spinbox 控件用于在固定的范围内选取一个值的时候使用。下面看一组简单的应用示例
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
<img alt="spinbox组件" src="http://c.biancheng.net/uploads/allimg/220105/110G51039-5.gif" />

###若不是数字，而是字符串形式的选项值，则采用values参数以元组的形式进行传参，如下所示：
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



============

##Text文本框控件
Text 文本控件是 Tkinter 中经常使用的控件，与 Entry 控件相比，Text 控件用于显示和编辑多行文本，而 Entry 控件则适合处理单行文本。

除了基本的共有属性之外，Text 控件还具备以下属性：





============


## 创建一个窗口 ##
	from tkinter import *
	
	root = Tk()  # 实例化TK
	
	root.mainloop()  # 进入事件循环
## 第一个GUI带事件的程序 ##
	from tkinter import *
	from tkinter import messagebox
	
	root = Tk()
	
	bt = Button(root)
	bt['text'] = '点我'
	bt.pack()
	
	
	def dianji(e):
	    messagebox.showinfo('message', 'give flower')  # 提示框
	
	
	bt.bind('<Button-1>', dianji)  # 绑定点击事件
	root.mainloop()  # 进入事件循环

#文件选择器 filedialog
    tkinter.filedialog 


静态工厂函数

调用以下函数时可创建模态本机外观对话框， 等待用户的选择，然后返回所选值或 访客。None



- tkinter.filedialog.**askopenfile**（mode='r'， **options)


- tkinter.filedialog.**askopenfiles**（mode='r'， **options)
以上两个函数创建一个对话框并**返回打开的 只读模式下的文件对象**。



- tkinter.filedialog.a**sksaveasfile**（mode='w'， **options)
创建一个对话框并**返回以只写模式打开的文件对象。**



- tkinter.filedialog.a**skopen文件名**（**选项)


- tkinter.filedialog.**askopen文件名**（**选项)
上述两个函数创建一个对话框并**返回 与现有文件对应的选定文件名。**



- tkinter.filedialog.**asksaveas文件名**（**options)
创建一个对话框并**返回选定的文件名。**



- tkinter.filedialog.a**skDirectory**（**Options)
提示用户选择目录。
其他关键字选项：
必须存在 - 确定所选内容是否必须是现有目录。


- 类 tkinter.filedialog.打开（主 = 无，**选项)


- 类 tkinter.filedialog.**SaveAs**（master=None， **options)
以上两个类提供了用于**保存和加载的本机对话框窗口 文件。**




<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">属性</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>

    <tr style="background-color: aqua;">
		<td>cancel_command</td>
		<td>触发对话框窗口的终止。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>dirs_double_event</td>
		<td>用于双击目录上的事件的事件处理程序。</td>
	</tr>

    <tr style="background-color: aqua;">
		<td>dirs_select_event</td>
		<td>目录上的单击事件的事件处理程序。。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>files_double_event</td>
		<td>双击文件的事件处理程序。</td>
	</tr>

    <tr style="background-color: aqua;">
		<td>files_select_event</td>
		<td>文件上的单击事件的事件处理程序。。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>filter_command</td>
		<td>按目录筛选文件。。</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>cancel_command</td>
		<td>按目录筛选文件。。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>get_filter</td>
		<td>检索当前正在使用的文件筛选器。。</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>get_selection</td>
		<td>检索当前选定的项目。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>go（dir_or_file=os.curdir， pattern='*'， default=''， key=None)</td>
		<td>呈现对话框并启动事件循环。</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>ok_event</td>
		<td>返回当前所选内容的退出对话框。。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>exit</td>
		<td>返回文件名（如果有）的退出对话框。。</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>set_filter</td>
		<td>设置文件筛选器。。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>set_selection</td>
		<td>将当前文件选择更新为文件。。</td>
	</tr>


****

</table>
类 tkinter.filedialog.LoadFileDialog（master， title=None)
FileDialog 的一个子类，用于创建用于选择 现有文件。

 ok_command()
 测试是否提供了文件，并且所选内容是否指示 已存在的文件。

类 tkinter.filedialog.SaveFileDialog（master， title=None)
FileDialog 的一个子类，用于创建用于选择 目标文件。

ok_command()¶
测试所选内容是否指向不是 目录。如果已经存在的文件是 选择。
## tkinter实现打开文件对话框并获取文件绝对路径 ##
	# 首先，导入模块
	import tkinter.filedialog
	 
	# 此处省略父容器的定义 ...
	 
	# 第2步，定义按钮并指定触发函数self.Command1_Cmd
	self.style.configure('Command1.TButton',font=('宋体',9))
	self.Command1 = Button(self.Frame1, text='打开文件', command=self.Command1_Cmd, style='Command1.TButton')
	self.Command1.place(relx=0.836, rely=0.107, relwidth=0.093, relheight=0.111)
	 
	# 第3步，定义按钮触发函数，event=None不能省略
	def Command1_Cmd(self, event=None):
	      # tkinter提供的askopenfilename函数可以实现打开文件对话框的效果，其返回值为所选文件的绝对路径
	      filename = tkinter.filedialog.askopenfilename()
	      print(filename)

## 创建Tkinter文件对话框 ##
	from tkinter import filedialog
	from tkinter import *
	
	root = Tk()
	root.filename = filedialog.askopenfilename(initialdir="/", title="Select file",
	                                           filetypes=(("Text files", "*.txt"), ("All files", "*.*")))
### 每一个参数的含义和用法。 ###



1. root：Tkinter中所有的控件都需要放在一个根控件中，这里我们创建了一个名为root的Tk控件。


1. filedialog：Tkinter自带的文件对话框模块。


1. askopenfilename：打开文件对话框，可选择打开文件。


1. asksaveasfilename：打开文件对话框，可选择保存文件。


1. initialdir：打开文件对话框时，显示的默认目录。


1. title：打开文件对话框时，显示的标题。


1. filetypes：指定接受的文件类型及其后缀名。

以上的参数里，initialdir和title是可选的，如果不指定，文件对话框会默认显示在当前文件夹下，并且标题为“Open”或“Save As”。

## 指定默认文件路径 ##
我们需要打开或保存的文件路径是固定的，可以在代码中指定默认文件路径，这样一来就可以省去手动选择文件路径的步骤。代码如下
	from tkinter import filedialog
	from tkinter import *
	
	root = Tk()
	root.filename = filedialog.askopenfilename(initialdir="/user/Downloads",
	                                           title="Select file",
	                                           filetypes=(("Text files", "*.txt"), ("All files", "*.*")))
以上例子中，文件对话框的默认打开路径为**/user/Downloads。**
## 过滤特定类型文件 ##
有时候我们只需要选择一种特定类型的文件，而不是所有类型文件。可以使用filetypes参数来过滤指定类型的文件，代码如下
	from tkinter import filedialog
	from tkinter import *
	
	root = Tk()
	root.filename = filedialog.askopenfilename(initialdir="/", title="Select image file",
	                                           filetypes=(("Image files", "*.jpg;*.png"), ("All files", "*.*")))
以上例子中，文件对话框只会显示后缀名为**.jpg**或**.png**的文件。
## 多选文件 ##
我们需要同时选择多个文件，或者选择一个文件夹。可以使用askopenfilenames和askdirectory函数，下面是示例代码：
	from tkinter import filedialog
	from tkinter import *
	
	root = Tk()
	root.filenames = filedialog.askopenfilenames(initialdir="/", title="Select images files",
	                                             filetypes=(("Image files", "*.jpg;*.png"), ("All files", "*.*")))
	root.foldername = filedialog.askdirectory(initialdir="/", title="Select folder")
以上例子中，askopenfilenames函数用于选择多个文件，askdirectory用于选择文件夹。选择的文件路径或文件夹路径分别存储在了root.filenames和root.foldername中。

### tk buton 传参 ###
	btn=Button(root,text="确认",command=lambda :print_hi("a"))
	    btn.grid(row=0,column=2)
	ttk.Button(frame, text='button',command=lambda:func(param))

### 窗口选择，并获取选择项 ###

	def print_hi(name):
   	   	 print(f'Hi,{name.get()}')


    master = Tk()
    master.geometry("175x175")

    # Tkinter string variable
    # able to store any string value
    v = StringVar(master, "1")

    # Dictionary to create multiple buttons
    values = {"RadioButton 1": "1", "RadioButton 2": "2", "RadioButton 3": "3", "RadioButton 4": "4",
              "RadioButton 5": "5"}

    # Loop is used to create multiple Radiobuttons
    # rather than creating each button separately
    for (text, value) in values.items():
        radiobutton = Radiobutton(master, text=text, variable=v, value=value, indicator=0, background="light blue",
                                  command=lambda: print_hi(v))
        radiobutton.pack(fill=X,
                         ipady=5)
## messagebox ##
    from tkinter import messagebox
### 该函数用于向用户展示一条信息，通常用于提示操作成功或失败的消息 
    messagebox.showinfo("提示", "当前操作成功！")
###该函数用于向用户发出警告信息，通常用于提示用户操作不当的消息。其中，title是信息框的标题，message是要显示的消息。
    messagebox.showwarning("警告", "当前操作失败！")
#### 该函数用于向用户显示一个错误信息，通常用于提示程序出现错误或异常。其中，title是信息框的标题，message是要显示的消息。 ####

    messagebox.showerror("错误", "程序出现异常，请稍后再试！")
#### 该函数用于向用户展示一个带有“是”或“否”按钮的询问框，用户可以选择答案。其中，title是信息框的标题，message是要询问的问题。该方法将返回用户选择的答案，通常是“Yes”或“No” ####

	if messagebox.askquestion("询问", "是否要删除该文件？") == 'yes':
	    # 用户点击了“是”按钮，执行删除操作
	else:
	    # 用户点击了“否”按钮，取消操作

### 该函数用于向用户展示一个带有“确定”或“取消”按钮的询问框，用户可以选择答案。其中，title是信息框的标题，message是要询问的问题。该方法将返回用户选择的答案，通常是True或False，其中True表示用户选择了“确定”，False表示用户选择了“取消” ###
	if messagebox.askokcancel("询问", "确定要关闭该窗口吗？"):
	    # 用户选择了“确定”，执行关闭窗口操作
	else:
	    # 用户选择了“取消”，继续执行操作
### 该函数用于向用户展示一个带有“是”或“否”按钮的询问框，用户可以选择答案。其中，title是信息框的标题，message是要询问的问题。该方法将返回用户选择的答案，通常是True或False，其中True表示用户选择了“是”，False表示用户选择了“否”。 ###
	if messagebox.askyesno("询问", "当前操作可能影响系统稳定性，确定要继续吗？"):
	    # 用户选择了“是”，继续执行操作
	else:
	    # 用户选择了“否”，取消操作
## 锚点（anchor） ##
<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">属性</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>
	<tr style="background-color: aqua;">
		<td>N</td>
		<td>North，上边缘</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>S</td>
		<td>South，下边缘</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>E</td>
		<td>East，右边缘</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>W</td>
		<td>West，左边缘</td>
	</tr>

</table>

### Tkinter 填充样式 fill ###
在 Tkinter 中，我们可以使用 fill 属性来设置组件在容器中的填充方式，该属性有四个可选值：NONE、X、Y、BOTH。
<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">属性</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>
	<tr style="background-color: aqua;">
		<td>NONE</td>
		<td>组件不填充</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>X</td>
		<td>横向填充</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>Y</td>
		<td>纵向填充</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>BOTH</td>
		<td>同时横向与纵向填充</td>
	</tr>

</table>

## Tkinter 的 pack() 方法 ##
pack() 方法是布局管理器，它将控件自动放置在矩形区域中，使得整个图形界面更加美观

    widget.pack(options)
widget 表示需要布置的控件，options 表示可选的参数选项，可以是以下一种或多种：

- expand：设置为 True 时，控件可以扩大以填充空白区域。
- fill：设置为 “x” 时，控件在水平方向上可伸展。
- fill：设置为 “y” 时，控件在垂直方向上可伸展。
- fill：设置为 “both” 时，控件在水平和垂直方向上可伸展。
- side：指定控件在容器中停靠的位置，可以是 “top”、”bottom”、”left” 或 “right”。
- anchor：控制控件在容器中的位置，可以是 “n”、”e”、”s”、”w”、”center”、”ne”、”nw”、”se” 或 “sw”。

## Tkinter grid() 方法 ##
grid()方法是一种常用的布局方式，它可以将组件分成网格状的布局，并能够根据具体的需求来分配布局的行列大小

### grid()方法布局界面需要注意以下几点 ###
- grid()方法会将组件分成网格状的布局。
- 所有组件的行列位置都是从0开始计算的。
- 可以通过rowspan和columnspan来合并网格，实现外观更加复杂的布局。

### grid()方法的属性和说明： ###

<table border="2"bordercolor="green" >
	<th style="size: 14;color:  black;background-color: blanchedalmond;">属性</th>
	<th style="size: 14;color:  black;background-color: blanchedalmond;">介绍</th>
	<tr style="background-color: aqua;">
		<td>row</td>
		<td>组件所在的行数，从0开始计数。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>column</td>
		<td>组件所在的列数，从0开始计数。</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>rowspan</td>
		<td>组件占据的行数。</td>
	</tr>
	<tr style="background-color: aquamarine;">
		<td>columnspan</td>
		<td>组件占据的列数。</td>
	</tr>
	<tr style="background-color: aqua;">
		<td>sticky</td>
		<td>组件在所在的单元格中的位置，可选值为N（上）、E（右）、S（下）、W（左）、NE（右上方）、NW（左上方）、SE（右下方）、SW（左下方）。sticky=W+E)</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>grid_rowconfigure(index, **options)</td>
		<td>设定行属性。见行属性设定表（权重）</td>
	</tr>
    <tr style="background-color: aqua;">
		<td>grid_columnconfigure(index, **options)(index, **options)</td>
		<td>设置列属性。见列属性设定表（权重）</td>
	</tr>
</table>


#权重案例
    print_hi('PyCharm')
    root = Tk()
    root.title("工具使用")
    # root.geometry("800x600")
    root.config(bg="#F5F5F5")

    # mwith=15
    # mheight=1
    mbg="#40E0D0"
    mFont=8
    # =============第一行标题=================
    Button(master=root, text="颜色选择器",bg=mbg,font=mFont,command=lambda :adbColorSelect()).grid(row=0,column=0,sticky=E+W)
    Button(master=root, text="颜色选择器",bg=mbg,font=mFont,command=lambda :adbColorSelect()).grid(row=0,column=1,sticky=E+W)
    Button(master=root, text="颜色选择器",bg=mbg,font=mFont,command=lambda :adbColorSelect()).grid(row=0,column=2,sticky=E+W)

    # 给标题设置权重
    childrenLenght = root.children.__len__()
    for i in range(childrenLenght):
        root.columnconfigure(i,weight=1)

    # =============第二行开始=================
    Button(master=root, text="颜色选择器",bg=mbg,font=mFont,command=lambda :adbColorSelect()).grid(row=1,column=0,sticky=E+W)
    # ==============================
    root.mainloop()

