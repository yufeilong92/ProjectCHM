# bat脚本编辑 #



- 显示中文

		chcp 65001
	
- 注解

  	 	::

- 输出提示信息 

  	 	ECHO 信息内容

- 关闭DOS命令提示符 

  	 	在DOS提示符状态下键入ECHO OFF，能够关闭DOS提示符的显示使屏幕只留下光标，直至键入ECHO ON，提示符才会重新出现

- 输出空行，即相当于输入一个回车

  		 ECHO．

      	值得注意的是命令行中的**“．”**要紧跟在ECHO后面中间不能有空格，否则“．”将被当作提示信息输出到屏幕。

- 建立新文件或增加文件内容 

  	格式：
	
		- ECHO 文件内容>文件名      
		         
		- ECHO 文件内容>>文件名

   

- PAUSE

  	 	PAUSE 运行显示：请按任意键继续. . .

- ERRORLEVEL 程序返回码

  		echo %errorlevel%
		每个命令运行结束，可以用这个命令行格式查看返回码
		用于判断刚才的命令是否执行成功
		默认值为0，一般命令执行出错会设 errorlevel 为1
        choice配合使用

        案例：
        choice /d Y /t 1 /c YN /m Y打开，N关闭
		if %errorlevel% equ 1 goto LOGOPEN
		if %errorlevel% equ 2 goto LOGON

- TITLE 设置cmd窗口的标题

		title 新标题        #可以看到cmd窗口的标题栏变了


- COLOR 设置默认的控制台前景和背景颜色

		COLOR [attr]
		  attr        指定控制台输出的颜色属性
		颜色属性由两个十六进制数字指定 -- 第一个为背景，第二个则为
		前景。每个数字可以为以下任何值之一:
			0 = 黑色       8 = 灰色
		    1 = 蓝色       9 = 淡蓝色
		    2 = 绿色       A = 淡绿色
		    3 = 湖蓝色    B = 淡浅绿色
		    4 = 红色       C = 淡红色
		    5 = 紫色       D = 淡紫色
		    6 = 黄色       E = 淡黄色
		    7 = 白色       F = 亮白色

		如果没有给定任何参数，该命令会将颜色还原到 CMD.EXE 启动时
		的颜色。这个值来自当前控制台窗口、/T 开关或
		DefaultColor 注册表值。
		如果用相同的前景和背景颜色来执行 COLOR 命令，COLOR 命令
		会将 ERRORLEVEL 设置为 1。
		例如: "COLOR fc" 在亮白色上产生亮红色

- GOTO 会点编程的朋友就会知道这是跳转的意思

		if {%1}=={} goto noparms
		if "%2"=="" goto noparms

		标签的名字可以随便起，但是最好是有意义的字符串啦，前加个冒号用来表示这个字符串是标签，goto命令就是根据这个冒号（:）来寻找下一步跳到到那里。最好有一些说明这样你别人看起来才会理解你的意图啊。
        @echo off
		:start
		set /a var+=1
		echo %var%
		if %var% leq 3 GOTO start
		pause

- start 命令

		批处理中调用外部程序的命令（该外部程序在新窗口中运行，批处理程序继续往下执行，不理会外部程序的运行状况），如果直接运行外部程序则必须等外部程序完成后才继续执行剩下的指令
		例：start explorer d:\
		调用图形界面打开D盘


- pushd 和 popd

		切换当前目录
		@echo off
		c: & cd\ & md mp3       #在 C:\ 建立 mp3 文件夹
		md d:\mp4               #在 D:\ 建立 mp4 文件夹
		cd /d d:\mp4            #更改当前目录为 d:\mp4
		pushd c:\mp3            #保存当前目录，并切换当前目录为 c:\mp3
		popd                    #恢复当前目录为刚才保存的 d:\mp4
		一般用处不大，在当前目录名不确定时，会有点帮助。（dos编程中很有用）

- IF 条件判断语句

		语法格式如下：
		IF [NOT] ERRORLEVEL number command
		IF [NOT] string1==string2 command
		IF [NOT] EXIST filename command

		(1) IF [NOT] ERRORLEVEL number command
		IF ERRORLEVEL这个句子必须放在某一个命令的后面，执行命令后由IF ERRORLEVEL 来判断命令的返回值。
		Number的数字取值范围0~255，判断时值的排列顺序应该由大到小。返回的值大于等于指定的值时，条件成立

		(2) IF [NOT] string1==string2 command
		string1和string2都为字符的数据，英文内字符的大小写将看作不同，这个条件中的等于号必须是两个（绝对相等的意思）
		条件相等后即执行后面的command
		检测当前变量的值做出判断，为了防止字符串中含有空格，可用以下格式
		if [NOT] {string1}=={string2} command
		if [NOT] [string1]==[string2] command
		if [NOT] "string1"=="string2" command
		这种写法实际上将括号或引号当成字符串的一部分了，只要等号左右两边一致就行了，比如下面的写法就不行：
		if {string1}==[string2] command

		(3) IF [NOT] EXIST filename command
		EXIST filename为文件或目录存在的意思
		echo off
		IF EXIST autoexec.bat echo 文件存在！
		IF not EXIST autoexec.bat echo 文件不存在！
		这个批处理大家可以放在C盘和D盘分别执行，看看效果


