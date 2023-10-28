# 一、pywin32

Python是一种非常流行的编程语言，可以用于各种任务，包括文件和剪贴板的操作。win32clipboard是Python的一个模块，它提供了一些函数，用于与Windows系统的剪贴板进行交互。在本文中，我们将展示如何使用python  win32clipboard模块来复制文件

```
pip install pywin32
```

# 二、调用Windows API

Pywin32库提供了对Windows API的封装，可以方便地调用Windows API。调用Windows API需要先导入win32api模块，然后使用该模块中的函数即可。例如，要创建一个消息框，可以使用以下代码：

```
import win32api, win32con

win32api.MessageBox(0, "Hello, Pywin32!", "Message", win32con.MB_OK)
```

这段代码会弹出一个消息框，显示“Hello, Pywin32!”。

# 三、控制窗口

Pywin32库可以帮助我们控制窗口，包括查找窗口、获取窗口句柄、设置窗口大小等等。其中，查找窗口和获取窗口句柄是最常用的操作。以下是一个查找窗口并获取窗口句柄的示例代码：

```
import win32gui

hwnd = win32gui.FindWindow(None, "窗口标题")

print(hwnd)
```

这段代码会查找标题为“窗口标题”的窗口，并打印出窗口句柄。

# 四、读取注册表

Pywin32库可以帮助我们读取Windows注册表中的键值。要读取注册表，需要先导入win32api模块，然后使用该模块中的函数即可。以下是一个读取注册表键值的示例代码：

```
import win32api

key = win32api.RegOpenKey(win32con.HKEY_CURRENT_USER, "SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run", 0, win32con.KEY_READ)

value = win32api.RegQueryValueEx(key, "键名")[0]

print(value)
```

这段代码会读取“HKEY_CURRENT_USER\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run”键中名为“键名”的键值，并打印出该键值。

# 五、调用COM组件

Pywin32库可以帮助我们调用COM组件。COM是一种面向对象的组件技术，可以实现各种功能，如打印、文件操作、数据库操作等等。要调用COM组件，需要先导入win32com模块，然后使用该模块中的函数即可。以下是一个调用Word组件进行文本替换的示例代码：

```
import win32com.client

word = win32com.client.Dispatch("Word.Application")

word.Visible = True

doc = word.Documents.Open("D:\\test.docx")

doc.Content.Find.Execute("查找文本", False, False, False, False, False, True, 1, True, "替换文本", 2)

doc.Save()

doc.Close()

word.Quit(
```

)

这段代码会打开名为“test.docx”的Word文档，查找文本“查找文本”，并将其替换为“替换文本”。

## 读取粘贴数据

```
##获取剪切板内容
win32clipboard.OpenClipboard()
context=win32clipboard.GetClipboardData(win32clipboard.CF_UNICODETEXT)
win32clipboard.CloseClipboard()

import win32clipboard as wc
import win32con

# 获取剪切板内容
def getCopy():
    wc.OpenClipboard()
    t = wc.GetClipboardData(win32clipboard.CF_UNICODETEXT)
    wc.CloseClipboard()
    return t

# 写入剪切板内容
def setCopy(str):
    wc.OpenClipboard()
    wc.EmptyClipboard()
    wc.SetClipboardData(win32clipboard.CF_UNICODETEXT, str)
    wc.CloseClipboard()

setCopy("中文English")
print(getCopy())

```

强调一点，网上很多人将 <u>**win32con.CF_UNICODETEXT**</u> 写成 <u>**win32con.CF_TEXT**</u>，这个是需要转码的，不然中文会有乱码，而且写入剪贴板的英文中间会有空格。