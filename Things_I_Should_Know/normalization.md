##关于正则化项及其作用

* 线性规划为例。输入x1,x2,....xn，输出y, 为求得线性变换w，如果w的形式极为复杂，
  它通常可以完美的拟合训练数据。然而这并不是很好，已经成为过拟合。为了不让过拟合出现即加入正则化项。

* 0范数
　0范数正则化项使得函数成为凸函数，并且约束解w中的非零项的个数。

* l1　范数
　1范数正则化项使得函数成为凸函数，Lasso
 
* l2范数
　2范数也是使得函数成为凸函数，Ridge Regression。其中2范数最好求解。
 ![L2norm](NumberedEquation2.gif)
 refer to : [Frobenius Norm](http://mathworld.wolfram.com/FrobeniusNorm.html)

* F范数

