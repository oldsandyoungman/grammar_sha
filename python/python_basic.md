> 上王桥的数字图像与视频处理，之后的作业要用到很多语法，希望自己不要在工具上被卡住，毕竟我的时间没有多。开此章，加油！



[TOC]

# python的基础语法

> 来自王涵老哥的整理，很细心，点个赞



### 1. 列表 `list` ：中括号`[]`

```python
classmates = ['1', '2', '3']
```

> 元素不一定要统一，可以类型完全不一样



##### (1) 求列表长度

```python
len(classmates)
```

##### (2) 取元素

```python
classmates[0]
classmates[-1]
classmates[0:5] # 左开右闭 [0,5)
classmates[::2] # 每隔两个点取元素
```

##### (3) 加元素

```python
classmates.append('4')
```

##### (4) 删除末尾元素

```python
classmates.pop()
```

##### (5) 更改元素

```python
classmates[-1] = '6'
```



### 2. range

##### (1) 一个参数：range(10) = [0, 10)

##### (2) 两个参数：range(3,9) = [3, 9)





### 3. for循环



##### (1) 列表 `list` 循环

```python
nums = [2,3,4,5,6,7]
for num in nums:
    print(num)
for num in nums[:6]:
    print(num)
for num in range(4, len(nums)):
    print(num)
```



##### (2) 元组for循环

```python
def transfer(x,y):
    r = np.sqrt(x*x+y*y)
    q = np.arctan(y/x)/math.pi
    return r, q

a=np.random.randint(20,size=20).reshape(10,2) # numpy.ndarray

b=[] # list
for x,y in zip(a[:,0],a[:,1]):
    b.append(transfer(x,y)) # b[0]: tuple格式
b=np.array(b).reshape(10,2)
print("a = \n",a)
print("b = \n",b)
```





### 4. while 循环

##### (1) 普通判断条件

```python
i = 0
nums = [2,3,4,5,6,7]
while(i<len(nums)):
    print(nums[i])
    i++
```







### 5. 数学运算函数

```python
abs(-19)
max(1,5)
min(1,5)
```





### 6. 第三方库函数

##### (1) 公用库

```python
import os
os.getcwd() # 当前路径
```

##### (2) 自定义函数 

```python
### myFunction.py
### import math
### def myFunc(name):
###    print("Hello "+name+"!")

from myFunction import myFunc
myFunc("Tony")
```





### 7. 打印函数

##### (1) 数值插入

```python
print('i=%d,j=%d'%(1,2))
```





### 8. 元组

##### (1) 元组取值

```python
a = (1,2,3)
a[0]
```





### 9. 字典

> 键值只能是不可变型变量：数值，字符串，元组

##### (1) 初始化

```python
d = dict()
d = {}
d = {1:2}
```

##### (2) 取值赋值

```python
print(d[1]) # 如果不存在会报错
d[1]=1
```

##### (3) 判断是否存在

```python
if (1 in d):
    print('存在')
if d.get('Thomas', -1)==-1
	print('不存在')
if (d.get(2)==None):
    print('无')
```

##### (4) 判断是否存在

```python
if (1 in d):
    print('存在')
```







### 10. 画图

##### (1) 图像/矩阵，注意彩色和灰色参数不一样

```python
plt.subplot(121)
plt.title('3.origin')
# 彩色显示
plt.imshow(img_rgb)
plt.axis('off')
plt.subplot(122)
plt.title('3.result')
# 灰色显示
plt.imshow(img_merge, cmap='gray')
plt.axis('off')
plt.show()
```



##### (2) 向量/折线

```python
import matplotlib as mpl
import matplotlib.pyplot as plt

count = np.zeros((256,), dtype=int)
plt.plot(count)
plt.show()
```









### 11. 运算符

##### (1) ** 幂运算

```python
a = 2
b = 3
a**b  # 8
```



##### (2) / 和 //

```python
a = 9
b = 3
a/b  # 3.0
a//b  # 3
```













### #. 其它细节

#### 1. True/False/None 要大写

#### 2. 中括号`[]`是列表