# Tkinter #

一个最简单的 Tkinter 程序至少应包含以下四个部分：

- 导入 tkinter 模块
- 创建主窗口，也称 root 窗口（即根窗口）
- 添加人机交互控件，同时编写相应的事件函数
- 通过主循环（mainloop）来显示主窗口

##案例

    # -*- coding:utf-8 -*-
    import tkinter as tk
    # 调用Tk()创建主窗口
    root_window =tk.Tk()
    # 给主窗口起一个名字，也就是窗口的名字
    root_window.title('C语言中文网：c.biancheng.net')
    #开启主循环，让窗口处于显示状态
    root_window.mainloop()
##功能

###添加文本
此处使用了标签 Lable 控件来实现。

    # 添加文本标签，text参数指定内容
    text=tk.Label(root_window,text="C语言中文网，欢迎您",bg="yellow",fg="red",font=('Times', 20, 'bold italic'))
    # 将标签对象放置在主窗口内
    text.pack()
###添加按钮
添加按钮的逻辑和添加文本标签类似，值得注意的是，按钮控件通过command参数实现了“关闭窗口”功能，代码如下：

    # 添加按钮
    button=tk.Button(root_window,text="关闭",command=root_window.quit)
    # 这里将按钮放置在主窗口的底部
    button.pack(side="bottom")
Tkinter 提供了十余种常用类型的控件，每个控件都有相应的属性，比如颜色（前景色/背景色/颜色常量）、文本内容、字体样式、控件大小、控件样式、控件命令等等，这些会在后续内容做详细介绍。


##Tkinter常用控件和属性 ##

### 控件类型 ###

<table>
<tbody>
<tr>
<th>
控件类型</th>
<th>
控件名称</th>
<th>
控件作用</th>
</tr>
<tr>
<td>
Button</td>
<td>
按钮</td>
<td>
点击按钮时触发/执行一些事件（函数）</td>
</tr>
<tr>
<td>
Canvas</td>
<td>
画布</td>
<td>
提供绘制图，比如直线、矩形、多边形等</td>
</tr>
<tr>
<td>
Checkbutton</td>
<td>
复选框</td>
<td>
多项选择按钮，用于在程序中提供多项选择框</td>
</tr>
<tr>
<td>
Entry</td>
<td>
文本框输入框</td>
<td>
用于接收单行文本输入</td>
</tr>
<tr>
<td>
Frame</td>
<td>
框架（容器）控件</td>
<td>
定义一个窗体（根窗口也是一个窗体），用于承载其他控件，即作为其他控件的容器</td>
</tr>
<tr>
<td>
Lable</td>
<td>
标签控件</td>
<td>
用于显示单行文本或者图片</td>
</tr>
<tr>
<td>
LableFrame</td>
<td>
容器控件</td>
<td>
一个简单的容器控件，常用于复杂的窗口布局。</td>
</tr>
<tr>
<td>
Listbox</td>
<td>
列表框控件</td>
<td>
以列表的形式显示文本</td>
</tr>
<tr>
<td>
Menu</td>
<td>
菜单控件</td>
<td>
菜单组件（下拉菜单和弹出菜单）</td>
</tr>
<tr>
<td>
Menubutton</td>
<td>
菜单按钮控件</td>
<td>
用于显示菜单项</td>
</tr>
<tr>
<td>
Message</td>
<td>
信息控件</td>
<td>
用于显示多行不可编辑的文本，与 Label控件类似，增加了自动分行的功能</td>
</tr>
<tr>
<td>
messageBox</td>
<td>
消息框控件</td>
<td>
定义与用户交互的消息对话框</td>
</tr>
<tr>
<td>
OptionMenu</td>
<td>
选项菜单</td>
<td>
下拉菜单</td>
</tr>
<tr>
<td>
PanedWindow</td>
<td>
窗口布局管理组件</td>
<td>
为组件提供一个框架，允许用户自己划分窗口空间</td>
</tr>
<tr>
<td>
Radiobutton</td>
<td>
单选框</td>
<td>
单项选择按钮，只允许从多个选项中选择一项</td>
</tr>
<tr>
<td>
Scale</td>
<td>
进度条控件</td>
<td>
定义一个线性“滑块”用来控制范围，可以设定起始值和结束值，并显示当前位置的精确值</td>
</tr>
<tr>
<td>
Spinbox</td>
<td>
高级输入框</td>
<td>
Entry 控件的升级版，可以通过该组件的上、下箭头选择不同的值</td>
</tr>
<tr>
<td>
Scrollbar</td>
<td>
滚动条</td>
<td>
默认垂直方向，鼠标拖动改变数值，可以和 Text、Listbox、Canvas等控件配合使用</td>
</tr>
<tr>
<td>
Text</td>
<td>
多行文本框</td>
<td>
接收或输出多行文本内容</td>
</tr>
<tr>
<td>
Toplevel</td>
<td>
子窗口</td>
<td>
在创建一个独立于主窗口之外的子窗口，位于主窗口的上一层，可作为其他控件的容器</td>
</tr>
</tbody>
</table>
<table>
<tbody>
<tr>
<th>
控件类型</th>
<th>
控件名称</th>
<th>
控件作用</th>
</tr>
<tr>
<td>
Button</td>
<td>
按钮</td>
<td>
点击按钮时触发/执行一些事件（函数）</td>
</tr>
<tr>
<td>
Canvas</td>
<td>
画布</td>
<td>
提供绘制图，比如直线、矩形、多边形等</td>
</tr>
<tr>
<td>
Checkbutton</td>
<td>
复选框</td>
<td>
多项选择按钮，用于在程序中提供多项选择框</td>
</tr>
<tr>
<td>
Entry</td>
<td>
文本框输入框</td>
<td>
用于接收单行文本输入</td>
</tr>
<tr>
<td>
Frame</td>
<td>
框架（容器）控件</td>
<td>
定义一个窗体（根窗口也是一个窗体），用于承载其他控件，即作为其他控件的容器</td>
</tr>
<tr>
<td>
Lable</td>
<td>
标签控件</td>
<td>
用于显示单行文本或者图片</td>
</tr>
<tr>
<td>
LableFrame</td>
<td>
容器控件</td>
<td>
一个简单的容器控件，常用于复杂的窗口布局。</td>
</tr>
<tr>
<td>
Listbox</td>
<td>
列表框控件</td>
<td>
以列表的形式显示文本</td>
</tr>
<tr>
<td>
Menu</td>
<td>
菜单控件</td>
<td>
菜单组件（下拉菜单和弹出菜单）</td>
</tr>
<tr>
<td>
Menubutton</td>
<td>
菜单按钮控件</td>
<td>
用于显示菜单项</td>
</tr>
<tr>
<td>
Message</td>
<td>
信息控件</td>
<td>
用于显示多行不可编辑的文本，与 Label控件类似，增加了自动分行的功能</td>
</tr>
<tr>
<td>
messageBox</td>
<td>
消息框控件</td>
<td>
定义与用户交互的消息对话框</td>
</tr>
<tr>
<td>
OptionMenu</td>
<td>
选项菜单</td>
<td>
下拉菜单</td>
</tr>
<tr>
<td>
PanedWindow</td>
<td>
窗口布局管理组件</td>
<td>
为组件提供一个框架，允许用户自己划分窗口空间</td>
</tr>
<tr>
<td>
Radiobutton</td>
<td>
单选框</td>
<td>
单项选择按钮，只允许从多个选项中选择一项</td>
</tr>
<tr>
<td>
Scale</td>
<td>
进度条控件</td>
<td>
定义一个线性“滑块”用来控制范围，可以设定起始值和结束值，并显示当前位置的精确值</td>
</tr>
<tr>
<td>
Spinbox</td>
<td>
高级输入框</td>
<td>
Entry 控件的升级版，可以通过该组件的上、下箭头选择不同的值</td>
</tr>
<tr>
<td>
Scrollbar</td>
<td>
滚动条</td>
<td>
默认垂直方向，鼠标拖动改变数值，可以和 Text、Listbox、Canvas等控件配合使用</td>
</tr>
<tr>
<td>
Text</td>
<td>
多行文本框</td>
<td>
接收或输出多行文本内容</td>
</tr>
<tr>
<td>
Toplevel</td>
<td>
子窗口</td>
<td>
在创建一个独立于主窗口之外的子窗口，位于主窗口的上一层，可作为其他控件的容器</td>
</tr>
</tbody>
</table>

