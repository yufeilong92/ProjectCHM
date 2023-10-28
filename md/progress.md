# progress #

[**官网**](https://pypi.org/project/progress/ "官网")

# 安装 #
    pip install progress

### Bars ###
有7个进度条可供选择:



- Bar

- ChargingBar

- FillingSquaresBar

- FillingCirclesBar

- IncrementalBar

- PixelBar

- ShadyBar

要使用它们，只需给next即可前进，结束即可完成：

	from progress.bar import Bar
	
	bar = Bar('Processing', max=20)
	for i in range(20):
	    # Do some work
	    bar.next()
	bar.finish()
或使用此类的任何bar作为上下文管理器:

	from progress.bar import Bar
	
	with Bar('Processing', max=20) as bar:
	    for i in range(20):
	        # Do some work
	        bar.next()
结果将是如下所示的条形图:

	Processing |#############                   | 42/100
为了简化在迭代器中完成工作的常见情况，可以使用iter方法:

	for i in Bar('Processing').iter(it):
	    # Do some work
进度条非常可自定义，您可以更改其宽度、填充字符、后缀等:

	bar = Bar('Loading', fill='@', suffix='%(percent)d%%')
这将生成如下所示的条形图:

	Loading |@@@@@@@@@@@@@                   | 42%
您可以在消息和后缀中使用许多模板参数

|name|value|
|:---|:---|
|index|	current value|
|max|maximum value|
|remaining|	max - index|
|progress|	index / max|
|percent|	progress * 100|
|avg|simple moving average time per item (in seconds)|
|elapsed|elapsed time in seconds|
|elapsed_td|elapsed as a timedelta (useful for printing as a string)|
|eta|avg * remaining|
|eta_td|eta as a timedelta (useful for printing as a string)|

您可以创建自定义子类，而不是在安装时传递所有配置选项:

	class FancyBar(Bar):
	    message = 'Loading'
	    fill = '*'
	    suffix = '%(percent).1f%% - %(eta)ds'
您也可以覆盖任何参数或创建自己的参数:

	class SlowBar(Bar):
	    suffix = '%(remaining_hours)d hours remaining'
	    @property
	    def remaining_hours(self):
	        return self.eta // 3600
# Spinners #
对于步数未知的操作，可以使用微调器:

	from progress.spinner import Spinner
	
	spinner = Spinner('Loading ')
	while state != 'FINISHED':
	    # Do some work
	    spinner.next()
有5个预定义的微调器:



- Spinner



- PieSpinner




- MoonSpinner



- LineSpinner



- PixelSpinner