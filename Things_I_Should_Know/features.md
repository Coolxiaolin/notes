## Local descriptors

* HOG

  方向梯度直方图（Histogram of Oriented Gradient, HOG）（本质：梯度的统计信息，而梯度主要存在于边缘的地方）
  
  [HOG的实现](http://blog.csdn.net/liulina603/article/details/8291093)
  
HOG特征提取方法就是将一个image（你要检测的目标或者扫描窗口）：

1）灰度化（将图像看做一个x,y,z（灰度）的三维图像）；

2）采用Gamma校正法对输入图像进行颜色空间的标准化（归一化）；目的是调节图像的对比度，降低图像局部的阴影和光照变化所造成的影响，同时可以抑制噪音的干扰；

3）计算图像每个像素的梯度（包括大小和方向）；主要是为了捕获轮廓信息，同时进一步弱化光照的干扰。

4）将图像划分成小cells（例如6*6像素/cell）；

5）统计每个cell的梯度直方图（不同梯度的个数），即可形成每个cell的descriptor；

6）将每几个cell组成一个block（例如3*3个cell/block），一个block内所有cell的特征descriptor串联起来便得到该block的HOG特征descriptor。

7）将图像image内的所有block的HOG特征descriptor串联起来就可以得到该image（你要检测的目标）的HOG特征descriptor了。这个就是最终的可供分类使用的特征向量了。
  
* HOF

Based on histograms of oriented (spatial) gradients (HOG) + histogram of optical flow (HOF)

* MBH

Motion Boundary Histogram


## Gobal Descriptor

* Fisher Vector
![Fisher Vector 是怎么用的](Things_I_Should_Know/FisherVector.png)

这个概念不大懂，后面要再看看
[一个解释](http://www.cnblogs.com/jie-dcai/p/5740480.html)

* PCA

 m = mean(Y);　　　　　　　　　　　　　　　　　　　 * 求均值
 
 Yi = Y - repmat(m, size(Y,1), 1);　　　　　　　 * 
 
 R = (Yi'*Yi) / size(Yi,1);　　　　　　　　　　　 * 求协方差 Con
 
 [V,D] = eig(R);　　　　　　　　　　　　　　　　　　* 求特征值，　这里按大小特征值排序，只取对应特征值大的那些特征向量。就是ＰＣＡ
 
 D = diag(D);　　　　　　　　　　　　　　　　　　　 * 取特征值
 
 WhiteT = V*diag(1./sqrt(D+0.001))*V';　　　　　* 白化
 
 T_inv = V*diag(sqrt(D+0.001))*V';
 
 Y = Yi * WhiteT;
