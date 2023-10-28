# python中继承的用法 #

## 使用 super() 函数 ##
Python 还有一个 super() 函数，它会使子类从其父继承所有方法和属性：

	class Student(Person):
	  def __init__(self, fname, lname):
	    super().__init__(fname, lname)

通过使用 super() 函数，您不必使用父元素的名称，它将自动从其父元素继承方法和属性。


### 1.什么是继承 ###

	"""
	让子类直接拥有父类的属性和方法的过程就是继承
	父类  -  被继承者(又叫超类)
	子类  -  继承者
	"""
### 2.怎么继承 ###

	"""
	class 类名(父类1,父类2,...):
	    类的说明文档
	    类的内容
	    
	注意: 默认情况下，定义的类继承自 object
	"""


	class Person:
	    num = 61
	
	    def __init__(self):
	        print('Person中init')
	        self.name = '小明'
	        self.age = 18
	        self.gender = '男'
	        self.__sex = '女'
	
	    def eat(self):
	        print(f'Person:{self.name}在吃饭')
	
	    @classmethod
	    def show_num(cls):
	        print(f'人类的数量:{cls.num}')
	
	    @staticmethod
	    def func1():
	        print('人类破坏环境！')
	
	
	# 让 Student(子类) 继承 Person(父类)
	class Student(Person):
	    pass
	
	
	# 继承的时候子类可以直接拥有父类所有的属性和方法
	print(Student.num)
	stu = Student()
	print(stu.name, stu.age, stu.gender)
	stu.eat()
	Student.show_num()
	Student.func1()
	print(stu.__dict__)

### 3.在子类中添加内容 ###

	"""
	1）在子类中添加类属性和方法
	类属性和方法的添加不会因为继承而收到任何影响
	2) 添加对象属性
	对象属性是怎么被继承：继承的时候因为init方法被继承，间接继承了对象属性
	
	在子类的__init__方法中通过 super()去调用父类的__init__方法
	"""
	
	# 类中的方法的调用过程(重要)
	"""
	通过类或者对象在调用方法的时候，会先看当前类中有没有这个方法，如果有就直接调用自己类中的方法；没有就看父类中有没有定义这个方法，如果父类定义了就调用父类的；父类没有定义，就看父类的父类中有没有定义....以此类推，如果 object 中没有定义才会报错！
	"""
	
	
	class Teacher(Person):
	    title = '老师'
	
	    def __init__(self):
	        # 调用父类的init方法
	        super().__init__()
	        self.school = '千锋'
	        self.subject = 'Python'
	        self.tea_id = '001'
	
	    def attend_class(self):
	        print('老师上课')
	
	    def eat(self):
	        super().eat()
	        print(f'老师在吃饭')
	
	
	print(Teacher.num, Teacher.title)
	t1 = Teacher()
	t1.attend_class()
	
	print(t1.school, t1.subject, t1.tea_id)
	print(t1.name)
	
	t1.eat()

# 二、多继承 #


	
	class Animal:
	    num = 10
	
	    def __init__(self, age, gender):
	        self.age = age
	        self.gender = gender
	
	    def eat(self):
	        print('动物需要吃东西')
	
	
	class Fly:
	    name = '飞行器'
	
	    def __init__(self, height, time):
	        self.height = height
	        self.time = time
	
	    def stop(self):
	        self.height = 0
	        print('停止飞行')
	
	
	class Bird(Animal, Fly):
	    pass
	
	
	b1 = Bird(2, '雌')
	
	# 两个父类的类属性都可以继承
	print(Bird.num)
	print(Fly.name)
	
	# 对象属性只会继承第一个父类的
	print(b1.age, b1.gender)
	# print(b1.height, b1.time)    # AttributeError: 'Bird' object has no attribute 'height'
	
	# 两个父类的不同方法都可以继承
	b1.eat()
	b1.stop()
	
	
	# 面试题：
	class A:
	    def show(self):
	        print('A')
	
	
	class B(A):
	    def show(self):
	        super(B, self).show()
	        print('B')
	
	
	class C(A):
	    def show(self):
	        super().show()
	        print('C')
	
	
	class D(B, C):
	    def show(self):
	        super().show()
	        print('D')
	
	
	print('==============d============')
	# mro:DBCA
	d = D()
	d.show()
	#
	# print(D.__mro__)
	print('===============b===============')
	b = B()
	b.show()
	
	
	# 面试题扩展
	class A:
	    def show(self):
	        print('A')
	
	
	class B(A):
	    def show(self):
	        super().show()
	        print('B')
	
	
	class C(A):
	    def show(self):
	        super().show()
	        print('C')
	
	
	class D(A):
	    def show(self):
	        super().show()
	        print('D')
	
	
	class E(B, C):
	    def show(self):
	        super().show()
	        print('E')
	
	
	class F(C, D):
	    def show(self):
	        super().show()
	        print('F')
	
	
	class G(F, E):
	    def show(self):
	        super().show()
	        print('G')
	
	
	print('=========G========')
	# mro: GFECDBA
	# G
	g = G()
	g.show()
	
	print('==================')
	f = F()
	f.show()
	
	# super的用法
	"""
	super(类, 对象)  -  获取指定类的父类（对象必须是类的对象； 类默认指向当前类，对象默认是当前类的对象)
	"""
	
	
	class A:
	    def show(self):
	        print('A')
	    pass
	
	
	class B(A):
	    def show(self):
	        print('B')
	
	
	class B2:
	    def show(self):
	        print('B2')
	
	
	class C(B, B2):
	    def show(self):
	        # super().show()     # super(C, self).show()
	        # super(C, self).show()
	        super(B, B()).show()
	        print('C')
	
	
	print('============C:=============')
	c = C()
	c.show()

