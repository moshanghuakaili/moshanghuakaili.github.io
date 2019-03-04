---
title: tensorflow-tf.nn.conv2d
date: 2018-08-26
type: 1
category: Piece study
---

&nbsp;tensorflow-tf.nn.conv2d 

实现卷积的函数，常常用来做图像处理
```
​tf.nn.conv2d(
    input,
    filter,
    strides,
    padding,
    use_cudnn_on_gpu=True,
    data_format='NHWC',
    dilations=[1, 1, 1, 1],
    name=None
)
```

### 参数
+ input  
  - Tensor (4-D [ batch, in_height, in_width, in_channels])，四者的顺序根据 data_format 的设置可以变化
  - types: half, bfloat16, float32, float64
  - 可以理解为要做卷积的图像，四维Tensor可以理解为 [ 图片数, 图的高度, 图的宽度,  图的通道数]
+ filter 
  - Tensor (4-D [filter_height, filter_width, in_channels, out_channels])
  - type 与input相同 
  - 卷积核 [卷积核高度, 卷积核宽度, 图的通道数-与input保持一致 
, 卷积核数量]
+ strides 
  - Tensor 长度为4的1D Tensor [ batch, in_height, in_width, in_channels] 顺序与 data_format 相同
  - 卷积时在图像每一维的步长
  - type: int s
+ padding 
  - 取值 “SAME” or “VALID”，选择padding算法
  - “SAME”和“VALID”的区别所在：若X为2*3的变量，卷积核长宽为2*2，卷积核步长为2，当向右滑动两步之后，“VALID”方式发现余下的窗口不到2*2会直接将第三列舍弃，而“SAME”方式并不会把多出的一列丢弃，只有一列了不够2*2，填充0
+ use_cudnn_on_gpu 
  - bool True or False，默认True
+ data_format 
  - 取值 “NHWC” or “NCHW”，默认”NHWC” ，对应 [batch, height, width, channels]
+ dilations 
  - Tensor 长度为4的1D Tensor，默认为[1,1,1,1]
  - type: int s
+ name

###  源码如下
 
```
​# tf.nn.conv2d
x_shape = [1,4,4,1]
x_val = tf.constant([[[[1.],[2.],[3.],[4.]],
                      [[2.],[3.],[4.],[1.]],
                      [[3.],[4.],[1.],[2.]],
                      [[4.],[1.],[2.],[3.]]]]) #1*4*4*1
my_filter = tf.constant(0.25,shape=[2,2,1,1]) #2*2的卷积核
my_strides = [1,2,2,1] #步长宽高均为2
convolution_layer = tf.nn.conv2d(x_val,my_filter,my_strides,padding='SAME')
print(sess.run(convolution_layer))
```

----
|原矩阵 | 卷积矩阵 | 结果 |
|-----|-----|-----|
|1 2 3 4|           | |
|2 3 4 1|0.25 0.25|2 3|
|3 4 1 2|0.25 0.25|3 2|
|4 1 2 3|      | |
---


> 参考：https://tensorflow.google.cn/api_docs/python/tf/nn/conv2d 
https://blog.csdn.net/zuolixiangfisher/article/details/80528989 
http://www.cnblogs.com/qggg/p/6832342.html
