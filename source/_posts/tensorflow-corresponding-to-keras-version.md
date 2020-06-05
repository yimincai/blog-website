---
title: Tensorflow與Keras版本對應
id: tensorflow-corresponding-to-keras-version
author: Yi-Min Cai
mathjax: false
date: 2020-06-05 19:43:28
categories: Machine Learning
tags:
    - Tensorflow
    - Keras
    - Linux
    - Ubuntu
    - Python
---
# 摘要

錯誤： `ModuleNotFoundError: No module named 'tensorflow.keras'`

1. Tensorflow、Kears版本對應錯誤
2. import方式錯誤：

<!-- more -->

```python
from tensorflow.keras import layers

# 改成

from tensorflow.python.keras import layers
```

# Tensorflow 與Keras版本對應

| Framework       | Env name (--env parameter) | Description                                    | Docker Image                                                 | Packages and Nvidia Settings                                 |
| :-------------- | :------------------------- | :--------------------------------------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| TensorFlow 1.14 | tensorflow-1.14            | TensorFlow 1.14.0 + Keras 2.2.5 on Python 3.6. | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.14](https://docs.floydhub.com/guides/tensorflow/#tensorflow-114) |
| TensorFlow 1.13 | tensorflow-1.13            | TensorFlow 1.13.0 + Keras 2.2.4 on Python 3.6. | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.13](https://docs.floydhub.com/guides/tensorflow/#tensorflow-113) |
| TensorFlow 1.12 | tensorflow-1.12            | TensorFlow 1.12.0 + Keras 2.2.4 on Python 3.6. | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.12](https://docs.floydhub.com/guides/tensorflow/#tensorflow-112) |
|                 | tensorflow-1.12:py2        | TensorFlow 1.12.0 + Keras 2.2.4 on Python 2.   | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.11 | tensorflow-1.11            | TensorFlow 1.11.0 + Keras 2.2.4 on Python 3.6. | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.11](https://docs.floydhub.com/guides/tensorflow/#tensorflow-111) |
|                 | tensorflow-1.11:py2        | TensorFlow 1.11.0 + Keras 2.2.4 on Python 2.   | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.10 | tensorflow-1.10            | TensorFlow 1.10.0 + Keras 2.2.0 on Python 3.6. | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.10](https://docs.floydhub.com/guides/tensorflow/#tensorflow-110) |
|                 | tensorflow-1.10:py2        | TensorFlow 1.10.0 + Keras 2.2.0 on Python 2.   | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.9  | tensorflow-1.9             | TensorFlow 1.9.0 + Keras 2.2.0 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.9](https://docs.floydhub.com/guides/tensorflow/#tensorflow-19) |
|                 | tensorflow-1.9:py2         | TensorFlow 1.9.0 + Keras 2.2.0 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.8  | tensorflow-1.8             | TensorFlow 1.8.0 + Keras 2.1.6 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.8](https://docs.floydhub.com/guides/tensorflow/#tensorflow-18) |
|                 | tensorflow-1.8:py2         | TensorFlow 1.8.0 + Keras 2.1.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.7  | tensorflow-1.7             | TensorFlow 1.7.0 + Keras 2.1.6 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.7](https://docs.floydhub.com/guides/tensorflow/#tensorflow-17) |
|                 | tensorflow-1.7:py2         | TensorFlow 1.7.0 + Keras 2.1.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.5  | tensorflow-1.5             | TensorFlow 1.5.0 + Keras 2.1.6 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) | [TensorFlow-1.5](https://docs.floydhub.com/guides/tensorflow/#tensorflow-15) |
|                 | tensorflow-1.5:py2         | TensorFlow 1.5.0 + Keras 2.1.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.4  | tensorflow-1.4             | TensorFlow 1.4.0 + Keras 2.0.8 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
|                 | tensorflow-1.4:py2         | TensorFlow 1.4.0 + Keras 2.0.8 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.3  | tensorflow-1.3             | TensorFlow 1.3.0 + Keras 2.0.6 on Python 3.6.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
|                 | tensorflow-1.3:py2         | TensorFlow 1.3.0 + Keras 2.0.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.2  | tensorflow-1.2             | TensorFlow 1.2.0 + Keras 2.0.6 on Python 3.5.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
|                 | tensorflow-1.2:py2         | TensorFlow 1.2.0 + Keras 2.0.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.1  | tensorflow                 | TensorFlow 1.1.0 + Keras 2.0.6 on Python 3.5.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
|                 | tensorflow:py2             | TensorFlow 1.1.0 + Keras 2.0.6 on Python 2.    | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |
| TensorFlow 1.0  | tensorflow-1.0             | TensorFlow 1.0.0 + Keras 2.0.6 on Python 3.5.  | [floydhub/tensorflow](https://hub.docker.com/r/floydhub/tensorflow/) |                                                              |

# 參考資料

- [keras学习- No module named ' tensorflow.keras ' 报错，看清 tf.keras与keras](https://blog.csdn.net/Eric_Blog_CSDN/article/details/88420234)
- [floydhub Environments](https://docs.floydhub.com/guides/environments/)