# 工具类 #
## 检查excel 是否打开 ##
	  def check_excel_isOpen(self,filepath):
	      try:
	            # 未打开
	            os.rename(filepath, filepath)
	            return False
	        except:
	            #已打开
	            return True