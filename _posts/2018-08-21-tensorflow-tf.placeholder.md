---
title: tensorflow-tf.placeholder
date: 2018-08-21
type: 1
category: Piece study
---

&nbsp;tensorflow-tf.placeholder

```
​tf.placeholder(
    dtype,
    shape=None,
    name=None
)​
```

### 参数
+ dtype: The type of elements in the tensor to be fed.（tf.float32,tf.float64,...)
+ shape: The shape of the tensor to be fed (optional). If the shape is not specified, you can feed a tensor of any shape[rows, cols] rows 或者cols 取值为None 表示不定
+ name: A name for the operation (optional).

###  源码如下
不能直接运算。必须在Session.run() ,Tensor.eval(), 或者Operation.run()中被 "feed_dict" 喂入数据，否则会报错
```
​@tf_export("placeholder")

def placeholder(dtype, shape=None, name=None):

  """Inserts a placeholder for a tensor that will be always fed.



  **Important**: This tensor will produce an error if evaluated. Its value must

  be fed using the `feed_dict` optional argument to `Session.run()`,

  `Tensor.eval()`, or `Operation.run()`.



  For example:



  ```python

  x = tf.placeholder(tf.float32, shape=(1024, 1024))

  y = tf.matmul(x, x)



  with tf.Session() as sess:

    print(sess.run(y))  # ERROR: will fail because x was not fed.



    rand_array = np.random.rand(1024, 1024)

    print(sess.run(y, feed_dict={x: rand_array}))  # Will succeed.

  ```



  @compatibility(eager)

  Placeholders are not compatible with eager execution.

  @end_compatibility

  
  Args:

    dtype: The type of elements in the tensor to be fed.

    shape: The shape of the tensor to be fed (optional). If the shape is not

      specified, you can feed a tensor of any shape.

    name: A name for the operation (optional).



  Returns:

    A `Tensor` that may be used as a handle for feeding a value, but not

    evaluated directly.



  Raises:

    RuntimeError: if eager execution is enabled

  """

  if context.executing_eagerly():

    raise RuntimeError("tf.placeholder() is not compatible with "

                       "eager execution.")



  return gen_array_ops.placeholder(dtype=dtype, shape=shape, name=name)​
```


> 参考：https://tensorflow.google.cn/api_docs/python/tf/placeholder