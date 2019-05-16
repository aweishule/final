#<center> 数字图像处理直线检测</center>

------

<center>自动化少61</center>

<center>魏俊哲</center>

<center>2140506024</center>

<center>2019.5.16</center>



> 1. 首先对测试图像（文件名为：test1~test6）进行边缘检测，可采用书上介绍的Sobel等模板或者canny算子方法；

### 原理说明
Canny边缘检测算法可以分为以下5个步骤：
1)        使用高斯滤波器，以平滑图像，滤除噪声。
2)        计算图像中每个像素点的梯度强度和方向。
3)        应用非极大值（Non-Maximum Suppression）抑制，以消除边缘检测带来的杂散响应。
4)        应用双阈值（Double-Threshold）检测来确定真实的和潜在的边缘。
5)        通过抑制孤立的弱边缘最终完成边缘检测。
Sobel算子是像素图像边缘检测中最重要的算子之一，在机器学习、数字媒体、计算机视觉等信息科技领域起着举足轻重的作用。在技术上，它是一个离散的一阶差分算子，用来计算图像亮度函数的一阶梯度之近似值。在图像的任何一点使用此算子，将会产生该点对应的梯度矢量或是其法矢量。
利用matlab提供的edge函数，参数选择为canny和sobel即可方便实现。


### 处理结果
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test1.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test2.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test3.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test4.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test5.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test6.bmp)

### 结果分析
 可以明显看出sobel处理后的图像边缘线更稀少，canny处理后边缘更密集。
> 2. 在边缘检测的基础上，用hough变换检测图中直线；

### 原理说明
hough变换过程
1.去噪（高斯核）
2.边缘提取（梯度算子、拉普拉斯算子、canny； 此处实现用sobel） 
3.二值化（判断此处是否为边缘点，就看灰度值==255）
4.映射到霍夫空间（此处准备两个容器，一个CImg用来展示hough-space概况，一个数组hough-space用来储存voting的值，因为投票过程往往有某个极大值超过255，多达几千，不能直接用灰度图来记录投票信息）
5.取局部极大值，设定阈值，过滤干扰直线
6.绘制直线、标定角点
使用matlab函数hough可以方便实现。
### 处理结果
使用canny处理的结果
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test1%20hough.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test2%20hough.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test3%20hough.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test4%20hough.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test5%20hough.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test6%20hough.bmp)
使用sobel处理的结果
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test1%20hough%20s.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test2%20hough%20s.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test3%20hough%20s.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test4%20hough%20s.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test5%20hough%20s.bmp)
![Aaron Swartz](https://raw.githubusercontent.com/aweishule/final/master/test6%20hough%20s.bmp)

> 3比较不同边缘检测算法（2种以上）、不同hough变换参数对直线检测的影响；

### 结果分析
可以看出使用sobel和canny边缘检测对直线检测的影响很大，两者变换后选取的点不同，检测出的直线也不同。整体上看sobel边缘检测对直线检测的效果更好。


### 附录
参考文献：Rafael C. Gonzalez., et al. 数字图像处理（第三版）, 电子工业出版社，2011.

