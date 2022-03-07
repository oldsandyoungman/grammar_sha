> 上王桥的数字图像与视频处理，之后的作业要用到很多语法，希望自己不要在工具上被卡住，毕竟我的时间没有多。开此章，加油！



[TOC]

# python的opencv库

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











### #. 其它细节

#### 1. True/False/None 要大写

#### 2. 中括号`[]`是列表