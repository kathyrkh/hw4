## 数字图像处理作业四

###                        ——空域滤波



###### 姓名：任珂含 

###### 班级：自动化少61 

###### 学号：2140506104

###### 提交日期：2019.3.19



###### *摘要：*

​	*本次作业使用matlab对所给图像进行了空域中值滤波、高斯滤波以及空域高通滤波的处理。*



##### 1.空域低通滤波器

​	要求：分别用高斯滤波器和中值滤波器去平滑测试图像test1和2，模板大小分别是3x3 ， 5x5 ，7x7； 分析各自优缺点。

​	**中值滤波**是一种非线性平滑技术，它将每一像素点的灰度值设置为该点某邻域窗口内的所有像素点灰度值的中值，对去椒盐噪声十分有效。中值滤波可以使用matlab中的medfilt2函数实现。

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/me1.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/me2.png)

​	**高斯滤波**是一种线性平滑滤波，适用于消除高斯噪声，广泛应用于图像处理的减噪过程。高斯滤波是对整幅图像进行加权平均的过程，每一个像素点的值都由其本身和邻域内的其他像素值经过加权平均后得到。具体操作是：用一个模板（或称卷积、掩模）扫描图像中的每一个像素，用模板确定的邻域内像素的加权平均灰度值去替代模板中心像素点的值。matlab中可使用fspecial('gaussian',[n n])和imfilter函数实现图像的高斯滤波。

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/me3.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/me4.png)

​	可以看出，对于test1中的白色点线状噪声，中值滤波效果很好，用高斯滤波就无法去除这些噪声。但中值滤波模板较大时会导致平滑的结果过于模糊，信息丢失。对于test2图像，高斯滤波的平滑效果更好。



##### 2.产生高斯滤波器

​	要求：利用固定方差 sigma=1.5产生高斯滤波器.。附件有产生高斯滤波器的方法，分析各自优缺点。

 	matlab中使用fspecial函数的gaussian类型时有两个参数，hsize表示模板尺寸，默认值为[3 3]，sigma为滤波器的标准差，单位为像素，默认值为0.5。以下是sigma=0.5和sigma=1.5时的平滑效果比较。



![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/gau1.png)





![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/gau2.png)

​	可以看出增大sigma后平滑效果更明显了。sigma增大后图上噪声有所减弱，对于test1，原本的白色点线噪声被模糊掉了一些，但仍然没有消失。可见高斯滤波并不擅长处理这种噪声。对于test2，一些手部的噪声被平滑得较好。

​	同时sigma增大后，平滑效果变好意味着图片清晰度有所降低。观察女郎的发丝能够看得比较明显。



##### 3.空域高通滤波器

​	要求：利用高通滤波器滤波测试图像test3,4：包括unsharp masking, Sobel edge detector, and Laplace edge detection；Canny algorithm.分析各自优缺点。

结果如下：

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/gt2.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/yt2.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/gt1.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/yt1.png)

​	对比发现，默认参数下unsharp masking的锐化效果并不明显。将锐化强度调到2，锐化效果明显多了，例如房屋的砖块边缘更清晰，黑白方块的边界也减少了模糊感：

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/um4.png)

![](https://raw.githubusercontent.com/kathyrkh/rkhimages/master/um3.png)

- ​	此时能够看出unsharp masking的锐化效果，但test3方块的直线边界产生了一些不平整噪声。
- ​	Sobel edge detector对test4房屋的提取边界效果较好，但对于test3方块，提取直线边界时不平整。
- ​	Laplace edge detection未能提取出test4房屋的边界。但对于test3方块提取的直线边界效果较好。
- ​	Canny algorithm也能够提取边缘，但对于test3方块提取的边缘不够平整，还在图像最外一圈提取出了人眼根本看不到且其他方法都没有显示出的边界。对于test4房屋这种方法提取出的边界过多了。



##### 参考文献：

[1] 冈萨雷斯等，数字图像处理（第三版）, 电子工业出版社，2005.

