# BeautifulSoup4 #
BeautifulSoup 提供一些简单的、Python 式的函数用来处理导航、搜索、修改分析树等功能。它是一个工具箱，通过解析文档为用户提供需要抓取的数据，因为简单，所以不需要多少代码就可以写出一个完整的应用程序。 BeautifulSoup 自动将输入文档转换为 Unicode 编码，输出文档转换为 utf-8 编码。你不需要考虑编码方式，除非文档没有指定一个编码方式，这时你仅仅需要说明一下原始编码方式就可以了。 BeautifulSoup 已成为和 lxml、html5lib 一样出色的 Python 解释器，为用户灵活地提供不同的解析策略或强劲的速度

## 安装 ##
    pip install beautifulsoup4

## 解析器 ##
|解析器|使用方式|
|:---|:---|
|python标准库|BeautifulSoup（markup,‘html.parser’ ）|
|lxml HTML解析器|BeautifulSoup（markup,‘lxml’）|
|lxml XML解析器|BeautifulSoup（markup,‘xml’）|
|html5lib|BeautifulSoup（markup,‘html5lib’|

## BeautifulSoup类的基本元素 ##
|基本元素|说明|
|:---|:---|
|Tag|标签，最基本的信息组织元素，分别用<>和</> 标明开头和结尾|
|Name|标签的名字，/p>.../p> 的名字是“p”，格式<tag>.name|
|Attributes|标签的属性，字典形式组织，格式：<tag>.attrs|
|NavigableString|标签内非属性字符串，<><\>中字符串，格式：<tag>.string|
|Comment|标签内字符串的注释部分，一种特殊的Comment类型|
## 使用 ##
导入模块

	from bs4 import BeautifulSoup
设置解析器，传递需要解析的html文档

	soup = BeautifulSoup(html,'lxml')
格式化代码
	soup.prettify()
查看title标签内的文本
	soup.title.string

