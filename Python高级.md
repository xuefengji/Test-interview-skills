# Python高级编程和算法面试真题

1、考点：

+ 深浅拷贝

+ 要从可变类型和不可变类型两方面回答

  + 可变对象：list dict

    + 对于可变对象：如果将a的值改变为list或dict

      ```
      import copy
      
      a = {'key':[1,2,3]}
      b = copy.copy(a)
      c = copy.deepcopy(a)
      print(a,b,c)
      print(id(a),id(b),id(c))
      print(a['key'],b['key'],c['key'])
      print(id(a['key']),id(b['key']),id(c['key']))
      
      
      结果为：
      {'key': [1, 2, 3]} {'key': [1, 2, 3]} {'key': [1, 2, 3]}
      7621560 7621640 42779544
      [1, 2, 3] [1, 2, 3] [1, 2, 3]
      13831560 13831560 42777288
      ```

      当对象为可变对象时，浅拷贝的子元素的地址没变，引用之前的子元素的地址，但深拷贝的子元素也会被拷贝一份

  + 不可变对象：元组、字符串、数字，只要创建就不能改的元素
    
    + 对于纯不可变对象：深拷贝和浅拷贝的值一致，存储的地址空间也一致
    
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
    
    + 当不可变元素中含有可变元素时，如元组含有可变元素
    
      ```
      import copy
      
      a = (1,2,[2,3,4])
      b = copy.copy(a)
      c = copy.deepcopy(a)
      print(a,b,c)
      print(id(a),id(b),id(c))
      print(id(a[2]),id(b[2]),id(c[2]))
      
      结果：
      (1, 2, [2, 3, 4]) (1, 2, [2, 3, 4]) (1, 2, [2, 3, 4])
      46282984 46282984 46971144
      46402984 46402984 46971240
      
      对于不可变对象中含有可变对象时，浅拷贝的父父元素和子元素地址没改变，而深拷贝的会将父元素和子元素都复制一份，地址都会改变
      ```
    
      



2、考点：

+ 类变量和实例变量

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

每个实例的变量都是相互独立的



3、考点：可变参数

python中一个函数function接收3个参数a、*args 、**kwargs

+ *args：元组类型
+ **kwargs：dict类型







4、考点：推导式

请根据列表list1=[1,2,3,4,5,6],使用一行代码生成一个新的列表list2，list2中每个元素是list1中的平方

+ lambda:list2 = map(lambda x:x*x,list1)
+ 推导式方式：
	list2=[i*i for i in list1]
	list2 = [i * i for i in list if i > 2]有条件的列表推导式
	字典推导式：
	key = {
		"key1":10,
		"key2":20,
		"key3":30
	}
	key1 = {key:value for key,value in key.items() if key == "key1"}



5、考点：冒泡、快排在效率上不同
请将下面的列表进行排序list1=[20,15,88,97,76,13,27,49]

常见的排序算法：
+  插入算法、希尔算法、直接排序、堆排序、冒泡排序、快速排序、归并排序、基数排序
复杂度：
+  时间复杂度：
	+ 常数阶O(1)、对数阶O(log2n)、线性阶O(n)、线性对数阶O(nlog2n)、平方阶O(n^2)、立方阶O(n^3)
	 随着问题的规模n的不断增大，上述的时间复杂度就不断的增大，意味着算法的执行效率越低
+ 空间复杂度

+ 冒泡排序：
	+ 相邻的两个数字进行比较，大的向下沉，最后一个元素是最大的
	+ 时间复杂度O(n^2)
	```
		def bubble_sort(blist):
			count = len(list)
			for i in range(0,count):
				for j in range(i+1,count):
					if blist[i] > blist[j]
						blist[i], blist[j]=blist[j],blist[i]
			return blist
	```

+ 快速排序：

  + 递归
  + 列表中取出第一个元素，作为标准。把比第一个元素小的都放在左侧，把比第一个元素大的都放在右侧
  + 时间复杂度：O(nlog2n)

  ```
	def quick_sort(quick_list):
    	if quick_list == []:
    		return []
    	else:
    		first = quick_list[0]
    		less = quick_sort([l for l in quick_list[1:] if l < first])
    		more = quick_sort([m for m in quick_list[1:] if m > first])
    		return less + [first] + more
  ```

  


6、考点：装饰器

请实现@runtime效果为当调用student_run时会自动打印当前时间

```
	@runtime
	def student_run(name):
		print("student" + name + "run")
		
	student_run("张三")
```

runtime代码：
```
import time
def runtime(fn):
    def run_outer(name):
        print(time.time())
        fn(name)
    return run_outer
```

7、考点：生成器
请简述func1和func2函数的返回值，以及函数运行机制

```
	def func1():
		for i in range(1, 5):
			return i
			
	def func2():
		for i in range(1, 5):
			yield i
```
return 会阻断循环

yield不会阻断循环，会将结果存储在生成器对象中，每生成一个返回一个，不像list是等待所有一起返回，占用内存比较小，对于生产器对象可以使用循环获取值
