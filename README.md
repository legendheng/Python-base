# Python-base
python3.6基础知识
## 目录：
  * 语法特点
  * 标识符
  * 字符定义
  * 列表list
  * 元组tuple
  * 字典dict
  * 集合set
  * 函数
  * 切片
  * 模块
  * 正则
  * 继承
  * 异常处理
  * 文件操作
  * Lambda函数
                      
### 一、语法特点
    Python的语法十分简洁，采用缩进方式，句末没有分号，条件判断没有大括号{}而是使用:（这些都和C、php、java等很多语言不同）
```python
a = 100
if a >= 0:
    print(a)
else:
    print(-a)
```
### 二、标识符
    标识符第一个字符必须字母或者下划线，不能出现数字或者其他字符，除第一个字符外可以是字母或者下划线或者数字
### 三、字符转义
    (1)使用\来转义，如果需要表示的字符为\，就使用\\
```python
print('I\'m ok.')
```
    (2)使用r``内部的字符默认不转义
```python
print(r'\\\t\\')
```
    (3)使用'''...'''的格式表示多行内容
```python
print('''line1
... line2
... line3''')
```
### 四、列表list
* 特点：查找和插入的时间随着元素的增加而增加；占用空间小，浪费内存很少
  * 定义一个列表：test=['one','two','three'] 注意使用[]
  * 获取列表长度：print(len(test))  #3
  * 获取下标为1的元素：print(test[1]) #two
  * 使用append方法往列表末尾添加元素：test.append('fourth') #['one', 'two', 'three', 'fourth']
  * 从列表中出栈一个元素：test.pop() #此时test列表的元素为['one', 'two', 'three']
  * 直接覆盖列表的元素：test[0]='ling' #此时test列表的元素为['ling', 'two', 'three']
  * 往列表的具体某个方向插值：test.insert(1,'insert') #此时test列表的元素为['ling', 'insert', 'two', 'three']
### 五、元组tuple
* 特点：一旦初始化就不能修改,没有append()，insert()这样的方法,只能取值不能赋值
  * 定义一个元组：test=('one','two','three') 注意使用()
  * 定义一个空元组：kong=()
  * 只定义一个元素时tuple定义时必须加一个逗号,：one=(1,)
### 六、字典dict
* 特点：查找速度非常快，不会随着key的增加而变慢，但是需要占用大量的内存，内存浪费多，跟list刚好相反
  * 定义一个字典：dict={'name':'legend','age':20,'weight':'50kg'}
  * 获取字典的某个值：print(dict['name']) #legend
  * 往字典添加数据：dict['habit']='篮球' #此时dict字典为{'name': 'legend', 'age': 20, 'weight': '50kg', 'habit': '篮球'}
### 七、集合set
* 特点：建立关系，消除重复元素(没有重复的key)
  * 用法一：
    * 定义一个set集合：test = set([one,wwo,three])  #此时set的元素{1, 2, 3}若里面有重复的值会为自动过滤
    * 添加元素：test.add(four) #此时test集合的元素{one,wwo,three,four}
    * 删除元素：test.remove(four) #此时test集合的元素{one,wwo,three}
  * 用法二：
    * 定义两个字符串：a=set('iamlegended') b=set('legended')
    * 输出交集：print(a&b) #输出{'d', 'e', 'n', 'l', 'g'}
    * 输出并集：print(a|b) #输出{'a', 'i', 'd', 'e', 'n', 'l', 'g', 'm'}
    * 输出输出差集，既a存在b不存在：print(a-b)  #输出{'a', 'i', 'm'}
    * 消除重复的元素，使元素唯一：print(set(a)) #输出{'a', 'i', 'd', 'e', 'n', 'l', 'g', 'm'}
### 八、函数
* 定义函数
```python
def fun():
  print("这是我的第一个函数")
```
* 调用函数
```python
fun()
```
### 九、切片
* 定义一个字符串例子：c="Iamlegend"
  * print(c[0]) #I(下标开始为0)
  * print(c[0:2]) #Ia(从0开始取，取到1，最后一个2是不算的)
  * print(c[:5]) #Iamle(从0开始取，取到4，，最后一个5是不算的)
  * print(c[5:]) #gend(从第5个字符开始取，取到最后一个)
  * print(c[5:7]) #ge(取5、6两个字符，最后一个7是不算的)
### 十、模块
* 引入模块
```python
import sys
```
* 安装第三方模块(例如requests、re、beautifulsoup等)
```python
pip install requests(用cmd命令进入python的Scripts目录，输入该命令来安装requests，个人觉得这是最方便的)
```
### 十一、正则
* 用\d可以匹配一个数字，\w可以匹配一个字母或数字
* 用*表示任意个字符（包括0个）
* 用+表示至少一个字符
* 用?表示0个或1个字符
* 用{n}表示n个字符
* 用{n,m}表示n-m个字符
* ^表示行的开头，^\d表示必须以数字开头
* $表示行的结束，\d$表示必须以数字结束
  * 基本所使用方法
    * （1）如果要匹配'010-12345'这样的号码呢？由于'-'是特殊字符，在正则表达式中，要用'\'转义，所以，上面的正则是\d{3}\-\d{3,8}
    * （2）[0-9a-zA-Z\_]可以匹配一个数字、字母或者下划线
  * findall的使用方法(定义一个字符串例子secord='aeasdxxIxxqewexxLovexxwerxxyouxxguyg')
    * （1）贪婪算法re.findall('xx.*xx',secord) (输出从最开始的xx到最后的xx)，输出为['xxIxxqewexxLovexxwerxxyouxx']
    * （2）非贪婪算法re.findall('xx.*?xx',secord) (从最开始的xx和第二个的xx，依次下去)，输出为['xxIxx', 'xxLovexx', 'xxyouxx']
    * （3）无敌算法（个人觉得非常爽）re.findall('asdxx(.*?)yg',secord) （输出asdxx到yg之间内容），输出['IxxqewexxLovexxwerxxyouxxgu']
  * sub替换某段字符
    * re.sub('123(.*?)123','123789123',s) #查找s字符串开头为123结尾为123的的字符串，替换成123789123
  * search查找
    * re.search('<title>(.*?)123(.*?)</title>',neirong).group(1) #group的值是根据有几个括号来获取内容，确定只有一个内容是效率比findall高
### 十二、继承
  * 单继承
    使用方法ClassA（B）
  * 多继承
    使用方法class C(A, B, X): 注意果多个父类有相同的类名，那么先使用左边的第一个父类
### 十三、异常处理
```python
try:
<语句>        #运行别的代码
except <名字>：
<语句>        #如果在try部份引发了'name'异常
except <名字>，<数据>:
<语句>        #如果引发了'name'异常，获得附加的数据
else:
<语句>        #如果没有异常发生
```
### 十四、文件操作
```python
f=open('user.txt','a',encoding='utf8')  #a是文件的追加写入
f.write("这是写入内容"+'\n')  #写入内容
f.close() #关闭
```
### 十五、Lambda函数（被用来创建一个函数对象，并且将值返回给他们）
    格式：lambda 参数：表达式
  * 例子一：
```python
a=lambda x:x+3  print(a(1))
```
  * 例子二：
```python
b=lambda x,y,z:x+y      #声明了多少个参数就要给多少个参数，即这里必须是3个
print(b(1,2,3))
```
  * 例子三：
```python
def d(t):
    return lambda y:y+t
d1=d(7)                 #这里把7当作是t，即d1==lambda y:y+7
print(d1(10))           #这里相当于把y=10传进lambda表达式
```
