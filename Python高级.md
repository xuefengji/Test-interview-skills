# Python高级编程和算法面试真题

1、

```
a = ('a','b','c')
b = copy.copy(a)
c = copy.deepcopy(a)
if b == c:    
	print("b和c的值相等")
if id(b) == id(c):    
	print("b和c的地址相等")
```

结果：两个都打印

如果将a的值改变为list或dict，只打印b和c的值相等

考点：

+ 深浅拷贝
+ 可变类型和不可变类型



2、

```
class Person:    
	x = 5    
	y = 6    
	def __init__(self,x,y):        
		self.x = x        
		self.y = y    
	def add(self):        
	return self.x + self.y
person = Person(10,20)
person.z = 7
print(person.x)     #10
print(person.y)     #20
print(Person.x)     #5
print(Person.y)     #6
print(Person.add(Person))   #11
print(person.add())         #30
print(person.z)      #7
print(Person.z)    #报错：AttributeError: type object 'Person' has no attribute 'z'
```

考点：

+ 类变量和实例变量



3、python中一个函数function接收3个参数a、*args 、**kwargs

+ *args
+ **kwargs

考点：可变参数



4、请根据列表list1=[1,2,3,4,5,6],使用一行代码生成一个新的列表list2，list2中每个元素是list1中的平方

考点：推导式



5、请将下面的列表进行排序list1=[20,15,88,97,76,13,27,49]

考点：冒泡、快排在效率上不同



6、请实现@runtime效果为当调用student_run时会自动打印当前时间

```
	@runtime
	def student_run(name):
		print("student" + name + "run")
		
	student_run("张三")
```
考点：注解

7、
请简述func1和func2函数的返回值，以及函数运行机制
```
	def func1():
		for i in range(1, 5):
			return i
			
	def func2():
		for i in range(1, 5):
			yield i
```
考点：