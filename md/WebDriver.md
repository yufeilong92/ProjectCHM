# WebDriver #
[WebDriver ](https://www.selenium.dev/zh-cn/documentation/)以本地化方式驱动浏览器，就像用户在本地或使用 Selenium 服务器的远程机器上所做的那样，这标志着浏览器自动化的飞跃。

##安装命令
    pip install selenium
##使用案例
    from selenium import webdriver
    from selenium.webdriver.chrome.service import Service
    
    service = Service(executable_path="/path/to/chromedriver")
    driver = webdriver.Chrome(service=service)
##浏览器使用
|浏览器|支持操作系统|维护者|下载|问题追溯|
|:---|:---|:---|:---|:---|
|Chromium/Chrome|Windows/macOS/Linux|Google|[下载](https://chromedriver.chromium.org/downloads)|[Issues](https://bugs.chromium.org/p/chromedriver/issues/list)|
|Firefox|Windows/macOS/Linux|Mozilla|[下载](https://github.com/mozilla/geckodriver/releases)|[Issues](https://github.com/mozilla/geckodriver/issues)|
|Edge|Windows/macOS/Linux|Microsoft|[下载](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/)|[Issues](https://github.com/MicrosoftDocs/edge-developer/issues)|
|Internet Explorer|Windows|Selenium Project|[下载](https://www.selenium.dev/downloads/)|[Issues](https://github.com/SeleniumHQ/selenium/labels/D-IE)|
|Safari|macOS High Sierra and newer|Apple|内置|	[Issues](https://feedbackassistant.apple.com/)|

##浏览器使用案例
##Chrome
    from selenium import webdriver
    from selenium.webdriver import ChromeOptions
    
    #设置操作的网站
    web_url = "https://bbs.csdn.net"
    browser = webdriver.Chrome(executable_path=r"D:\chromedriver_win32\chromedriver\chromedriver.exe")
    #打开网页
    browser.get(web_url)

###Options
    options = ChromeOptions()
    driver = webdriver.Chrome(options=options)
###args 参数是启动浏览器时输入的浏览器命令行参数. 
    chrome_options = ChromeOptions()
    chrome_options.add_argument("--headless=new")
###将 detach 参数设置为true将在驱动过程结束后保持浏览器的打开状态.
    chrome_options = ChromeOptions()
    chrome_options.add_experimental_option("detach", True)
##Firefox
    from selenium import webdriver
     
    # 创建浏览器对象
    driver = webdriver.Firefox()
     
    # 访问网页
    driver.get("https://www.example.com")
###Options 
    options = FirefoxOptions()
    driver = webdriver.Firefox(options=options)
###Arguments
args参数用于启动浏览器时使用的命令行开关列表。

常用的参数包括-headless和“-profile”、“/path/to/profile”

    options=Options()
    options.add_argument("-profile")
    options.add_argument("/path/to/profile")
###Profiles
有几种方法可以使用Firefox配置文件

	from selenium.webdriver.firefox.options import Options
	from selenium.webdriver.firefox.firefox_profile import FirefoxProfile
	options=Options()
	firefox_profile = FirefoxProfile()
	firefox_profile.set_preference("javascript.enabled", False)
	options.profile = firefox_profile
###设置

    path = os.path.abspath("tests/extensions/webextensions-selenium-example.xpi")
    driver.install_addon(path)

###卸载

    path = os.path.abspath("tests/extensions/webextensions-selenium-example.xpi")
    id = driver.install_addon(path)
    driver.uninstall_addon(id)

###未签名的安装

    path = os.path.abspath("tests/extensions/webextensions-selenium-example/")
    driver.install_addon(path, temporary=True)
##EDGE
###选项

    options = EdgeOptions()
    driver = webdriver.Edge(options=options)
###Arguments

    options = EdgeOptions()
    options.add_argument("--headless=new")
##IE 
###Options
    options = InternetExplorerOptions()
    driver = webdriver.Ie(options=options)
###fileUploadDialogTimeout
在某些环境中, 当打开文件上传对话框时, Internet Explorer可能会超时. IEDriver的默认超时为1000毫秒, 但您可以使用fileUploadDialogTimeout功能来增加超时时间.
	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.file_upload_dialog_timeout = 2000
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
###ensureCleanSession
设置为 true时, 此功能将清除InternetExplorer所有正在运行实例的 缓存, 浏览器历史记录和Cookies (包括手动启动或由驱动程序启动的实例) . 默认情况下，此设置为 false.

使用此功能将导致启动浏览器时性能下降, 因为驱动程序将等待直到缓存清除后再启动IE浏览器.

此功能接受一个布尔值作为参数.

	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.ensure_clean_session = True
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
  
###ignoreZoomSetting
InternetExplorer驱动程序期望浏览器的缩放级别为100%, 否则驱动程序将可能抛出异常. 通过将 ignoreZoomSetting 设置为 true, 可以禁用此默认行为.

此功能接受一个布尔值作为参数.

	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.ignore_zoom_level = True
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
  
###ignoreProtectedModeSettings
启动新的IE会话时是否跳过 保护模式 检查.

如果未设置, 并且所有区域的 保护模式 设置都不同, 则驱动程序将可能引发异常.

如果将功能设置为 true, 则测试可能会变得不稳定, 无响应, 或者浏览器可能会挂起. 但是, 到目前为止, 这仍然是第二好的选择, 并且第一选择应该 始终 是手动实际设置每个区域的保护模式设置. 如果用户正在使用此属性， 则只会给予 “尽力而为” 的支持.

此功能接受一个布尔值作为参数.
	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.ignore_protected_mode_settings = True
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
###silent
设置为 true时, 此功能将禁止IEDriverServer的诊断输出.

此功能接受一个布尔值作为参数.  
	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.set_capability("silent", True)
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
###IE 命令行选项
Internet Explorer包含几个命令行选项, 使您可以进行故障排除和配置浏览器.

下面介绍了一些受支持的命令行选项

-private : 用于在私有浏览模式下启动IE. 这适用于IE 8和更高版本.

-k : 在kiosk模式下启动Internet Explorer. 浏览器在一个最大化的窗口中打开, 该窗口不显示地址栏, 导航按钮或状态栏.

-extoff : 在无附加模式下启动IE. 此选项专门用于解决浏览器加载项问题. 在IE 7和更高版本中均可使用.

注意: forceCreateProcessApi 应该启用命令行参数才能正常工作.  
	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.add_argument('-private')
	options.force_create_process_api = True
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
###forceCreateProcessApi
强制使用CreateProcess API启动Internet Explorer. 默认值为false.

对于IE 8及更高版本, 此选项要求将 “TabProcGrowth” 注册表值设置为0.  
	from selenium import webdriver
	
	options = webdriver.IeOptions()
	options.force_create_process_api = True
	driver = webdriver.Ie(options=options)
	
	driver.get("http://www.google.com")
	
	driver.quit()
  



##简单案例：
	# 驱动会话
	driver = webdriver.Chrome()
    # 导航 到一个网页.
 	driver.get("https://www.selenium.dev/selenium/web/web-form.html")
	# 浏览器的信息 , 包括窗口句柄、浏览器尺寸/位置、cookie、警报等.
    title = driver.title
	# 建立等待策略
  	driver.implicitly_wait(0.5)
	# 查找元素 
	text_box = driver.find_element(by=By.NAME, value="my-text")
    submit_button = driver.find_element(by=By.CSS_SELECTOR, value="button")
	#  操作元素
    text_box.send_keys("Selenium")
    submit_button.click()
	#  获取元素信息
  	value = message.text
	#  结束会话
	driver.quit()
##使用 findElement* 查找单个元素
##Before
	driver.findElementByClassName("className");
	driver.findElementByCssSelector(".className");
	driver.findElementById("elementId");
	driver.findElementByLinkText("linkText");
	driver.findElementByName("elementName");
	driver.findElementByPartialLinkText("partialText");
	driver.findElementByTagName("elementTagName");
	driver.findElementByXPath("xPath");
##After
	driver.findElement(By.className("className"));
	driver.findElement(By.cssSelector(".className"));
	driver.findElement(By.id("elementId"));
	driver.findElement(By.linkText("linkText"));
	driver.findElement(By.name("elementName"));
	driver.findElement(By.partialLinkText("partialText"));
	driver.findElement(By.tagName("elementTagName"));
	driver.findElement(By.xpath("xPath"));
##使用 findElements* 查找多个元素
##Before
	driver.findElementsByClassName("className");
	driver.findElementsByCssSelector(".className");
	driver.findElementsById("elementId");
	driver.findElementsByLinkText("linkText");
	driver.findElementsByName("elementName");
	driver.findElementsByPartialLinkText("partialText");
	driver.findElementsByTagName("elementTagName");
	driver.findElementsByXPath("xPath");
##After
	driver.findElements(By.className("className"));
	driver.findElements(By.cssSelector(".className"));
	driver.findElements(By.id("elementId"));
	driver.findElements(By.linkText("linkText"));
	driver.findElements(By.name("elementName"));
	driver.findElements(By.partialLinkText("partialText"));
	driver.findElements(By.tagName("elementTagName"));
	driver.findElements(By.xpath("xPath"));

##查询网络元素
根据提供的定位值定位元素.
使用Selenium最基本的一个方面是获得要使用的元素引用。Selenium提供了许多内置的定位器策略来唯一地识别元素。有很多方法可以在非常高级的场景中使用定位器。出于本文档的目的，让我们考虑以下HTML片段：

	<ol id="vegetables">
	 <li class="potatoes">
	 <li class="onions">
	 <li class="tomatoes"><span>Tomato is a Vegetable</span>
	</ol>
	<ul id="fruits">
	  <li class="bananas">
	  <li class="apples">
	  <li class="tomatoes"><span>Tomato is a Fruit</span>
	</ul>
###第一个匹配元素

许多定位器将与页面上的多个元素相匹配。单数find元素方法将返回对给定上下文中找到的第一个元素的引用
####查找整个DOM
当在驱动程序实例上调用find元素方法时，它会返回对DOM中与所提供的定位器匹配的第一个元素的引用。此值可以存储并用于将来的元素操作。在我们上面的示例HTML中，有两个元素的类名为“番茄”，因此此方法将返回“蔬菜”列表中的元素。

	vegetable = driver.find_element(By.CLASS_NAME, "tomatoes")

####查找DOM的子集
与其在整个DOM中找到唯一的定位器，不如将搜索范围缩小到另一个已定位元素的范围。在上面的例子中，有两个元素的类名为“tomatos”，而要获得第二个元素的引用则有点困难。
一种解决方案是定位具有唯一属性的元素，该元素是所需元素的祖先，而不是不需要的元素的祖先。然后在该对象上调用find元素：

	fruits = driver.find_element(By.ID, "fruits")
	fruit = fruits.find_element(By.CLASS_NAME,"tomatoes")


####优化定位器

嵌套查找可能不是最有效的定位策略，因为它需要向浏览器发出两个单独的命令。

为了稍微提高性能，我们可以使用CSS或XPath在一个命令中找到这个元素。请参阅我们鼓励的测试实践部分中的定位器策略建议。

对于本例，我们将使用CSS选择器：

	fruit = driver.find_element(By.CSS_SELECTOR,"#fruits .tomatoes")

####所有匹配元素

有几个用例需要获取对匹配定位器的所有元素的引用，而不仅仅是第一个。复数find元素方法返回元素引用的集合。如果没有匹配项，则返回一个空列表。在这种情况下，对所有水果和蔬菜列表项的引用将在集合中返回。

	plants = driver.find_elements(By.TAG_NAME, "li")
####获取元素

通常，您得到一个元素集合，但想要使用特定的元素，这意味着您需要迭代该集合并确定您想要的元素。  
	from selenium import webdriver
	from selenium.webdriver.common.by import By
	
	driver = webdriver.Firefox()
	
	    # Navigate to Url
	driver.get("https://www.example.com")
	
	    # Get all the elements available with tag name 'p'
	elements = driver.find_elements(By.TAG_NAME, 'p')
	
	for e in elements:
	    print(e.text)
####从元素中查找元素

它用于在父元素的上下文中查找匹配的子WebElement的列表。为了实现这一点，父WebElement与“findElements”链接以访问子元素
	from selenium import webdriver
	from selenium.webdriver.common.by import By
	
	driver = webdriver.Chrome()
	driver.get("https://www.example.com")
	
	    # Get element with tag name 'div'
	element = driver.find_element(By.TAG_NAME, 'div')
	
	    # Get all the elements available with tag name 'p'
	elements = element.find_elements(By.TAG_NAME, 'p')
	for e in elements:
	    print(e.text)
####获取活动元素

它用于跟踪（或）查找在当前浏览上下文中具有焦点的DOM元素。
	 from selenium import webdriver
	 from selenium.webdriver.common.by import By
	
	 driver = webdriver.Chrome()
	 driver.get("https://www.google.com")
	 driver.find_element(By.CSS_SELECTOR, '[name="q"]').send_keys("webElement")
	
	   # Get attribute of current active element
	 attr = driver.switch_to.active_element.get_attribute("title")
	 print(attr)
##Web元素交互
用于操纵表单的高级指令集.
仅有五种基本命令可用于元素的操作:

[点击](https://w3c.github.io/webdriver/#element-click) (适用于任何元素)

[发送键位](https://w3c.github.io/webdriver/#element-send-keys) (仅适用于文本字段和内容可编辑元素)

[清除](https://w3c.github.io/webdriver/#element-send-keys)(仅适用于文本字段和内容可编辑元素)

提交 (仅适用于表单元素)
选择 (参见 [选择列表元素](https://www.selenium.dev/zh-cn/documentation/webdriver/support_features/select_lists/))


##**定位器**
在 WebDriver 中有 8 种不同的内置元素定位策略：

|定位器 Locator|描述|
|:---|:---|
|class name|定位class属性与搜索值匹配的元素（不允许使用复合类名）|
|css selector|定位 CSS 选择器匹配的元素|
|id|定位 id 属性与搜索值匹配的元素|
|name|定位 name 属性与搜索值匹配的元素|
|link text|定位link text可视文本与搜索值完全匹配的锚元素|
|partial link text|定位link text可视文本部分与搜索值部分匹配的锚点元素。如果匹配多个元素，则只选择第一个元素。|
|tag name|定位标签名称与搜索值匹配的元素|
|xpath|定位与 XPath 表达式匹配的元素|
###创建定位器

要使用Selenium处理web元素，我们需要首先在网页上找到它。Selenium为我们提供了上述方法，使用这些方法我们可以在页面上定位元素。为了理解和创建定位器，我们将使用以下HTML片段。

	<html>
	<body>
	<style>
	.information {
	  background-color: white;
	  color: black;
	  padding: 10px;
	}
	</style>
	<h2>Contact Selenium</h2>
	
	<form action="/action_page.php">
	  <input type="radio" name="gender" value="m" />Male &nbsp;
	  <input type="radio" name="gender" value="f" />Female <br>
	  <br>
	  <label for="fname">First name:</label><br>
	  <input class="information" type="text" id="fname" name="fname" value="Jane"><br><br>
	  <label for="lname">Last name:</label><br>
	  <input class="information" type="text" id="lname" name="lname" value="Doe"><br><br>
	  <label for="newsletter">Newsletter:</label>
	  <input type="checkbox" name="newsletter" value="1" /><br><br>
	  <input type="submit" value="Submit">
	</form> 
	
	<p>To know more about Selenium, visit the official page 
	<a href ="www.selenium.dev">Selenium Official Page</a> 
	</p>
	
	</body>
	</html>
###class name

HTML页面web元素可以具有属性类。我们可以在上面显示的HTML片段中看到一个示例。我们可以使用Selenium中提供的类名定位器来识别这些元素。

    driver = webdriver.Chrome()
	driver.find_element(By.CLASS_NAME, "information")
###css选择器
CSS是用于设计HTML页面样式的语言。我们可以使用css选择器定位器策略来识别页面上的元素。如果元素有一个id，我们将定位器创建为css＝#id。否则，我们遵循的格式是css=[属性=值]。让我们看看上面HTML片段中的一个例子。我们将使用css为“名字”文本框创建定位器。

    driver = webdriver.Chrome()
	driver.find_element(By.CSS_SELECTOR, "#fname")
###ID
我们可以使用网页中元素的ID属性来定位它。通常，ID属性对于网页上的元素应该是唯一的。我们将使用它来识别姓氏字段。

    driver = webdriver.Chrome()
	driver.find_element(By.ID, "lname")
###name
我们可以使用网页中元素的NAME属性来定位它。通常，NAME属性对于网页上的元素应该是唯一的。我们将使用它来识别时事通讯复选框。

    driver = webdriver.Chrome()
	driver.find_element(By.NAME, "newsletter")
###link text
如果我们想要定位的元素是链接，我们可以使用链接文本定位器在网页上识别它。链接文本是链接显示的文本。在共享的HTML片段中，我们有一个可用的链接，让我们看看如何定位它。

    driver = webdriver.Chrome()
	driver.find_element(By.LINK_TEXT, "Selenium Official Page")
###partial link text
如果我们要定位的元素是链接，我们可以使用部分链接文本定位器在网页上识别它。链接文本是链接显示的文本。我们可以将部分文本作为值传递。在共享的HTML片段中，我们有一个可用的链接，让我们看看如何定位它。

    driver = webdriver.Chrome()
	driver.find_element(By.PARTIAL_LINK_TEXT, "Official Page")

###tag name
我们可以使用HTML标签本身作为定位器来识别页面上的web元素。从上面共享的HTML片段中，让我们使用其HTML标记“a”来识别链接。

    driver = webdriver.Chrome()
	driver.find_element(By.TAG_NAME, "a")
###xpath
HTML文档可以被视为XML文档，然后我们可以使用xpath，这将是到达感兴趣的元素以定位元素所经过的路径。XPath可以是绝对的XPath，它是从文档的根目录创建的。示例-/html/form/input[1]。这将返回阳性单选按钮。或者xpath可以是相对的。示例-//输入[@name='name']。这将返回名字文本框。让我们使用xpath为女性单选按钮创建定位器。

    driver = webdriver.Chrome()
	driver.find_element(By.XPATH, "//input[@value='f']")
##关于网络元素的信息
###是否显示
此方法用于检查连接的元素是否正确显示在网页上. 返回一个 Boolean 值， 如果连接的元素显示在当前的浏览器上下文中，则为True，否则返回false。

此功能于W3C规范中提及， 但由于无法覆盖所有潜在条件而无法定义。 因此，Selenium不能期望驱动程序直接实现这种功能，现在依赖于直接执行大量JavaScript函数。 这个函数对一个元素的性质和在树中的关系做了许多近似的判断，以返回一个值。

	# Navigate to the url
	driver.get("https://www.selenium.dev/selenium/web/inputs.html")
	
	# Get boolean value for is element display
	is_email_visible = driver.find_element(By.NAME, "email_input").is_displayed()

###是否启用
此方法用于检查所连接的元素在网页上是启用还是禁用状态。 返回一个布尔值，如果在当前浏览上下文中是 启用 状态，则返回 true，否则返回 false。

	    # Navigate to url
	driver.get("http://www.google.com")
	
	    # Returns true if element is enabled else returns false
	value = driver.find_element(By.NAME, 'btnK').is_enabled()

###点击按钮:

	    # 这不会工作
	driver.find_element(By.TAG_NAME, 'button').click()
###是否被选定
此方法确认相关的元素是否 已选定，常用于复选框、单选框、输入框和选择元素中。

该方法返回一个布尔值，如果在当前浏览上下文中 选择了 引用的元素，则返回 True，否则返回 False。

	# Navigate to url
	driver.get("https://the-internet.herokuapp.com/checkboxes")
	
	# Returns true if element is checked else returns false
	value = driver.find_element(By.CSS_SELECTOR, "input[type='checkbox']:first-of-type").is_selected()
###获取元素标签名 
此方法用于获取在当前浏览上下文中具有焦点的被引用元素的TagName。

	# Navigate to url
	driver.get("https://www.example.com")
	
	# Returns TagName of the element
	attr = driver.find_element(By.CSS_SELECTOR, "h1").tag_name

###使用 name 或 id
如果您的 frame 或 iframe 具有 id 或 name 属性，则可以使用该属性。如果名称或 id 在页面上不是唯一的， 那么将切换到找到的第一个。
	
	    # 通过 id 切换框架
	driver.switch_to.frame('buttonframe')
	
	    # 单击按钮
	driver.find_element(By.TAG_NAME, 'button').click()
###位置和大小 
用于获取参照元素的尺寸和坐标。

提取的数据主体包含以下详细信息：

元素左上角的X轴位置
元素左上角的y轴位置
元素的高度
元素的宽度

	# Navigate to url
	driver.get("https://www.example.com")
	
	# Returns height, width, x and y coordinates referenced element
	res = driver.find_element(By.CSS_SELECTOR, "h1").rect
###获取元素CSS值
获取当前浏览上下文中元素的特定计算样式属性的值。

	# Navigate to Url
	driver.get('https://www.example.com')
	
	# Retrieves the computed style property 'color' of linktext
	cssValue = driver.find_element(By.LINK_TEXT, "More information...").value_of_css_property('color')
###文本内容
获取特定元素渲染后的文本内容。

	# Navigate to url
	driver.get("https://www.example.com")
	
	# Retrieves the text of the element
	text = driver.find_element(By.CSS_SELECTOR, "h1").text
###获取特性或属性
获取与 DOM 属性关联的运行时的值。 它返回与该元素的 DOM 特性或属性关联的数据。

	# Navigate to the url
	driver.get("https://www.selenium.dev/selenium/web/inputs.html")
	
	# Identify the email text box
	email_txt = driver.find_element(By.NAME, "email_input")
	
	# Fetch the value property associated with the textbox
	value_info = email_txt.get_attribute("value")

#浏览器交互
## 获取浏览器信息
###获取标题 
从浏览器中读取当前页面的标题:

	driver.title
###获取当前 URL
您可以从浏览器的地址栏读取当前的 URL，使用:

	driver.current_url
###打开网站
启动浏览器后你要做的第一件事就是打开你的网站。这可以通过一行代码实现:

	driver.get("https://selenium.dev")
###后退
按下浏览器的后退按钮:

	driver.back()
###前进
按下浏览器的前进键:

	driver.forward()
###刷新
刷新当前页面

	driver.refresh()
###Alerts 警告框
其中最基本的称为警告框, 它显示一条自定义消息, 以及一个用于关闭该警告的按钮, 在大多数浏览器中标记为"确定"(OK). 在大多数浏览器中, 也可以通过按"关闭"(close)按钮将其关闭, 但这始终与“确定”按钮具有相同的作用. 查看样例警告框.

WebDriver可以从弹窗获取文本并接受或关闭这些警告.

	# Click the link to activate the alert
	driver.find_element(By.LINK_TEXT, "See an example alert").click()
	
	# Wait for the alert to be displayed and store it in a variable
	alert = wait.until(expected_conditions.alert_is_present())
	
	# Store the alert text in a variable
	text = alert.text
	
	# Press the OK button
	alert.accept()
###Confirm 确认框
确认框类似于警告框, 不同之处在于用户还可以选择取消消息. 查看样例确认框.

此示例还呈现了警告的另一种实现:
	
	# Click the link to activate the alert
	driver.find_element(By.LINK_TEXT, "See a sample confirm").click()
	
	# Wait for the alert to be displayed
	wait.until(expected_conditions.alert_is_present())
	
	# Store the alert in a variable for reuse
	alert = driver.switch_to.alert
	
	# Store the alert text in a variable
	text = alert.text
	
	# Press the Cancel button
	alert.dismiss()
###Prompt 提示框
提示框与确认框相似, 不同之处在于它们还包括文本输入. 与处理表单元素类似, 您可以使用WebDriver的sendKeys来填写响应. 这将完全替换占位符文本. 按下取消按钮将不会提交任何文本. 查看样例提示框.
	
	# Click the link to activate the alert
	driver.find_element(By.LINK_TEXT, "See a sample prompt").click()
	
	# Wait for the alert to be displayed
	wait.until(expected_conditions.alert_is_present())
	
	# Store the alert in a variable for reuse
	alert = Alert(driver)
	
	# Type your message
	alert.send_keys("Selenium")
	
	# Press the OK button
	alert.accept()
###添加 Cookie

	from selenium import webdriver
	
	driver = webdriver.Chrome()
	
	driver.get("http://www.example.com")
	
	# Adds the cookie into current browser context
	driver.add_cookie({"name": "key", "value": "value"})
###获取命名的 Cookie
此方法返回与cookie名称匹配的序列化cookie数据中所有关联的cookie.

	from selenium import webdriver
	
	driver = webdriver.Chrome()
	
	# Navigate to url
	driver.get("http://www.example.com")
	
	# Adds the cookie into current browser context
	driver.add_cookie({"name": "foo", "value": "bar"})
	
	# Get cookie details with named cookie 'foo'
	print(driver.get_cookie("foo"))
  
###获取全部 Cookies
此方法会针对当前访问上下文返回“成功的序列化cookie数据”. 如果浏览器不再可用, 则返回错误.
	from selenium import webdriver
	
	driver = webdriver.Chrome()
	
	# Navigate to url
	driver.get("http://www.example.com")
	
	driver.add_cookie({"name": "test1", "value": "cookie1"})
	driver.add_cookie({"name": "test2", "value": "cookie2"})
	
	# Get all available cookies
	print(driver.get_cookies())
###删除 Cookie
此方法删除与提供的cookie名称匹配的cookie数据.

	from selenium import webdriver
	driver = webdriver.Chrome()
	
	# Navigate to url
	driver.get("http://www.example.com")
	driver.add_cookie({"name": "test1", "value": "cookie1"})
	driver.add_cookie({"name": "test2", "value": "cookie2"})
	
	# Delete a cookie with name 'test1'
	driver.delete_cookie("test1")
  
###删除所有 Cookies
此方法删除当前访问上下文的所有cookie.

	from selenium import webdriver
	driver = webdriver.Chrome()
	
	# Navigate to url
	driver.get("http://www.example.com")
	driver.add_cookie({"name": "test1", "value": "cookie1"})
	driver.add_cookie({"name": "test2", "value": "cookie2"})
	
	#  Deletes all cookies
	driver.delete_all_cookies()
##窗口

###窗口和标签页
WebDriver 没有区分窗口和标签页。如果你的站点打开了一个新标签页或窗口，Selenium 将允许您使用窗口句柄来处理它。 每个窗口都有一个唯一的标识符，该标识符在单个会话中保持持久性。你可以使用以下方法获得当前窗口的窗口句柄:

	driver.current_window_handle
###切换窗口或标签页
单击在 <a href=“https://seleniumhq.github.io"target="_blank”>新窗口 中打开链接， 则屏幕会聚焦在新窗口或新标签页上，但 WebDriver 不知道操作系统认为哪个窗口是活动的。 要使用新窗口，您需要切换到它。 如果只有两个选项卡或窗口被打开，并且你知道从哪个窗口开始， 则你可以遍历 WebDriver， 通过排除法可以看到两个窗口或选项卡，然后切换到你需要的窗口或选项卡。

不过，Selenium 4 提供了一个新的 api NewWindow 它创建一个新选项卡 (或) 新窗口并自动切换到它。

	from selenium import webdriver
	from selenium.webdriver.support.ui import WebDriverWait
	from selenium.webdriver.support import expected_conditions as EC
	
	    # 启动驱动程序
	with webdriver.Firefox() as driver:
	    # 打开网址
	driver.get("https://seleniumhq.github.io")
	
	    # 设置等待
	    wait = WebDriverWait(driver, 10)
	
	    # 存储原始窗口的 ID
	    original_window = driver.current_window_handle
	
	    # 检查一下，我们还没有打开其他的窗口
	    assert len(driver.window_handles) == 1
	
	    # 单击在新窗口中打开的链接
	    driver.find_element(By.LINK_TEXT, "new window").click()
	
	    # 等待新窗口或标签页
	    wait.until(EC.number_of_windows_to_be(2))
	
	    # 循环执行，直到找到一个新的窗口句柄
	    for window_handle in driver.window_handles:
	        if window_handle != original_window:
	            driver.switch_to.window(window_handle)
	            break
	
	    # 等待新标签页完成加载内容
	    wait.until(EC.title_is("SeleniumHQ Browser Automation"))
###创建新窗口(或)新标签页并且切换
创建一个新窗口 (或) 标签页，屏幕焦点将聚焦在新窗口或标签在上。您不需要切换到新窗口 (或) 标签页。如果除了新窗口之外， 您打开了两个以上的窗口 (或) 标签页，您可以通过遍历 WebDriver 看到两个窗口或选项卡，并切换到非原始窗口。

	    # 打开新标签页并切换到新标签页
	driver.switch_to.new_window('tab')
	
	    # 打开一个新窗口并切换到新窗口
	driver.switch_to.new_window('window')
###关闭窗口或标签页
当你完成了一个窗口或标签页的工作时，_并且_它不是浏览器中最后一个打开的窗口或标签页时，你应该关闭它并切换回你之前使用的窗口。 假设您遵循了前一节中的代码示例，您将把前一个窗口句柄存储在一个变量中。把这些放在一起，你会得到:

	    #关闭标签页或窗口
	driver.close()
	
	    #切回到之前的标签页或窗口
	driver.switch_to.window(original_window)
如果在关闭一个窗口后忘记切换回另一个窗口句柄，WebDriver 将在当前关闭的页面上执行，并触发一个 No Such Window Exception 无此窗口异常。必须切换回有效的窗口句柄才能继续执行。
###在会话结束时退出浏览器
当你完成了浏览器会话，你应该调用 quit 退出，而不是 close 关闭:

	driver.quit()
退出将会


- 关闭所有与 WebDriver 会话相关的窗口和选项卡


- 结束浏览器进程


- 结束后台驱动进程


- 通知 Selenium Grid 浏览器不再使用，以便可以由另一个会话使用它(如果您正在使用 Selenium Grid)

调用 quit() 失败将留下额外的后台进程和端口运行在机器上，这可能在以后导致一些问题。

有的测试框架提供了一些方法和注释，您可以在测试结束时放入 teardown() 方法中。
	
	    # unittest teardown
	    # https://docs.python.org/3/library/unittest.html?highlight=teardown#unittest.TestCase.tearDown
	def tearDown(self):
	self.driver.quit()
如果不在测试上下文中运行 WebDriver，您可以考虑使用 try / finally，这是大多数语言都提供的， 这样一个异常处理仍然可以清理 WebDriver 会话。
	
	try:
	    #WebDriver 代码…
	finally:
	driver.quit()
Python 的 WebDriver 现在支持 Python 上下文管理器，当使用 with 关键字时，可以在执行结束时自动退出驱动程序。
	with webdriver.Firefox() as driver:
	  # WebDriver 代码…
	
	# 在此缩进位置后 WebDriver 会自动退出
##窗口管理
屏幕分辨率会影响 web 应用程序的呈现方式，因此 WebDriver 提供了移动和调整浏览器窗口大小的机制。
###获取窗口大小
获取浏览器窗口的大小(以像素为单位)。
	
	    # 分别获取每个尺寸
	width = driver.get_window_size().get("width")
	height = driver.get_window_size().get("height")
	
	    # 或者存储尺寸并在以后查询它们
	size = driver.get_window_size()
	width1 = size.get("width")
	height1 = size.get("height")
###设置窗口大小
恢复窗口并设置窗口大小。

	driver.set_window_size(1024, 768)

###得到窗口的位置 
获取浏览器窗口左上角的坐标。

	    # 分别获取每个尺寸
	x = driver.get_window_position().get('x')
	y = driver.get_window_position().get('y')
	
	    # 或者存储尺寸并在以后查询它们
	position = driver.get_window_position()
	x1 = position.get('x')
	y1 = position.get('y')

###设置窗口位置
将窗口移动到设定的位置。
	
	    # 将窗口移动到主显示器的左上角
	driver.set_window_position(0, 0)
###最大化窗口
扩大窗口。对于大多数操作系统，窗口将填满屏幕，而不会阻挡操作系统自己的菜单和工具栏。

	driver.maximize_window()
###最小化窗口 
最小化当前浏览上下文的窗口. 这种命令的精准行为将作用于各个特定的窗口管理器.

最小化窗口通常将窗口隐藏在系统托盘中.

注意: 此功能适用于Selenium 4以及更高版本

	driver.minimize_window()
###全屏窗口
填充整个屏幕，类似于在大多数浏览器中按下 F11。

	driver.fullscreen_window()

###屏幕截图
用于捕获当前浏览上下文的屏幕截图. WebDriver端点 屏幕截图 返回以Base64格式编码的屏幕截图.

	from selenium import webdriver
	
	driver = webdriver.Chrome()
	
	    # Navigate to url
	driver.get("http://www.example.com")
	
	    # Returns and base64 encoded string into image
	driver.save_screenshot('./image.png')
	
	driver.quit()
###元素屏幕截图
用于捕获当前浏览上下文的元素的屏幕截图. WebDriver端点 屏幕截图 返回以Base64格式编码的屏幕截图

	from selenium import webdriver
	from selenium.webdriver.common.by import By
	
	driver = webdriver.Chrome()
	
	    # Navigate to url
	driver.get("http://www.example.com")
	
	ele = driver.find_element(By.CSS_SELECTOR, 'h1')
	
	    # Returns and base64 encoded string into image
	ele.screenshot('./image.png')
	
	driver.quit()
###执行脚本
在当前frame或者窗口的上下文中，执行JavaScript代码片段.
	
	    # Stores the header element
	header = driver.find_element(By.CSS_SELECTOR, "h1")
	
	    # Executing JavaScript to capture innerText of header element
	driver.execute_script('return arguments[0].innerText', header)

###打印页面
打印当前浏览器内的页面

注意: 此功能需要无头模式下的Chromium浏览器
	
	from selenium.webdriver.common.print_page_options import PrintOptions
	
	    print_options = PrintOptions()
	    print_options.page_ranges = ['1-2']
	
	    driver.get("printPage.html")
	
	    base64code = driver.print_page(print_options)

###点击并按住

此方法将鼠标移动到元素的中心与按下鼠标左键相结合。这对于聚焦特定元素很有用

    clickable = driver.find_element(By.ID, "clickable")
    ActionChains(driver)\
        .click_and_hold(clickable)\
        .perform()

###点击并释放
此方法将移动到元素的中心与按住并释放鼠标左键相结合。这也被称为“点击”：

    clickable = driver.find_element(By.ID, "click")
    ActionChains(driver)\
        .click(clickable)\
        .perform()

###上下文单击
这种方法将移动到元素的中心与按下和释放鼠标右键（按钮2）相结合。这也被称为“右键单击”：

    clickable = driver.find_element(By.ID, "clickable")
    ActionChains(driver)\
        .context_click(clickable)\
        .perform()

###后退单击
没有方便的方法，只是按下并释放鼠标按钮3

    action = ActionBuilder(driver)
    action.pointer_action.pointer_down(MouseButton.BACK)
    action.pointer_action.pointer_up(MouseButton.BACK)
    action.perform()

###向前单击
没有方便的方法，只是按下并释放鼠标按钮4

    action = ActionBuilder(driver)
    action.pointer_action.pointer_down(MouseButton.FORWARD)
    action.pointer_action.pointer_up(MouseButton.FORWARD)
    action.perform()

###双击
这种方法将移动到元素的中心与按下和释放鼠标左键两次相结合。

    clickable = driver.find_element(By.ID, "clickable")
    ActionChains(driver)\
        .double_click(clickable)\
        .perform()

###移动到元素
此方法将鼠标移动到元素的视图中心点。这也被称为“悬停”。请注意，元素必须在视口中，否则命令将出错。

    hoverable = driver.find_element(By.ID, "hover")
    ActionChains(driver)\
        .move_to_element(hoverable)\
        .perform()

##按偏移量移动
这些方法首先将鼠标移动到指定的原点，然后移动所提供偏移中的像素数。请注意，鼠标的位置必须在视口中，否则命令将出错。
###与元素的偏移
此方法将鼠标移动到图元的视图中心点，然后按提供的偏移量移动。

    mouse_tracker = driver.find_element(By.ID, "mouse-tracker")
    ActionChains(driver)\
        .move_to_element_with_offset(mouse_tracker, 8, 0)\
        .perform()

###与视口的偏移
此方法将鼠标从当前视口的左上角移动所提供的偏移量。

    action = ActionBuilder(driver)
    action.pointer_action.move_to_location(8, 0)
    action.perform()

###与当前指针位置的偏移
此方法将鼠标从当前位置移动用户提供的偏移量。如果之前没有移动过鼠标，则该位置将位于视口的左上角。请注意，当页面滚动时，指针位置不会改变。
请注意，第一个参数X指定在为正数时向右移动，而第二个参数Y指定在为负数时向下移动。因此，moveByOffset（30，-10）从当前鼠标位置向右移动30，向上移动10。

    ActionChains(driver)\
        .move_by_offset( 13, 15)\
        .perform()

###在元素上拖放
该方法首先在源元素上执行点击并按住，移动到目标元素的位置，然后释放鼠标。

    draggable = driver.find_element(By.ID, "draggable")
    droppable = driver.find_element(By.ID, "droppable")
    ActionChains(driver)\
        .drag_and_drop(draggable, droppable)\
        .perform()

###按偏移拖放
此方法首先在源元素上单击并按住，移动到给定的偏移量，然后释放鼠标

    draggable = driver.find_element(By.ID, "draggable")
    start = draggable.location
    finish = driver.find_element(By.ID, "droppable").location
    ActionChains(driver)\
        .drag_and_drop_by_offset(draggable, finish['x'] - start['x'], finish['y'] - start['y'])\
        .perform()