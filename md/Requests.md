# Requests #
首先，requests 库是 Python 的一个第三方库，不是自带的。所以我们需要额外安装。

在这之前需要你先安装好 Python3 环境，如 Python 3.6 版本，如若没有安装可以参考：https://cuiqingcai.com/5059.html。
## 安装 ##
    pip install requests
## 使用 ##
### GET请求 ###
    import requests  
    
    r = requests.get('https://static1.scrape.cuiqingcai.com/')  
    print(r.text)

参数

	import requests  
	
	data = {  
	'name': 'germey',  
	'age': 25
	}  
	r = requests.get('http://httpbin.org/get', params=data)  
	print(r.text)
响应
	import requests  
	
	r = requests.get('http://httpbin.org/get')  
	print(type(r.text))  
	print(r.json())  
	print(type(r.json()))


### POST 请求 ###

	import requests
	
	data = {'name': 'germey', 'age': '25'}
	r = requests.post("http://httpbin.org/post", data=data)
	print(r.text)
#### 响应 ####
发送请求后，得到的自然就是响应，即 Response。

在上面的实例中，我们使用 text 和 content 获取了响应的内容。此外，还有很多属性和方法可以用来获取其他信息，比如状态码、响应头、Cookies 等。示例如下：
	import requests
	
	r = requests.get('https://static1.scrape.cuiqingcai.com/')
	print(type(r.status_code), r.status_code)
	print(type(r.headers), r.headers)
	print(type(r.cookies), r.cookies)
	print(type(r.url), r.url)
	print(type(r.history), r.history)
