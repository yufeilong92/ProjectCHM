# TQDM #

[**官网**](https://pypi.org/project/tqdm/#files)
**tqdm**是 Python 进度条库，可以在 Python长循环中添加一个进度提示信息。用户只需要封装任意的迭代器，是一个快速、扩展性强的进度条工具库。
# 安装 #
    pip install tqdm

## 使用方法 ##
### 传入可迭代对象 ###
	import time
	from tqdm import *
	
	for i in tqdm(range(100)):
	    time.sleep(0.01)
### trange(i)：tqdm(range(i))的简单写法 ###
	for t in trange(100):
	    time.sleep(0.01)
### update()方法手动控制进度条更新的进度 ###
	with tqdm(total=200) as pbar:
	    for i in range(20):  # 总共更新 20 次
	        pbar.update(10)  # 每次更新步长为 10
	        time.sleep(1)
或者
	
	pbar = tqdm(total=200)
	
	for i in range (20):
	    pbar.update(10)
	    time.sleep(1)
	
	pbar.close()

### write()方法 ###

	pbar = trange(10)
	
	for i in pbar:
	    time.sleep(1)
	    if not (i % 3):
	        tqdm.write('Done task %i' %i)

### 通过set_description()和set_postfix()设置进度条显示信息 ###
	
	from random import random,randint
	
	with trange(10) as t:
	    for i in t:                
	        t.set_description("GEN %i"%i)  # 进度条左边显示信息        
	        t.set_postfix(loss=random(), gen=randint(1,999), str="h", lst=[1,2])  # 进度条右边显示信息
	        time.sleep(0.1)  


## 使用案例 ##

	import requests
	from tqdm import tqdm
	
	def downloadMp4(url ,path):
	    rep=requests.get(url,stream=path)
	
	    total=int(rep.headers.get('content-length',0))
	
	    with open (path,"wb")as file,tqdm(
	        desc=path,
	        total=total,
	        unit='iB',
	        unit_scale=True,
	        unit_divisor=1024
	    )as bar:
	        for data in rep.iter_content(chunk_size=1024):
	            size=file.write(data)
	            bar.update(size)
	    file.close()
	    bar.close()
	    rep.close()
	
	if __name__=="__main__":
	    url="地址"
	    path=r"地址
	    downloadMp4(url,"18.mp4")