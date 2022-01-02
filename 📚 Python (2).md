

# 一、程序构成
> 1.python程序由模块构成，一个模块对应python源文件，后缀名:   .py
> 2.模块由语句构成，顺序依次执行

使用\行连接符
​


- 对象
   - python中，一切皆对象，对象本质：内存块，拥有特定的值，支持特定类型的相关操作
   - 每个对象由：标识identity, 类型type，值value
   - 使用内置函数**id(obj)**	返回对象obj的标识
   - 使用**type(obj)** 	获得对象的所属类型
   - 使用**print(obj)	**打印出值
```python
a = 3
id(3) #1531372336
type(3) #<class 'int'>
b="234"
type(b) #<class 'str'>
```

- 引用：python中变量为对象的引用，变量存储的就是对象的地址，变量通过地址引用了"对象"
- 变量位于：栈内存；对象位于：堆内存
- ![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641062831718-fe75ee46-7088-46c1-8e5d-40fd370a9d27.png#clientId=u20dd605f-7688-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=307&id=uceda0d79&margin=%5Bobject%20Object%5D&name=image.png&originHeight=307&originWidth=331&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36861&status=done&style=none&taskId=ucd1d0112-7c86-4d57-9d1f-366a34bae44&title=&width=331)
- Python是**动态类型语言**，根据变量引用的对象，python解释器自动确定数据类型
- python是**强类型语言**，每个对象都有数据类型，只支持该类型支持的操作

​

标识符：变量，函数，类，模块名称。区分大小写

- 模块和包名，全小写，math,os,sys
- 函数名，全小写，phone, my_name
- 类名，首字母大写，MyClass, Phone
- 常量名，全大写，SPEED，MAX_SPEED

​


- 删除变量 del a 	垃圾回收机制【对象没有被引用】
- **链式**赋值	x=y=123	【x,y指向同一个对象】
- 系列解包赋值 a,b,c=4,5,6	相当于a=4,b=5,c=6
```python
//利用系列解包赋值实现变量交换
a,b=1,2
a,b=b,a
print(a,b)
```

- **常量**，python不支持常量，即没有语法规则限制改变一个常量的值，我们只能通过约定常量的命名规则，以及在程序的逻辑上不对常量的值作出修改
```python
MAX_SPEED = 120
print(MAX_SPEED)
```


- 最基本**内置数据类型**：整型，浮点型，布尔型，字符串型
- **运算**，/浮点数除法，//整数除法，%模（取余），**幂
- divmod()函数同时得到商和余数 
- **进制**
   - 0b或0B，二进制	0	1
   - 0o或0O，八进制
   - 0x或0X，十六进制
```python
int(3.999)#3
int("222abc")#报错
```

- 自动转型：整数和浮点数混合运算，表达式结果自动转型成浮点数，2+8.0的结果是10.0
- python3中，int可以存储任意大小的整数
- 浮点数float, 3.14 [314E-2,314e-2]
```python
float(3) 	#3.0
float("3.4") 	#3.4
b=3+5.2 	#8.2
int(3.94)	#3
round(3.54)	#4
```

- 增强型赋值运算符 +=，/=	//=	**=
```python
//时间
import time
b=int(time.time())
```

- 逻辑运算符 or, and, not
- **同一运算符**，用于比较两个对象的存储单元，实际比较的是对象的地址,is , is not
- **整数缓存问题**:[-5,256] 缓存； 保存为文件执行[-5,+]缓存
```python
c=10
d=10
c is d	#True
a = -6
b = -6
a = b #False
```
​

# 二、基础
### 1. 字符串
字符串的本质：字符序列，不支持单字符类型。
字符串编码Unicode，16位

- ord()字符-->Unicode码
- chr()十进制-->对应的字符 

引号创建字符串
连续三个单引号或三个双引号，可以帮助我们创建_多行字符串_
空字符串 c = ''	len(c)
转义字符：\续行符，\\反斜杠符，\'单引号，\"双引号，\b退格，\n换行，\t横向制表符，\r回车
字符串复制： a = 'Sxt'*3	
```python
print("aa",end='*')
print("bb",end='**')
#aa*bb**
```
str()实现数字转型字符串
```python
str(5.20)-->'5.20'
str(3.14e2)-->'314.0'
str(True)-->'True'
```
使用[ ] 提取字符，字符串本质就是字符序列

- 正向搜索[0,len(str)-1]，反向搜索

**replace()**实现字符串替换，a.replace('c','高')
​

字符串切片slice操作[start; end; step]	#包头不包尾
三个量为负数的情况

- "abcdfdf"[-3:]	#倒数三个
- "sadfasdfas"[-8:-3]倒数第八个到倒数第三个
- "adfasdfasdgas"[::-1]步长为负，从右到左反向提取

切片操作时，
```python
a = "to be or not to be"
a.split()
# ['to', 'be', 'or', 'not', 'to', 'be']

b =  ['to', 'be', 'or', 'not', 'to', 'be']
'*'.join(b)
#	'to*be*or*not*to*be'


import time

time01 = time.time()
a = ""
for i in range(100000):
    a += "xst"
    
time02 = time.time()
print("运算时间："+str(time02-time01))
```

- **字符串驻留：**仅保存一份相同且不变字符串的方法，不同的值被存放在字符串驻留池中
- 对于符合标识符规则的字符串（仅包含下划线__,字母和数字）会启用字符串驻留机制
- **is / not is**，判断两个对象是否是同一对象，比较的是对象的地址，即id(obj1)是否和id(obj2)相等
- i**n / not in**，成员操作符



**常用查找方法**

1. len(a)
1. a.startswith("xxx")		#开头
1. a.endwith("bbb")		#结尾
1. a.find("高")
1. a.rfind("的")	#_最后一次_出现指定字符串的位置
1. a.count("啊")	#指定字符串出现了几次
1. a.isalnum()	#所有字符全是字母或数字



**去除首尾信息**
```python
"*s*x*t*".strip('*')
#'s*x*t'
"*s*x*t*".lstrip('*')	#'s*x*t*'
"*s*x*t*".rstrip('*')	#'*s*x*t'
"   s*x*t   ".strip()	#'s*x*t'
```
**大小写转换**
a.capitalize() 首字母大写
a.title()每个单词首字母大写
a.upper()		a.lower()		
a.swapcase() 	#产生新的，所有字母大小写转换
​

**格式排版**	center(), ljust()	, rjust()
```python
a = "SXT"
a.center(10,"*")
#'***SXT****'

a = "SXT"
a.center(10)
#	'   SXT    '

a = "SXT"
a.ljust(10,"%")
#	'SXT%%%%%%%'
```
**其他方法**

- isalnum()	是否为字母或数字
- isalpha(）是否只由字母组成（含汉字）
- isdigit()	是否只由数字组成
- isspace()	是否为空白符
- isupper()	是否为大写字母
- islower()	是否为小写字母



字符串格式化** str.format()**
```python
a = "名字是:{0},年龄是:{1}"
a.format("A",12)
#	'名字是:A,年龄是:12'

a = "名字是:{name},年龄是:{age}"
a.format(age=19,name="小王")
#	'名字是:小王,年龄是:19'
```
​

**填充和对齐**
^, <, >分别是居中，左对齐，右对齐，后面带宽度
：号后面带填充的字符，只能是一个字符，不指定的话默认是用空格填充
```python
"{:*>8}".format("245")	# '*****245'

"我是{0}，我喜欢数字{1:*^8}".format("AAA","666")
#'我是AAA，我喜欢数字**666***'
```
​

数字格式化
```python
a = "我是{0},我的存款有{1:.2f}"
a.format("AAA",3.114324123)
#'我是AAA,我的存款有3.11'
```


**可变字符串**
```python
import io
s="hello,sxt"
sio=io.StringIO(s)
sio.getvalue()
sio.seek(7)#指针
sio.write("g")
sio.getvalue()
```
​

**比较运算符**可以连用	3<a<10
​

**位操作**	
```python
a = 0b11001
b = 0b01000
c = a|b
bin(c)
# '0b11001'

bin(c&b)	#'0b1000'
bin(c^b)	#'0b10001'

a = 3
a<<2	#12	左移2位，相当于乘以4



#1.列表、元组等合并
[10,20,30]+[5,10,100]
# [10,20,30]+[5,10,100]

#2.列表、元组等复制
[10,20,30]*3
# [10, 20, 30, 10, 20, 30, 10, 20, 30]
```
❤Python没有++，--
❤乘除优先加减
❤位运算和算术运算>比较运算符>赋值运算符>逻辑运算符
​

### 2. 序列
**数据存储方式**：字符串、列表、元组、字典、集合
存放多个值的连续的内存空间[10,20,30,40]
![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641111702614-bf4d9de5-f374-41b8-8301-c926982b4fad.png#clientId=u86f42483-b228-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=261&id=u96bb8b4e&margin=%5Bobject%20Object%5D&name=image.png&originHeight=261&originWidth=686&originalType=binary&ratio=1&rotation=0&showTitle=false&size=87254&status=done&style=none&taskId=ud7c32798-347f-435e-9d85-61d6826dff3&title=&width=686)
​

列表：用于存储任意数目、任意类型的数据集合
a = [10,20,'abc',True]
python的列表大小可变，根据需要随时增加或缩小
```python
#列表创建
a = [10,20,'gaoqi','sxt']
a = []#空列表
a.append(20)

a = list()#创建一个空列表对象
a = list(range(10))
# [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

#range([start,]end[,step])
list(range(3,15,2))
# [3, 5, 7, 9, 11, 13]

list(range(15,3,-1))
# [15, 14, 13, 12, 11, 10, 9, 8, 7, 6, 5, 4]

list(range(-10,-13,-1))
# [-10, -11, -12]

a = [x*2 for x in range(5)]
# [0, 2, 4, 6, 8]

a = [x*2 for x in range(100) if x%9==0]#通过if过滤元素
# [0, 18, 36, 54, 72, 90, 108, 126, 144, 162, 180, 198]

```
​

♥列表元素的增加和删除
```python
a = [20,40]
a.append(80)	#[20, 40, 80]

a = [20,40]
a = a+[50]	#[20, 40, 50]产生一个新对象

a = [20,40]
a.extend([50,60])	#原地操作，不创建新对象

a = [10,20,30]
a.insert(2,100)
# [10, 20, 100, 30]

#删除
a = [10,20,30]
del a[1] #[10,30]

a = [10, 20, 100, 30]
b = a.pop()	#30
c = a.pop(1) #20

a = [10, 20, 100, 30]
a.remove(10)
# [20, 100, 30] 删除第一次出现的

# index()获得指定元素在列表中首次出现的索引
a = [10, 20, 100, 30]
a.index(10)
a.index(20,3) #指定范围，从3开始

a = [10, 20, 100, 30]
a.count(10)#1，计数

#成员资格判断
a = [10, 20, 100, 30]
20 in a	
# True

a = [10, 20, 100, 30]
a.sort()#升序
a.sort(reverse=True)#降序

import random
random.shuffle(a) #打乱顺序


#建新列表的排序
a = [20,10,30,40]
a = sorted(a)
```




元组tuple
不可变序列，
```python
# 元组的创建
a = (10,20,30)
a = 10,20,30

# 元组的访问和计数
a = (20,10,30,9,8)
a[1]
a[:4]	#切片

a = (20,10,30,9,8)
sorted(a)

# zip(列表1，列表2，...)将多个列表对应位置的元素组合成为元组，并返回这个zip对象
a = [10,20,30]
b = [0,50,60]
zip(a,b)
```
​

**生成器推导式创**建元组，使用小括号，生成器推导式生成的不是列表也不是元组，而是一个生成器对象，__next__()方法进行遍历
```python
s = (x*2 for x in range(5))
# <generator object <genexpr> at 0x0000017E3A004BA0>
tuple(s)
# (0, 2, 4, 6, 8)

list(s)
# [] 只能访问一次元素，第二次就为空了，需要在生成一次



s = (x*2 for x in range(5))
s.__next__()
# 0
s.__next__()
# 2 
s.__next__()
# 4
```

1. 元组核心特点：不可变序列
1. 元组的访问和处理速度比列表快
1. 与整数和字符串一样，元组可以作为字典的键，列表永远不可能作为字典的键

​

​

字典
"键值对"的无序可变序列
key	: 任意的不可变数据，比如：整数、浮点数、字符串、元组
但是：列表，字典，集合这些可变对象不行
```python
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
b = dict('name':'gaoqi' ,'age':18 ,'job':'programmer')
c = dict([('name':'gaoqi' ),('age':18),('job':'programmer')])

#通过zip()创建字典对象
k = ['name','age','job']
v = ['A',10,'B']
d = dict(zip(k,v))


# 通过fromkeys创建值为空的字典
b = dict.fromkeys(['name','age','job'])
# b = dict.fromkeys(['name','age','job'])


#字典元素的访问
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
a['name']	#'gaoqi'
#通过get()方法获得value
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
a.get('name')	#'gaoqi'
a.get('A','不存在') 	#'不存在'
a.keys()	#dict_keys(['name', 'age', 'job'])
a.values() 	#dict_values(['gaoqi', 18, 'programmer'])
len(a) 	#3
"name" in a		#True

#使用update()将字典中所有键值对全部添加到就旧字典对象上，如果key有重复，则直接覆盖

#元素删除del()
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
del(a['name'])
#clear()删除全部
#删除pop()
b = a.pop('age')	#18

#popitem()随机删除和返回该键值对
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
a.popitem()
#('job', 'programmer')
```
**序列解包**
x,y,z=(20,30,10)
(a,b,c) = (9,8,10)
[a,b,c] = [10,20,30]
​

```python
a = {'name':'gaoqi' ,'age':18 ,'job':'programmer'}
name,age,job=a
name	# 'name'
name,age,job=a.items()
name	#('name', 'gaoqi')
name,age,job=a.values()
name	#'gaoqi'
```
表格数据使用字典和列表存储，并实现访问
​

**字典核心底层原理**
字典对象的核心是散列表。散列表是一个稀疏数组（总有空白元素的数组），数组的每个单元叫做bucket。每个bucket有两个部分：一个是键对象的引用，一个是值对象的引用。
![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641127465400-68aec49e-6b4a-4084-855c-a0cd1b27af08.png#clientId=ub9cdbe44-4a72-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=148&id=u9626519e&margin=%5Bobject%20Object%5D&name=image.png&originHeight=148&originWidth=234&originalType=binary&ratio=1&rotation=0&showTitle=false&size=35473&status=done&style=none&taskId=u1aa6a639-60db-424d-88ca-cd85a3891dc&title=&width=234)

- 字典在内存中开销巨大，典型的空间换时间
- 键查询速度很快
- 往字典里面添加新键可能导致扩容，导致散列表中键的次序变化。因此，不要在遍历字典的同时进行字典的修改

​

集合：无序可变，元素不能重复，集合底层是字典实现，集合的所有元素都是字典中的“键对象”，因此是不能重复的且唯一的
```python
a = {3,5,7}
a.add(9)
a	#{3, 5, 7, 9}

a = ['a','b','a']
b = set(a)
b	# {'a', 'b'}

#remove()



a = {1,3,'sxt'}
b = {'he','it','sxt'}

a|b	#{1, 3, 'he', 'it', 'sxt'}
a&b #{'sxt'}
a - b	#{1, 3}
a.difference(b)	#{1, 3} 差集
a.intersection(b)	#{'sxt'}交集
```
### 3. 控制语句


选择结构：单分支，双分支，多分支
```python
a = input("请输入一个小于10的数字：")
if int(a)<10:
    print(a)
    
#请输入一个小于10的数字：3
#3

```
在选择和循环结构中，**False情况：**
False, 0,0.0, 控制None,空序列对象（空列表，空元组，空集合，空字典，空字符串），空range对象，空迭代对象
条件表达式中，不能有赋值操作符“=”
​

双分支选择结构
```python
a = input("请输入一个小于10的数字：")
if int(a)<10:
    print(a)
else:
    print("AA")
```
三元条件运算符
```python
num = input("请输入一个小于10的数字：")
print(num if int(num)<10 else "数字太大")
```
​

多分支选择结构
```python
if score<60:
    grade="不及格"
elif score<80:
    grade='及格'
elif score<90:
     grade='良好'
else:
	 grade='优秀'
```
​

选择结构的嵌套
```python
score = int(input("请输入一个分数"))
if score>100 or score<0:
    print("请输入一个0-100的分数")
else:
    if score>=90:
        print("a")
    elif score>=80:
        print("B")
    elif score>=70:
        print("C")
    elif score>=60:
        print("D")
    else:
        print("E")
```
​

### 循环结构
​

1.while
```python
num = 0 
while num<=10:
    print(num)
    num += 1
```

2. for

for 变量 in 可迭代对象：
循环体语句
```python
for x in (20,30,40):
    print(x*3)
    

for x in 'sxt001':
    print(x)
    
```
​

嵌套循环
```python
for x in range(5):
    for y in range(5):
        print(x,end="\t")
    print()
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641131286786-6c27ebd9-6c6e-4bae-9e95-545f19a1357c.png#clientId=ub9cdbe44-4a72-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=88&id=u4bba4f41&margin=%5Bobject%20Object%5D&name=image.png&originHeight=88&originWidth=267&originalType=binary&ratio=1&rotation=0&showTitle=false&size=1751&status=done&style=none&taskId=u50151c9f-28e2-4cbb-902e-ced83ace73d&title=&width=267)


```python
#测试zip()并行迭代

names = ("A",'B',"C")
ages = (10,20,30)
jobs = ("M",'N','P')

for name,age,job in zip(names,ages,jobs):
    print("{0}--{1}--{2}".format(name,age,job))
    
    
#	A--10--M
#	B--20--N
#	C--30--P
```
​

推导式创建序列
```python
#列表推导式	[表达式 for item in 可迭代对象]
y = [x*2 for x in range(1,50) if x%5==0]
cells = [(row,col) for row in range(1,10) for col in range(1,10)]
#可以使用两个循环

#字典推导式
char_count = {c:my_text.count(c) for c in my_text}

#集合推导式
{x for x in range(1,100) if x%9==0}

#生成器推导式（生成元组）
gnt = (x for x in range(1,100) if x%9==0)
#一个生成器只能运行一次。第一次迭代可以得到数据，第二次迭代发现数据已经没有了。
```
​

​

​

​

### 4. 函数用法和底层分析
> 函数分类：内置函数；标准库函数；第三方库函数；用户自定义函数

```python
def test01():
    print("*"*10)
test01()
#	**********
```

- 内置函数对象会自动创建
- 标准库和第三方库函数，通过import导入模块时，会执行模块的def语句



**形参和实参**
```python
def printMax(a,b):#形式参数
    if a>b:
        print(a)
    else:
        print(b)

printMax(10,20)#实际参数

help(printMax.__doc__)#得到文档字符串

def test03(x,y,z):
    return [x*10,y*10,z*10]
print(test03(1,2,3))

test01()
c = test01	#指向同一个对象
c()

id(c) == id(test01)

```
​

全局变量，局部变量
```python
a = 3	#全局变量

def test01():
    b=4
    print(b*4)
 
test01()
```
global a #如果要在函数内改变全局变量的值，增加global关键字声明
a=300
​

locals()#打印输出的局部变量
globals()#打印输出的全局变量
效率测试：局部变量的查询和访问速度比全局变量快
​

**参数的传递**

- 本质：从实参到形参的赋值操作
- Python：一切皆对象，所有的赋值操作都是“引用的赋值”，所以python中参数的传递都是“引用传递”，不是“值传递”
- 对“可变对象”进行“写操作”，直接作用于原对象本身
- 对“不可变对象”进行写操作，会产生一个新的“对象空间”。并用新的值填充这块空间
- 可变对象：字典、列表、集合、自定义的对象等
- 不可变对象有：数字、字符串、元组、function等
```python
b = [10,20]
def f2(m):
    print(id(m))
    m.append(30)
f2(b)	#m和b指向同一个对象
print(id(b))
```


- copy(浅拷贝)：不拷贝子对象的内容，只是拷贝子对象的引用
- deepcopy（深拷贝）：会连子对象的内存也全部拷贝一份，对子对象的修改不会影响源对象



```python
import copy
a = [10,20,[5,6]]
b = copy.copy(a)
print("a:",a)
print("b:",b)
#	a: [10, 20, [5, 6]]
#	b: [10, 20, [5, 6]]

b.append(30)
b[2].append(7)
print('浅拷贝')
print("a:",a)
print("b:",b)

#	浅拷贝
#	a: [10, 20, [5, 6, 7, 7]]
#	b: [10, 20, [5, 6, 7, 7], 30, 30]
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641139096482-efc4c5c5-1592-4022-af9c-b688588df8c1.png#clientId=u4bd258f5-652c-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=301&id=ufc025c33&margin=%5Bobject%20Object%5D&name=image.png&originHeight=490&originWidth=533&originalType=binary&ratio=1&rotation=0&showTitle=false&size=126345&status=done&style=none&taskId=u3ce5618f-2b59-41cc-b742-6c155171217&title=&width=327)
​

```python
import copy
a = [10,20,[5,6]]
b = copy.deepcopy(a)
print("a:",a)
print("b:",b)
#	a: [10, 20, [5, 6]]
#	b: [10, 20, [5, 6]]

b.append(30)
b[2].append(7)
print('深拷贝')
print("a:",a)
print("b:",b)

#	深拷贝
#	a: [10, 20, [5, 6]]
#	b: [10, 20, [5, 6, 7], 30]
```
![image.png](https://cdn.nlark.com/yuque/0/2022/png/25775237/1641139260333-b09839e4-8431-4036-88e2-78cf77316c3a.png#clientId=u4bd258f5-652c-4&crop=0&crop=0&crop=1&crop=1&from=paste&height=456&id=u09c8592d&margin=%5Bobject%20Object%5D&name=image.png&originHeight=575&originWidth=554&originalType=binary&ratio=1&rotation=0&showTitle=false&size=180388&status=done&style=none&taskId=u01e279a7-a4b2-476f-ab1c-b59091c97ae&title=&width=439)
​

传递不可变对象时，如果发生拷贝，是浅拷贝

- 传递不可变对象时，如果发生拷贝，是浅拷贝
- 传递不可变对象时，不可变对象里面包含的子对象是可变的，则方法内部修改了这个可变对象，源对象也发生了变化。

​

**参数的几种类型**
1.位置参数
2.默认值参数	def f1(a, b, c=10, d=20)	#默认值必须位于普通位置参数后面
3.命名参数
def f1(a,b,c): ..
f1(c=10,a=1,b=2)
4.**可变参数**

- *param	将多个参数收集到一个"元组"对象中
- **param  将多个参数搜集到一个"字典"对象中
```python
def f1(a,b,*c):
    print(a,b,c)
f1(8,9,19,20)

def f2(a,b,**c):
    print(a,b,c)
f2(8,9,name='gz',age=18)

def f3(a,b,*c,**d):
    print(a,b,c,d)
f3(8,9,20,30,name='gq',age=18)
```
5.强制命名参数，可变参数后面增加新的参数
```python
def f1(*a,b,c):
    print(a,b,c)
f1(2,b=3,c=4)
```
​

lambda表达式和匿名函数
1.lambda	arg1,arg2,arg3.. :<表达式>
```python
f = lambda a,b,c:a+b+c
print(f(3,4,5))

g = [lambda a:a*2,lambda b:b*3,lambda c:c*4]
print(g[0](6),g[1](7),g[2](8))


#函数也是对象
def test01(a,b,c,d):
	...

h = [test01,test01]
print(h[0](3,4,5,6))
```


**eval()函数**

- 功能：将字符串str当成有效的表达式求值并返回计算结果
```python
s = "print('ab')"
eval(s)

a = 10
b = 20
c = eval("a+b")


dict1 = dict(a=100,b=200)

d1 = eval("a+b")
d2 = eval("a+b",dict1)
```
**​**

**递归函数**
```python
def test01():
    print("test01")
    test02()
    
def test02():
    print("test02")
    
test01()

#test01
#test02
```


**递归函数**

- 终止条件
- 递归步骤：把第n步的值和第n-1步相关联
```python
def test01(n):
    print("test01:",n)
    if n==0:
        print("over")
    else:
        test01(n-1)
```


​

​

### ​

​

​

​

​

​

​

### 5. 公众号
> ~~日常浏览，量变引起质变~~  厕所文学



### 6. 学科哲学
> 哲学就是解决“如何处理问题”的问题
> 学习方法、学科的基本思路、研究历程（历史）、背景（学习只是一种为了解决某些问题而需要去做的事情，找找那个问题吧💡）

# 


# 三、技术笔记
### 技术笔记链接
> 具体技术点

1. test
> 语雀文章链接 | 卡片形式



### 小记
> 零碎知识点



1. ​

