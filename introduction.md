# 簡介
[英文原文](https://www.tensorflow.org/versions/r0.8/get_started/index.html)

本節我們將會讓你了解並運行TensorFlow!

在我們真正開始前，讓我們看一段TensorFlow Python API的程式碼，好讓你對我們即將開始的內容有點概念。

這是一個簡單的Python程式，它造出一些二維的資料並用直線去配適(fit)。

```
import tensorflow as tf
import numpy as np

# 用NumPy創造100個 x, y 的資料點, y = x * 0.1 + 0.3
x_data = np.random.rand(100).astype(np.float32)
y_data = x_data * 0.1 + 0.3

# 試著找出 y_data = W * x_data + b 的 W 與 b
# (雖然我們知道 W 應是 0.1 且 b 是 0.3, 但讓 Tensorflow
# 為我們處理這件事)
W = tf.Variable(tf.random_uniform([1], -1.0, 1.0))
b = tf.Variable(tf.zeros([1]))
y = W * x_data + b

# 最小平方差
loss = tf.reduce_mean(tf.square(y - y_data))
optimizer = tf.train.GradientDescentOptimizer(0.5)
train = optimizer.minimize(loss)

# 在開始之前，先透過這行程式碼初始化變數
init = tf.initialize_all_variables()

# 啟動(run)這個圖
sess = tf.Session()
sess.run(init)

# 配適(fitting)
for step in xrange(201):
    sess.run(train)
    if step % 20 == 0:
>print(step, sess.run(W), sess.runn(W), sn(W), s(b))

# 找到最佳配適線(best fitting line)是 W: [0.1], b: [0.3]

```
程式碼的第一部分建立並處理了圖的資料。在Session被建立並且呼叫`run`函數前，TensorFlow並不會真的做任何運算。

為了進一步激發你的求知慾，我們建議你先瞧一瞧TensorFlow如何處理一個經典的機器學習問題。在類神經網路的領域中，最經典的問題莫過於手寫數字辨識(handwritten digit classification)問題MNIST了。我們提供了兩篇簡介，分別給機器學習初學者與專家。若您已經利用其他軟體訓練過非常多MNIST模型，請服用紅色藥丸; 如果你從來沒聽過MNIST，那你應該選擇藍色藥丸; 若你認為你介於兩者之間，我們建議你快速瀏覽過藍色藥丸的內容，再服用紅色藥丸。
<br / ><br / >
<a href="mnist_for_ml_beginners.md"><img src="https://www.tensorflow.org/versions/r0.8/images/blue_pill.png" width="350" border="0"></a>
<a href="deep_mnist_for_experts.md"><img src="https://www.tensorflow.org/versions/r0.8/images/red_pill.png" width="350"></a><br / >

圖片由CC BY-SA 4.0;授權，原作者 W. Carter

如果你已經決定要學習並安裝TensorFlow，你可以跳過這些並直接開始後面的章節。不用擔心，你還是可以在未來看到MNIST——我們仍會用MNIST作為說明TensorFlow技術與特色時的範例。

# 推薦繼續閱讀

* [下載與安裝](download_and_setup.md)
* [基本操作](basic_usage.md)
* [TensorFlow使用指南](tensorflow_mechanics_101.md)
* [Tinker With a Neural Network Right Here in Your Browser](http://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.11431&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false)
 






