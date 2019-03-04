---
title: tensorflow-tf.multiply & tf.maltmul
date: 2018-08-21
type: 1
category: Piece study
---

&nbsp;tensorflow-tf.multiply & tf.maltmul

## tf.multiply

```
​tf.multiply(
    x,
    y,
    name=None
)
Return x * y element-wise.
```

### 参数
+ x: A Tensor. Must be one of the following types: bfloat16, half, float32, float64, uint8, int8, uint16, int16, int32, int64,complex64, complex128
+ y: A Tensor. Must have the same type as x
+ name: A name for the operation (optional)
+ 返回值为x 和 y各个元素分别相乘

###  源码如下
tf.multiply(a,b)与a*b的结果相同
一般来说，x 和y 的维度需要相同，输出的值z 和x, y的维度也相同 [3,2]=tf.multiply([3,2],[3,2])，也可以是[3,2]=tf.multiply([3,1],[3,2])
```
​x=tf.constant([1,2,3,4,5,6],shape=[3,2])
y=tf.constant([1,2,3,4,5,6],shape=[2,3])
a=tf.constant([[1,2,3]])
with tf.Session() as sess:

    print("x:\n",sess.run(x))
    print("y:\n",sess.run(y))
    print("a:\n",sess.run(a))
```

```
输出结果：
x:
[[1 2]
[3 4]
[5 6]]
y:
[[1 2 3]
[4 5 6]]
a:
[[1 2 3]]
b:
2
```

```
with tf.Session() as sess:
    print("x*x:\n",sess.run(x*x))
    print("tf.multiply(x,x):\n",sess.run(tf.multiply(x,x)))
    print("tf.multiply(y,a):\n",sess.run(tf.multiply(y,a)))
    print("tf.multiply(y,b):\n",sess.run(tf.multiply(y,b)))
```

```
输出结果：
x*x:
[[ 1 4]
[ 9 16]
[25 36]]
tf.multiply(x,x):
[[ 1 4]
[ 9 16]
[25 36]]
tf.multiply(y,a):
[[ 1 4 9]
[ 4 10 18]]
tf.multiply(y,b):
[[ 2 4 6]
[ 8 10 12]]
```

## tf.matmul

```
​tf.matmul(
    a,
    b,
    transpose_a=False,
    transpose_b=False,
    adjoint_a=False,
    adjoint_b=False,
    a_is_sparse=False,
    b_is_sparse=False,
    name=None
)
```

###  源码如下
就是正常的矩阵乘法运算
```
​print("tf.matmul(x,y):\n",sess.run(tf.matmul(x,y)))
```

```
输出结果：
tf.matmul(x,y):
[[ 9 12 15]
[19 26 33]
[29 40 51]]
```

```
a = tf.constant(np.arange(1, 13, dtype=np.int32),
                shape=[2, 2, 3])
b = tf.constant(np.arange(1, 13, dtype=np.int32),
                shape=[2, 3, 2])
with tf.Session() as sess:
    print("a:\n",sess.run(a))
    print("b:\n",sess.run(b))
    print("tf.matmul(a,b):\n",sess.run(tf.matmul(a,b)))
```

```
输出结果：
a:
[[[ 1 2 3]
[ 4 5 6]]
[[ 7 8 9]
[10 11 12]]]
b:
[[[ 1 2]
[ 3 4]
[ 5 6]]
[[ 7 8]
[ 9 10]
[11 12]]]
tf.matmul(a,b):
[[[ 22 28]
[ 49 64]]
[[220 244]
[301 334]]]
```

> 参考：https://tensorflow.google.cn/api_docs/python/tf/matmul 和 https://tensorflow.google.cn/api_docs/python/tf/multiply