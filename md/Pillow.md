[Pillow](https://python-pillow.org/)

在Python的图像处理领域，Pillow是一个强大而广泛使用的第三方库。它提供了丰富的图像处理功能，包括打开、保存、调整大小、裁剪、旋转等操作。本文将详细介绍Pillow库的使用方法，并通过代码示例进行讲解，帮助你理解和应用Pillow库进行图像处理。

```
pip install Pillow
```

安装完成后，我们可以使用**import**语句导入Pillow库：

```
from PIL import Image
```




# 一、颜色选择器

原理其实很简单，点击取色，弹出一个全屏的透明窗口，获取鼠标点击的位置，在使用ImageGrab.grab()对屏幕截屏，获取鼠标所在位置的颜色。
## 弹出全屏窗口并设置透明

    root =Toplevel()
    w = root.winfo_screenwidth()
    h = root.winfo_screenheight()
    root.geometry(f"{w}x{h}+0+0")
    root.overrideredirect(True) # 隐藏窗口栏
    root.attributes('-alpha',0.01)# 设置透明度 最小0.01 设置为0 界面会消失掉
    root.configure(cursor="crosshair") # 设置鼠标样式
    root.bind("<Button-1>",lambda event:callback(event,root,colorHex,colorRGB,colorTv,w,h))
    root.bind("<Button-3>",lambda event:callback(event,root,colorHex,colorRGB,colorTv,w,h))
    mainloop()
## 截屏获取颜色

    root.destroy()
    img = ImageGrab.grab()
    img = img.resize((w, h))# 对截图大小重置为窗口大小。
    px = img.load()
    img.close()
    rgbroot = px[event.x, event.y]
    
    rgb_hex = rgb2hex(rgbroot)
    
    rgb_1 = hex2rgb(rgb_hex)
    
    setTvContent(colorHex,rgb_hex)
    setTvContent(colorRGB,rgb_1)
    colorTv.config(background=f"{rgb_hex}")
## 窗口大小和截屏的图片大小不一致 ##
如果是win系统，设置了缩放与布局（通常是125%），会出现点击的颜色和返回的颜色不一致的问题，将比例改为100%就会正常取色。但是这样去改系统还是比较麻烦，其实可以在程序里面，将截取的图片，缩放到和窗口大小一样就行。

```
    img = img.resize((w, h))
```


## 取色板 ##
取色笔是tk自带组件，调用相关的包就行了。

```
    from tkinter import colorchooser
    colorchooser.askcolor()
```


## RGB转HEX ##
    def rgb2hex(rgb):
    hex_color = "#" + hex(rgb[0])[2:].zfill(2) + hex(rgb[1])[2:].zfill(2) + hex(rgb[2])[2:].zfill(2)
    return hex_color.upper()
## HEX转RGB ##
    def hex2rgb(hex_color):
    h = hex_color
    rgb = (int((h[1:3]), 16), int((h[3:5]), 16), int((h[5:7]), 16))
    return rgb

## 整体代码

```
#!/usr/bin/env python

-*- coding: utf-8 -*-

@Time    : 2023/6/6 20:15

@Author  : backpacker

@File    : ColorPython.py

@Description : 颜色选择器

from tkinter import Tk,messagebox,filedialog
from tkinter.colorchooser import *
from tkinter import *

from PIL import ImageGrab

def hex2rgb(hex_color):
    h = hex_color
    rgb = (int((h[1:3]), 16), int((h[3:5]), 16), int((h[5:7]), 16))
    return rgb

def rgb2hex(rgb):
    hex_color = "#" + hex(rgb[0])[2:].zfill(2) + hex(rgb[1])[2:].zfill(2) + hex(rgb[2])[2:].zfill(2)
    return hex_color.upper()

def callback(event,root,colorHex, colorRGB, colorTv,w,h):
    root.destroy()
    img = ImageGrab.grab()
    img = img.resize((w, h))# 对截图大小重置为窗口大小。
    px = img.load()
    img.close()
    rgbroot = px[event.x, event.y]

​    rgb_hex = rgb2hex(rgbroot)

​    rgb_1 = hex2rgb(rgb_hex)

​    setTvContent(colorHex,rgb_hex)
​    setTvContent(colorRGB,rgb_1)
​    colorTv.config(background=f"{rgb_hex}")


​	
​	def gatherColor(colorHex:Text,colorRGB:Text,colorTv:Label):
​	    root =Toplevel()
​	    w = root.winfo_screenwidth()
​	    h = root.winfo_screenheight()
​	    root.geometry(f"{w}x{h}+0+0")
​	    root.overrideredirect(True) # 隐藏窗口栏
​	    root.attributes('-alpha',0.01)# 设置透明度 最小0.01 设置为0 界面会消失掉
​	    root.configure(cursor="crosshair") # 设置鼠标样式
​	    root.bind("<Button-1>",lambda event:callback(event,root,colorHex,colorRGB,colorTv,w,h))
​	    root.bind("<Button-3>",lambda event:callback(event,root,colorHex,colorRGB,colorTv,w,h))
​	    mainloop()


​	
​	def selectColor(colorHex:Text,colorRGB:Text,colorLB:Label):
​	    selectColor = askcolor()
​	

​    setTvContent(colorHex,selectColor.__getitem__(1))

​    setTvContent(colorRGB,selectColor.__getitem__(0))

​    colorLB.config(background=f"{selectColor.__getitem__(1)}")

​    pass

def setTvContent(tv:Text,char:str):
    tv.delete(0.0,END)
    tv.insert(END,char)


​	
​	
​	def showDialog():
​	    root=Tk()
​	    root.geometry("640x540")
​	    root.title("颜色采集")
​	

​    withd=20
​    height=1

​    Label(root,text="颜色值HEX: ",width=withd,height=height,font=10,background="light gray").grid(row=0,column=0,pady=8)
​    Label(root,text="颜色值RGB: ",width=withd,height=height,font=10,background="light gray").grid(row=1,column=0,pady=8)
​    Label(root,text="颜色     : ",width=withd,height=height,font=10,background="light gray").grid(row=2,column=0,pady=8)
​    Label(root,text="选择颜色值: ",width=withd,height=height,font=10,background="light gray").grid(row=3,column=0,pady=8)
​    Label(root,text="选择颜色值: ",width=withd,height=height,font=10,background="light gray").grid(row=4,column=0,pady=8)

​    colorHex = Text(root, width=withd,height=height,font=10, background="light gray")
​    colorHex.grid(row=0,column=1,pady=8,padx=4)

​    colorRGB = Text(root,width=withd,height=height, font=10, background="light gray")
​    colorRGB.grid(row=1,column=1,pady=8,padx=4)

​    colorTv = Label(root, width=withd,height=height,font=10, background="light gray")
​    colorTv.grid(row=2,column=1,pady=8,padx=4)

​    Button(root,text="点击采集", width=withd,height=height,font=10, background="light gray",
​                      command=lambda :gatherColor(colorHex,colorRGB,colorTv)).grid(row=3,column=1,pady=8,padx=4)
​    Button(root,text="点击选择", width=withd,height=height,font=10, background="light gray",
​                      command=lambda :selectColor(colorHex,colorRGB,colorTv)).grid(row=4,column=1,pady=8,padx=4)
​    mainloop()

if __name__ == '__main__':
    showDialog()
```

# 二、打开和保存图像

1. **打开图像**。使用Pillow库可以轻松打开各种图像格式的文件。我们可以使用**open()**函数打开图像文件，并将其赋值给一个变量。

代码示例：

```
from PIL import Image

# 打开图像文件
image = Image.open("image.jpg")
```

在上面的例子中，我们使用**open()\**函数打开了名为"image.jpg"的图像文件，并将其赋值给\**image**变量。这样就可以在后续的代码中使用**image**对象进行图像处理。

1. **保存图像**。Pillow库提供了**save()**方法，可以将处理后的图像保存为不同格式的文件。我们可以指定保存的文件名和保存的格式。

```
from PIL import Image

\# 打开图像文件
image = Image.open("image.jpg")

\# 保存图像
image.save("output.png", "PNG")
```

在上面的例子中，我们使用**save()\**方法将\**image**对象保存为名为"output.png"的PNG格式文件。通过指定不同的格式，我们可以保存图像为JPEG、PNG、BMP等格式。

# 三、基本图像操作

1. **调整图像大小**。Pillow库提供了**resize()**方法，可以调整图像的大小。我们可以指定新的宽度和高度，也可以根据比例进行调整。

代码示例：

```
from PIL import Image

\# 打开图像文件
image = Image.open("image.jpg")

\# 调整图像大小
new_size = (800, 600)
resized_image = image.resize(new_size)

\# 保存调整后的图像
resized_image.save("resized_image.jpg")
```

在上面的例子中，我们使用**resize()**方法将图像调整为800x600像素的大小，并将调整后的图像保存为"resized_image.jpg"文件。

1. **裁剪图像**。 Pillow库的**crop()**方法可以用于裁剪图像。我们可以指定裁剪区域的左上角和右下角坐标。

代码示例：

```
from PIL import Image

\# 打开图像文件
image = Image.open("image.jpg")

\# 裁剪图像
box = (100, 100, 500, 400)
cropped_image = image.crop(box)

\# 保存裁剪后的图像
cropped_image.save("cropped_image.jpg")
```

在上面的例子中，我们使用**crop()**方法裁剪图像，指定了左上角坐标为(100, 100)，右下角坐标为(500, 400)。裁剪后的图像被保存为"cropped_image.jpg"文件。

1. **旋转图像**。Pillow库提供了**rotate()**方法，可以对图像进行旋转操作。我们可以指定旋转角度进行图像旋转。

代码示例：

```
from PIL import Image

\# 打开图像文件
image = Image.open("image.jpg")

\# 旋转图像
rotated_image = image.rotate(45)

\# 保存旋转后的图像
rotated_image.save("rotated_image.jpg")
```

1. **图像缩略图**。Pillow库的**thumbnail()**方法可以生成图像的缩略图。我们可以指定缩略图的最大尺寸。

代码示例：

```
from PIL import Image

# 打开图像文件
image = Image.open("image.jpg")

# 生成缩略图
thumbnail_size = (200, 200)
image.thumbnail(thumbnail_size)

# 保存缩略图
image.save("thumbnail.jpg")
```

在上面的例子中，我们使用**thumbnail()**方法生成200x200像素的缩略图，并将缩略图保存为"thumbnail.jpg"文件。

1. **添加水印**。Pillow库提供了丰富的绘图功能，可以在图像上添加文本、形状等元素，实现水印效果。

代码示例：

```
from PIL import Image, ImageDraw, ImageFont

# 打开图像文件
image = Image.open("image.jpg")

# 创建绘图对象
draw = ImageDraw.Draw(image)

# 添加水印文本
text = "Watermark"
font = ImageFont.truetype("arial.ttf", 36)
text_size = draw.textsize(text, font)
text_position = (image.width - text_size[0], image.height - text_size[1])
draw.text(text_position, text, fill=(255, 255, 255), font=font)

# 保存带水印的图像
image.save("watermarked_image.jpg")
```

在上面的例子中，我们使用**ImageDraw**模块创建了一个绘图对象，并使用**text()**方法在图像上添加了水印文本。通过指定文本的位置、颜色和字体等参数，我们可以自定义水印效果。