- @  命令行回显屏蔽符

		这个字符在批处理中的意思是关闭当前行的回显
		ECHO OFF可以关闭掉整个批处理命令的回显，但不能关掉ECHO OFF这个命令，现在我们在ECHO OFF这个命令前加个@，就可以达到所有命令均不回显的要求

- %  批处理变量引导符

		%* 从第一个参数开始的所有参数
		参数%0具有特殊的功能，可以调用批处理自身，以达到批处理本身循环的目的，也可以复制文件自身等等

- “> ”  重定向符

		使用命令：echo hello >1.txt将建立文件1.txt，内容为”hello “（注意行尾有一空格）
		使用命令：echo hello>1.txt将建立文件1.txt，内容为”hello“（注意行尾没有空格）

- >>  重定向符

		这个符号的作用和>有点类似，但他们的区别是>>是传递并在文件的末尾追加，而>是覆盖
		echo hello > 1.txt
		echo world >>1.txt
		这时候1.txt 内容如下:
		hello
		world

- 自定义变量

		自定义变量就是由我们来给他赋予值的变量
		要使用自定义变量就得使用set命令了

		@echo off
		set var=我是值
		echo %var%
		pause

		如果我们想让用户手工输入变量的值,而不是在代码里指定,可以用用set命令的/p参数
		@echo off
		set /p var=请输入变量的值
		echo %var%
		pause

		var变量名  =号右边的是提示语,不是变量的值
		变量的值由我们运行后自己用键盘输入! 

- if…else…条件语句

		DOS条件语句主要有以下形式：
		IF [NOT] ERRORLEVEL number command
		IF [NOT] string1==string2 command
		IF [NOT] EXIST filename command
		增强用法：IF [/I] string1 compare-op string2 command
		增强用法中加上/I就不区分大小写了!
		增强用法中还有一些用来判断数字的符号

		EQU - 等于
		NEQ - 不等于
		LSS - 小于
		LEQ - 小于或等于
		GTR - 大于
		GEQ - 大于或等于

		IF EXIST filename (
		    del filename
		) ELSE (
		    echo filename missing
		)




- 随机数（%random%）的应用技巧

  	 `::`

- choice命令详解

		::choice /d 1 /t 1 /c 123 /m 1创建目录或文本，2导出目录，3取消
		choice /c 123 /m 1创建目录或文本，2导出目录，3取消
		choice [/C choices] [/N] [/CS] [/T timeout /D choice] [/M text]
		choice 命令可以让用户输入一个字符，从而运行不同的命令

		$ choice /?
		CHOICE [/C choices] [/N] [/CS] [/T timeout /D choice] [/M text]
		
		描述:
		    该工具允许用户从选择列表选择一个项目并返回所选项目的索引。
		
		参数列表:
		   /C    choices       指定要创建的选项列表。默认列表是 "YN"。
		   /N                  在提示符中隐藏选项列表。提示前面的消息得到显示，
		                       选项依旧处于启用状态。
		   /CS                 允许选择分大小写的选项。在默认情况下，这个工具
		                       是不分大小写的。
		   /T    timeout       做出默认选择之前，暂停的秒数。可接受的值是从 0
		                       到 9999。如果指定了 0，就不会有暂停，默认选项
		                       会得到选择。
		   /D    choice        在 nnnn 秒之后指定默认选项。字符必须在用 /C 选
		                       项指定的一组选择中; 同时，必须用 /T 指定 nnnn。
		   /M    text          指定提示之前要显示的消息。如果没有指定，工具只
		                       显示提示。
		   /?                  显示此帮助消息。
		
		   注意:
		   ERRORLEVEL 环境变量被设置为从选择集选择的键索引。列出的第一个选
		   择返回 1，第二个选择返回 2，等等。如果用户按的键不是有效的选择，
		   该工具会发出警告响声。如果该工具检测到错误状态，它会返回 255 的
		   ERRORLEVEL 值。如果用户按 Ctrl+Break 或 Ctrl+C 键，该工具会返回 0
		   的 ERRORLEVEL 值。在一个批程序中使用 ERRORLEVEL 参数时，将参数降
		   序排列。
		
		示例:
		   CHOICE /?
		   CHOICE /C YNC /M "确认请按 Y，否请按 N，或者取消请按 C。"
		   CHOICE /T 10 /C ync /CS /D y
		   CHOICE /C ab /M "选项 1 请选择 a，选项 2 请选择 b。"
		   CHOICE /C ab /N /M "选项 1 请选择 a，选项 2 请选择 b。"


-  exit 命令

  	 `::`

- shutdown命令

  	 `::`

- 注解

  	 `::`

- 注解

  	 `::`

- 注解

  	 `::`

