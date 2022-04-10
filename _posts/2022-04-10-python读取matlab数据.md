---
layout: post
title: python读取matlab数据Tile
date: 2022-04-09
tags: [matlab,python]
toc:  true
---
# python读取matlab数据(.mat文件)

我们都知道，matlab是一个非常好用的矩阵计算分析软件，然额，matlab自带的绘图效果极为锯齿，所以，这里分享一个在python中读取matlab处理后的数据.mat文件。

1.首先，我们这里先打开matlab，随便在命令行窗输入两个变量，

```matlab
matlab_x=1:0.01:10;
matlab_y=sin(matlab_x);
```

2.计算处理后，matlab右边的工作区会有两个变量值，分别为matlab_y、matlab_x

![](https://project1002.oss-cn-beijing.aliyuncs.com/matlab/Snipaste_2021-08-26_15-01-50.png)

3.然后，我们将鼠标放置在工作区**空白位置**右键，选择**保存**，也可以在工作区处于工作高亮状态时使用快捷键ctrl+s进行保存，会弹出保存文件名，这里我们保存为matlab.mat

![image-20210826151017831](https://project1002.oss-cn-beijing.aliyuncs.com/matlab/image-20210826151017831.png)

4.接下来就是用Python读取上一步中保存的matlab工作区的数据Data。Python中我们需要用到scipy库，这里我们先import进去

```python
import scipy.io as scio
```

5.读取.mat文件

```python
data=scio.loadmat('./matlab.mat')
```

6.查看当前data数据类型

```python
type(data)
```

输出的为dict字典类型

7.读取对应我们想要的数据

这里我们假设需要将数据matlab_y读进python中（这里我们用numpy库将数据转化为数组类型）

```python
import numpy as np #导入矩阵处理库
python_y=np.array(data['matlab_y']) #将matlab数据赋值给python变量
```

至此，就完成了使用python读取matlab数据。

**enjoy it！**