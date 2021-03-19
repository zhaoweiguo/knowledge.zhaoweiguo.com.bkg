常用
####

深度学习适合做::

    接近人类水平的图像分类
    接近人类水平的语音识别
    接近人类水平的手写文字转录
    更好的机器翻译
    更好的文本到语音转换
    数字助理，比如谷歌即时(Google Now)和亚马逊 Alexa
    接近人类水平的自动驾驶
    更好的广告定向投放，Google、百度、必应都在使用
    更好的网络搜索结果
    能够回答用自然语言提出的问题
    在围棋上战胜人类


two essential characteristics of how deep learning learns from data::

    1. the incremental, layer-by-layer way in which 
        increasingly complex representations are developed, 
    2. the fact that these intermediate incremental representations are learned jointly, 
        each layer being updated to follow both the representational needs of the layer above 
        and the needs of the layer below. 
    深度学习从数据中进行学习时有两个基本特征:
    第一，通过渐进的、逐层的方式形成越来 越复杂的表示;
    第二，对中间这些渐进的表示共同进行学习，每一层的变化都需要同时考虑上 下两层的需要

::
    
    1. shadllow learning problems:
        gradient boosting machines  -> XGBoost
    2. perceptual problems:
        deep learning               ->  Keras


::

    strong AI: 通用人工智能
    Weak AI: 专业人工智能


层(Layers)::

    不同的张量格式与不同的数据处理类型需要用到不同的层。
    Different layers are appropriate for different tensor formats and different types of data processing.

    1. 简单的向量数据保存在 形状为 (samples, features) 的 2D 张量中，通常用密集连接层来处理。
        [也叫全连接层()或密集层()，对应于 Keras 的 Dense 类]
    1. simple vector data, stored in 2D tensors of shape (samples, features), 
        is often processed by densely connected layers, 
        also called fully connected or dense layers (the Dense class in Keras).
    说明:
    densely connected layer: 密集连接层
    fully connected layer: 全连接层
    dense layer: 密集层

    2. 序列数据保存在形状为 (samples, timesteps, features) 的 3D 张量中，通常用循环层(比如 Keras 的 LSTM 层)来处理。
    2. Sequence data, stored in 3D tensors of shape (samples, timesteps, features), 
        is typically processed by recurrent layers such as an LSTM layer. 
    说明:
    recurrent layer: 循环层

    3. 图像数据保存在 4D 张量中，通常用二维卷积层(Keras 的 Conv2D)来处理。
    3. Image data, stored in 4D tensors, is usually processed by 2D convolution layers (Conv2D).
    说明:
    2D convolution layers (Conv2D): 二维卷积层(Keras 的 Conv2D)

损失函数(loss function)::

    对于二分类问题，你可以使用二元交叉熵(binary crossentropy)损 失函数;
    binary crossentropy for a two-class classification problem

    对于多分类问题，可以用分类交叉熵(categorical crossentropy)损失函数;
    categorical crossentropy for a many-class classification problem

    对于回归问题，可以用均方误差(mean-squared error)损失函数;
    mean-squared error for a regression problem

    对于序列学习问题，可以用联结主义 时序分类(CTC，connectionist temporal classification)损失函数
    connectionist temporal classification (CTC) for a sequence-learning problem








