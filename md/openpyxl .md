# Openpyxl  #
模块属于第三方模块，是一个在 python 中能够处理 excel 文件的模块，还有比较出名的是xlrd、xlwt 分别控制excel文件的读写，这俩个能够兼容所有版本的文件。openpyxl 针对 excel 2003版本之前的兼容性可能不好 但是功能更加强大。 
##安装方式
      pip install openpyxl  
##使用方式
###创建 .xlsx

    import openpyxl
    workbook = openpyxl.workbook()
####创建工作表Sheet
xlsx文件工作表的索引是从0开始的

    # 第一个工作表后面创建工作表
    sheet_name = ‘sheet1’
    sheet = workbook.create_sheet(sheet_name)
    
    # Equal to the following
    # 工作表名称列表
    sheet_names = workbook.get_sheet_names()
    sheet = workbook.create_sheet(sheet_name, index=len(sheet_names))
    
    # 第一个工作表前创建
    sheet = workbook.create_sheet(sheet_name, 0)
    # sheet = workbook.create_sheet(sheet_name, index=0)
    
    # 使用新建xlsx文件后活动状态的空白工作表
    sheet = workbook.active
    sheet.title = sheet_name
	
	 ws1 = wb.create_sheet() # 插入到结尾 (默认)
	# or
	 ws2 = wb.create_sheet(0) # 插入到启始位置
###在创建工作表时，会自动给它们一个名称。它们按顺序编号(表格，表格1，表格2，……)。你可以在任何时候用title属性改变这个名字:

	 ws.title = "New Title"
###为工作表指定名称后，可以将其作为工作簿的键或使用openpyxl.workbook.Workbook.get_sheet_by_name()/sheetnames方法：
	>>> ws3 = wb["New Title"]
	>>> ws4 = wb.get_sheet_by_name("New Title")
	>>> ws is ws3 is ws4
	True

###您可以使用openpyxsl .workbook. workbook. get_sheet_names()方法查看工作簿中所有工作表的名称：
	>>> print(wb.get_sheet_names())
	['Sheet2', 'New Title', 'Sheet1']
###可以循环遍历工作表：
	>>> for sheet in wb:
	... print(sheet.title)


###保存Workbook

    excel_file = ‘excel1.xlsx’
    workbook.save(excel_file)
###关闭 Workbook

    workbook.close()
###打开.xlsx
    excel_file = ‘excel1.xlsx’
    workbook = openpyxl.load_workbook(excel_file)
###使用工作表
    # 使用当前活动工作表
    sheet = workbook.active
    
    # 使用指定已存在的工作表
    sheet_name = ‘sheet1’
    sheet = workbook.get_sheet_by_name(sheet_name)
    
    # 判断工作表是否已存在
    sheet_names = workbook.get_sheet_names()
    sheet_existed = sheet_name in sheet_names
###修改工作表单元格内容
xlsx文件工作表的单元格索引是从1开始的。

    # data = [[‘Name’, ‘Sex’, ‘Age’],
    # 		[‘Jack’, ‘M’, ‘20’], [‘Ross’, ‘F’, ‘19’], [‘Peter’, ‘M’, ‘25’]]
    data = [[‘Jack’, ‘M’, ‘20’], [‘Ross’, ‘F’, ‘19’], [‘Peter’, ‘M’, ‘25’]]
    for row, item in enumerate(data):
    for column, cell in enumerate(item):
    sheet.cell(row=row + 1, column=column + 1, value=cell)

    sh.cell(row_init, 4).value = f"{baseHear}{web_url.strip()}"
###添加空白行

    workbook.remove(sheet_name)
	# workboo.remove(worksheet=sheet_name)

### 读取表的当前行与列 ###
    sh = wb[sheets[sheetIndex]]
    rows = sh.rows
    columns = sh.columns
    print(f"{rows},{columns}")

##示例
	def save_to_excel(data, excel_file, sheet_name='sheet1'):
	# data is like [[row1_column1, row1_column2, row1_column3],
	#				[row2_column1, row2_column2, row2_column3],
	#				[...], ...]
    if os.path.exists(excel_file):
        workbook = load_excel(excel_file)
    else:
        workbook = openpyxl.Workbook()
    sheet_names = workbook.get_sheet_names()
    if sheet_name in sheet_names:
        sheet = workbook.get_sheet_by_name(sheet_name)
    else:        
        sheet = workbook.create_sheet(sheet_name)
        # sheet = workbook.create_sheet(sheet_name, len(workbook.get_sheet_names()))
        # sheet = workbook.active
        # sheet.title = sheet_name
    for row, item in enumerate(data):
        for column, cell in enumerate(item):
            sheet.cell(row=row + 1, column=column + 1, value=cell)
    workbook.save(excel_file)
    workbook.close()