除了上述控件外，还有一些高级控件，比如 PanedWindow、messagebox、LableFrame、Spinbox，在后续章节也会讲解。

### 控件基本属性 ###

#### 控件的共用属性做简单介绍 ####

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
anchor</td>
<td>
定义控件或者文字信息在窗口内的位置</td>
</tr>
<tr>
<td>
bg</td>
<td>
bg 是 background 的缩写，用来定义控件的背景颜色，参数值可以颜色的十六进制数，或者颜色英文单词</td>
</tr>
<tr>
<td>
bitmap</td>
<td>
定义显示在控件内的位图文件</td>
</tr>
<tr>
<td>
borderwidth</td>
<td>
定于控件的边框宽度，单位是像素</td>
</tr>
<tr>
<td>
command</td>
<td>
该参数用于执行事件函数，比如单击按钮时执行特定的动作，可将执行用户自定义的函数</td>
</tr>
<tr>
<td>
cursor</td>
<td>
当鼠标指针移动到控件上时，定义鼠标指针的类型，字符换格式，参数值有 crosshair（十字光标）watch（待加载圆圈）plus（加号）arrow（箭头）等</td>
</tr>
<tr>
<td>
font</td>
<td>
若控件支持设置标题文字，就可以使用此属性来定义，它是一个数组格式的参数 (字体,大小，字体样式)</td>
</tr>
<tr>
<td>
fg</td>
<td>
fg 是 foreground 的缩写，用来定义控件的前景色，也就是字体的颜色</td>
</tr>
<tr>
<td>
height</td>
<td>
该参数值用来设置控件的高度，文本控件以字符的数目为高度（px），其他控件则以像素为单位</td>
</tr>
<tr>
<td>
image</td>
<td>
定义显示在控件内的图片文件</td>
</tr>
<tr>
<td>
justify</td>
<td>
定义多行文字的排列方式，此属性可以是 LEFT/CENTER/RIGHT</td>
</tr>
<tr>
<td>
padx/pady</td>
<td>
定义控件内的文字或者图片与控件边框之间的水平/垂直距离</td>
</tr>
<tr>
<td>
relief</td>
<td>
定义控件的边框样式，参数值为FLAT（平的）/RAISED（凸起的）/SUNKEN（凹陷的）/GROOVE（沟槽桩边缘）/RIDGE（脊状边缘）</td>
</tr>
<tr>
<td>
text</td>
<td>
定义控件的标题文字</td>
</tr>
<tr>
<td>
state</td>
<td>
控制控件是否处于可用状态，参数值默认为 NORMAL/DISABLED，默认为 NORMAL（正常的）</td>
</tr>
<tr>
<td>
width</td>
<td>
用于设置控件的宽度，使用方法与&nbsp;height 相同</td>
</tr>
</tbody>
</table>