示例

	>>from bs4 import BeautifulSoup
	>>soup = BeautifulSoup('<p>Hello</p>', 'lxml')
	>>print(soup.p.string)
	>>'''Hello''
	
	from bs4 import Beautifulsoup
	
	soup = Beautifulsoup(html_doc, 'html.parser')
	对象 = soup.body.a		# 查找最开始第一个body标签下的第一个a标签
	
	
	对象.name			  # 获取标签的名字
	对象.attrs		  # 获取标签的所有属性
	对象.get(属性名)		# 获取标签指定属性
	对象.text			  # 获取标签的文本内容（子子孙孙都拼接在一起的）
	对象.get_text()	  # 和上面一样
	对象.string		  # 当前标签下有文本才取出来，否则全是None
	对象.strings		  # 子子孙孙的内容都放大生成器中
	## 标签选择器 ##

### 返回title标签 ###

	soup.title

### 返回标签的类型 ###
	type(soup.title) #返回<class 'bs4.element.Tag'>一个类变量
### 返回head标签 ###
	soup.head
### 返回p标签,只返回第一个p标签，如果有多个只能输出第一个 ###
	soup.p
## 获取名称 ##
### 返回title标签的名称 ###
	soup.title.name  #返回title 最外层标签的名称
### 获取属性 ###
	html = '''<p class="title" name="zhaojia">the paragraph</p>'''
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.p.attrs['name'] #返回zhaojia 
	soup.p['name']] #返回结果同上
### 获取内容 ###
	html = '''<p class="title" name="zhaojia">the paragraph</p>'''
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.p.string #返回the paragraph 
### 嵌套选择 ###
	html = '''<head><p class="title" name="zhaojia">the paragraph</p><head>'''
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.head.p.string  #返回the paragraph
	soup.head.p.attrs['name'] # 返回zhaojia
### 子节点和子孙节点 ###
	html = '''<head><p class="title" name="zhaojia">the paragraph</p><head>'''
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.head.contents #返回所有子节点列表
	the = soup.head.children
	for i,children in enumerate(the)：
	    print(i,children) # 返回一个iterable 必须使用for循环遍历出来
	soup.head.descendants #获取所有的子孙节点，返回类型是iterable object
### 获取父节点和祖先节点 ###
	soup.a.parent #获取父节点，输出父节点全部内容
	soup.a.parents #获取祖先节点
###  获取兄弟节点 ###
	soup.a.next_siblings
	soup.a.previous_siblings
## 标准选择器 ##
###  find_all（）方法 ###
#### 根据name查找（name-标签名） ####
name 参数可以查找所有名字为 name 的tag,字符串对象会被自动忽略掉.

	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.find_all('p') 查找所有的p标签，并且以列表的形式返回
	type(soup.find_all('p')) 返回类型是<class 'bs4.element.Tag'>
### keyword 参数 ###
如果一个指定名字的参数不是搜索内置的参数名,搜索时会把该参数当作指定名字tag的属性来搜索,如果包含一个名字为 id 的参数,Beautiful Soup会搜索每个tag的”id”属性.

	soup.find_all(id='link2')
	#[<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>]
如果传入 href 参数,Beautiful Soup会搜索每个tag的”href”属性:

	soup.find_all(href=re.compile("elsie"))
	#[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>]
### CSS搜索 ###
通过 class_ 参数搜索有指定CSS类名的tag:

	soup.find_all("a", class_="sister")
	#[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
	#<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
	#<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]

### 正则表达式 ###
	import re
	
	soup.find_all(re.compile('^b'))		# 查找出所有以b开头的标签

class_ 参数同样接受不同类型的 过滤器 ,字符串,正则表达式,方法或 True :

	 soup.find_all(class_=re.compile("itl"))
    #[<p class="title"><b>The Dormouse's story</b></p>]
    
    def has_six_characters(css_class):
        return css_class is not None and len(css_class) == 6
    
    soup.find_all(class_=has_six_characters)
    #[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
    #<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>,
    #<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]

href的值

    urla = item.findNext('a')['href']
### 列表 ###
	soup.find_all(['a', 'b'])	# 找到所有的a标签和b标签


#### 根据attrs查找（attrs-属性） ####
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.find_all(attrs = {'id':'list-1'})
####  根据text查找 （text-文本） ####
	from bs4 import BeautifulSoup
	soup = BeautifulSoup(html,'lxml')
	soup.find_all(text = 'the')
### find（）方法 ###
find方法返回一个，findall返回所有
### 总结 ###
	soup.find_all(name='a')  # # 查找所有 a 标签
	soup.find_all(name=['a','b'])  # 查找所有 a 标签和 b 标签
	soup.find_all(name=re.compile("^b"))  # 以 b 开头的标签查找
	
	soup.find_all("a", class_="sister")  # 查找class为sister的a标签
	
	soup.find_all(attrs={"属性名":"值"})
	
	soup.find_all(text="Elsie")  # 通过文本内容查找
	
	soup.find_all(id='link2')  # 通过id查找元素
	soup.find_all(class_="sister")  # 通过class查找元素
	
	soup.find_all("a", limit=2)  # 限制返回2个









## CSS选择器 ##



- 通过select（）直接传入CSS选择器就可以查找


- class 选择器前面加一个点号


- id 选择器前面加一个#

标签什么都不需要加
soup.select(’.class’)
soup.select(’#id #id2’)两个条件用空格隔开
soup.select(tag1 tag3)
### 获取属性 ###
	for ul in soup.select('ul'):
	    print(ul['id'])
	    print(ul.attrs['id'])
### 获取内容 ###

	for ul in soup.select('ul'):
	    print(ul.get_text)
###  通过标签来查找 ###
	soup.select('title')

### 总结 ###
	print(soup.select(".sister"))  # 查找类为sister的元素，返回一个列表
	print(soup.select("#link1"))  # 查找id为link1的元素，返回一个列表
	print(soup.select("a"))  # 查找a标签，返回一个列表
	print(soup.select("p[class=title]"))  # 查找class为title的p标签
	print(soup.select("p #link2"))  # 查看在p标签里的id为link2的p标签



# 示例 #
	>>> soup = BeautifulSoup(html_doc, 'html.parser') #也可以指定lxml或其他解析器                                   
	>>> print(soup.prettify())                        #以优雅的方式显示出来
	<html>
	 <head>
	  <title>
	   The Dormouse's story
	  </title>
	 </head>
	 <body>
	  <p class="title">
	   <b>
	    The Dormouse's story
	   </b>
	  </p>
	  <p class="story">
	   Once upon a time there were three little sisters; and their names were
	   <a class="sister" href="http://example.com/elsie" id="link1">
	    Elsie
	   </a>
	   ,
	   <a class="sister" href="http://example.com/lacie" id="link2">
	    Lacie
	   </a>
	   and
	   <a class="sister" href="http://example.com/tillie" id="link3">
	    Tillie
	   </a>
	   ;
	and they lived at the bottom of a well.
	  </p>
	  <p class="story">
	   ...
	  </p>
	 </body>
	</html>
使用

	>>> soup.title                              #访问<title>标签的内容
	<title>The Dormouse's story</title>
	>>> soup.title.name                         #查看标签的名字
	'title'
	>>> soup.title.text                         #查看标签的文本
	"The Dormouse's story"
	>>> soup.title.string                       #查看标签的文本
	"The Dormouse's story"
	>>> soup.title.parent                       #查看上一级标签
	<head><title>The Dormouse's story</title></head>
	>>> soup.head
	<head><title>The Dormouse's story</title></head>
	>>> soup.b                                   #访问<b>标签的内容
	<b>The Dormouse's story</b>
	>>> soup.body.b                              #访问<body>中<b>标签的内容
	<b>The Dormouse's story</b>
	>>> soup.name                  #把整个BeautifulSoup对象看作标签对象
	'[document]'
	>>> soup.body                  #查看body标签内容
	<body>
	<p class="title"><b>The Dormouse's story</b></p>
	<p class="story">Once upon a time there were three little sisters; and their names were
	<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>,
	<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
	<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
	and they lived at the bottom of a well.</p>
	<p class="story">...</p>
	</body>
	>>> soup.p                             #查看段落信息
	<p class="title"><b>The Dormouse's story</b></p>
	>>> soup.p['class']                   #查看标签属性
	['title']
	>>> soup.p.get('class')               #也可以这样查看标签属性
	['title']
	>>> soup.p.text                        #查看段落文本
	"The Dormouse's story"
	>>> soup.p.contents                    #查看段落内容
	[<b>The Dormouse's story</b>]
	>>> soup.a
	<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>
	>>> soup.a.attrs                       #查看标签所有属性
	{'class': ['sister'], 'href': 'http://example.com/elsie', 'id': 'link1'}
	>>> soup.find_all('a')                #查找所有<a>标签
	[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>, <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>, <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
	>>> soup.find_all(['a', 'b'])        #同时查找<a>和<b>标签
	[<b>The Dormouse's story</b>, <a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>, <a class="sister" href="http://example.com/lacie" id="link2">Lacie</a>, <a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
	>>> import re
	>>> soup.find_all(href=re.compile("elsie"))
	                                      #查找href包含特定关键字的标签
	[<a class="sister" href="http://example.com/elsie" id="link1">Elsie</a>]
	>>> soup.find(id='link3')             #查找属性id='link3'的标签
	<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>
	>>> soup.find_all('a', id='link3')    #查找属性'link3'的a标签
	[<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>]
	>>> for link in soup.find_all('a'):
	    print(link.text,':',link.get('href'))
		
	Elsie : http://example.com/elsie
	Lacie : http://example.com/lacie
	Tillie : http://example.com/tillie
	>>> print(soup.get_text())                 #返回所有文本
	The Dormouse's story
	The Dormouse's story
	Once upon a time there were three little sisters; and their names were
	Elsie,Lacie and Tillie; and they lived at the bottom of a well.
	...
	>>> soup.a['id'] = 'test_link1'           #修改标签属性的值
	>>> soup.a
	<a class="sister" href="http://example.com/elsie" id="test_link1">Elsie</a>
	>>> soup.a.string.replace_with('test_Elsie') #修改标签文本
	'Elsie'
	>>> soup.a.string
	'test_Elsie'

	>>> for child in soup.body.children:     #遍历直接子标签
	    print(child)
	
	<p class="title"><b>The Dormouse's story</b></p>
	<p class="story">Once upon a time there were three little sisters; and their names were
	<a class="sister" href="http://example.com/elsie" id="test_link1">test_Elsie</a>,
	<a class="sister" href="http://example.com/lacie" id="link2">Lacie</a> and
	<a class="sister" href="http://example.com/tillie" id="link3">Tillie</a>;
	and they lived at the bottom of a well.</p>
	<p class="story">...</p>
	>>> test_doc = '<html><head></head><body><p></p><p></p></body></heml>'
	>>> s = BeautifulSoup(test_doc, 'lxml')
	>>> for child in s.html.children:        #遍历直接子标签
	    print(child)
		
	<head></head>
	<body><p></p><p></p></body>
	>>> for child in s.html.descendants:     #遍历子孙标签
	    print(child)
		
	<head></head>
	<body><p></p><p></p></body>
	<p></p>
	<p></p>
