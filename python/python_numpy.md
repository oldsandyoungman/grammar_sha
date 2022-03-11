> 上王桥的数字图像与视频处理，之后的作业要用到很多语法，希望自己不要在工具上被卡住，毕竟我的时间没有多。开此章，加油！



[TOC]

# python的numpy库

> 来自王涵老哥的整理，很细心，点个赞



### 1. 初始化一个矩阵

> numpy 里的矩阵，都是 numpy.ndarray 格式
>
> ```python
> aa = [[1,2,3],[4,5,6]]
> type(aa) # list
> a = np.array(aa)
> type(a) # numpy.ndarray
> type(a[1]) # numpy.ndarray
> ```



##### (1) 零矩阵

```python
a = np.ones((2,3),dtype=int)
```

##### (2) 单位矩阵

```python
b = np.zeros((2,3),dtype=int)
b = np.zeros((2,3))
```

##### (3) 顺序矩阵

```python
c = np.arange(32).reshape(4,8)
```

##### (4) 用 python 的 list 初始化

```python
a = np.array([[1,2,3],[4,5,6]])
a[1] # array([4, 5, 6])
```

##### (5) 用 元组 初始化

```python
a = (1,2) # <class 'tuple'>
b = np.array(a) # <class 'numpy.ndarray'>
```

##### (6) 随机值矩阵

```python
# [0,20)内的随机数
a=np.random.randint(20,size=20).reshape(10,2)
```





### 2. 矩阵的取值赋值

##### (1) 一维矩阵取值赋值

```python
c = np.arange(32)
c[1:3]
c[1:]
```



##### (2) 二维矩阵取值赋值

```python
a = np.ones((2,3),dtype=int)
a[:,1] # :等于所有行都取
a[[0,9],:]=1 a[[0,9]]=1 # 第1行和第10行赋值为1
a[:, [0,9]]=1 # 第1列和第10列赋值为1
```



##### (3) 判断条件取值（会改变维数）

```python
b = np.array([[4,3],[2,1]])
b[b<4] # array([3, 2, 1])
b[(b<4) & (b>1)] # array([3, 2])
```



##### (4) 矩阵倒序输出

```python
# 行逆序输出
matrix = matrix[::-1, :]
# 列逆序输出
matrix = matrix[:, ::-1]
```





### 3. 矩阵相乘

##### (1) 普通相乘 *（对应位置相乘）

```python
f = np.array([1,2,3])
g = np.array([4,5,6])
f*g # array([ 4, 10, 18])
```



##### (2) 点乘 dot

```python
f = np.array([1,2,3])
g = np.array([4,5,6])
np.dot(f,g) # 32
f.dot(g) # 32
```





### 4. 矩阵的性质

##### (1) 取维数

```python
e = np.array([1,2,3])
f = np.array([[1,2,3]])
g = np.ones((2,3), dtype=int)
e.shape # (3,)
f.shape # (1,3)
g.shape # (2,3)
```







### 5. 矩阵转置

```python
g = np.ones((2,3), dtype=int)
g.T
```





### 6. 最小值所在索引

```python
# 距离5.2最近的值的索引
np.argmin(np.abs(np.array([2,3,1,4,5,7,0])-5.2))
```





### 7. 元组变数组

```python
a = (1,2) # <class 'tuple'>
b = np.array(a) # <class 'numpy.ndarray'>
```





### 8. 设置打印完整程度

```python
import numpy as np
np.set_printoptions(threshold=np.inf)
```



### 9. 矩阵求逆

```python
import numpy as np

a  = np.array([[1, 2], [3, 4]])  # 初始化一个非奇异矩阵(数组)
# 方法一
print(np.linalg.inv(a))  # 对应于MATLAB中 inv() 函数

# 方法二 矩阵对象可以通过 .I 更方便的求逆
A = np.matrix(a)
print(A.I)
b = np.array(A.I)
```



### 10. 数组填充

```python
import numpy as np

# h: 高度上补全的数量
# w: 宽度上补全的数量

# ‘constant’——表示连续填充相同的值，每个轴可以分别指定填充值，constant_values=（x, y）时前面用x填充，后面用y填充，缺省值填充0
# ‘edge’——表示用边缘值填充
# ‘linear_ramp’——表示用边缘递减的方式填充
# ‘maximum’——表示最大值填充
# ‘mean’——表示均值填充
# ‘median’——表示中位数填充
# ‘minimum’——表示最小值填充
# ‘reflect’——表示对称填充
# ‘symmetric’——表示对称填充
# ‘wrap’——表示用原数组后面的值填充前面，前面的值填充后面

img = np.pad(img, (h, w), 'reflect')
```







### #. 其它细节

#### 1. True/False/None 要大写

#### 2. 中括号`[]`是列表