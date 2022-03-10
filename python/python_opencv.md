> 上王桥的数字图像与视频处理，之后的作业要用到很多语法，希望自己不要在工具上被卡住，毕竟我的时间没有多。开此章，加油！



[TOC]

# python的opencv库

> 来自王涵老哥的整理，很细心，点个赞



### 1. 图片处理

##### (1) 图片读取

```python
# cv2.imread(img_path, flags)
# * flags=1：读取彩色图，默认为BGR方法； 等同于cv2.IMREAD_COLOR
# * flags=0：读取为灰度图；          等同于cv2.IMREAD_GRAYSCALE

img_raw = cv2.imread('../pic/cham.jpg', flags = 1)# 读取图片 BGR
img_raw = cv2.imread('/root/project/digital_image_process_assistant/pic/cham.jpg')
print(type(img_raw)) # numpy.ndarray
print(img_raw.dtype) # uint8(读图片默认uint8，np.zeros()默认是float64)
```

##### (2) 图片转通道

```python
img_rgb = cv2.cvtColor(img_raw,cv2.COLOR_BGR2RGB) #将BGR转为RGB
img_gray = cv2.cvtColor(img_raw, cv2.COLOR_BGR2GRAY) #将BGR转为灰度
```

##### (3) 图像保存

```python
cv2.imwrite('./champ_1.png',img_rgb)
```

##### (4) 图像维度

```python
print(img_gray.shape) # tuple
```

##### (5) 图像数据格式

```python
print(img_gray.dtype) # uint8 / float64
```

##### (6) 图像数据格式转换

```python
img_new2 = img_new2.astype(np.uint8)
```

##### (7) 图像拷贝

```python
img_new1 = img_gray.copy()
```





### 2. 图片操作

##### (1) 图片像素取反

```python
reverse_gray = 255 - img_gray
```

##### (2) 图片增强亮度

（1）遍历方法

```python
# 如果越界，会从0继续算，例如255*1.2=306，最终值是306-256=50，即会有白突然变黑的过程
print(img_gray.dtype) # uint8
random_img = np.zeros(img_gray.shape, dtype=np.uint8)
for i in range(img_gray.shape[0]):
    for j in range(img_gray.shape[1]):
        if img_gray[i, j]*1.2 > 255:
            random_img[i, j] = 255
        else:
            random_img[i, j] = img_gray[i, j]*1.2
```

（2）广播方法

```python
# 没加越界处理
print(img_gray.dtype) # uint8
img_new2 = 1.2*img_gray # (uint8)255 -> (float64)306.0
print(img_new2.dtype) # float64
img_new2 = img_new2.astype(np.uint8) # (float64)306.0 -> (uint8)50
print(img_new2.dtype) # uint8

# 加了越界处理
print(img_gray.dtype) # uint8
img_new2 = 1.2*img_gray # (uint8)255 -> (float64)306.0
print(img_new2.dtype) # float64

img_new2[img_new2>255] = 255

img_new2 = img_new2.astype(np.uint8) # (float64)306.0 -> (uint8)50
print(img_new2.dtype) # uint8
```



##### (3) 分辨率调节

```python
# cv2.resize(img, (width, height), interpolation = cv2.INTER_LINEAR)
# interpolation:
# cv2.INTER_LINEAR： 双线性插值，默认情况使用
# cv2.INTER_NEAREST： 最邻近插值
# cv2.INTER_AREA： 使用像素区域关系重新采样，和cv2.INTER_NEAREST相似
# cv2.INTER_CUBIC： 4x4像素邻域内的双立方插值

W,H = (1000,1000)
img_resize = cv2.resize(img_rgb, (W,H), interpolation = cv2.INTER_LINEAR)
print('img_resize.shape:', img_resize.shape)
```

##### 



### #. 其它细节

#### 1. True/False/None 要大写

#### 2. 中括号`[]`是列表