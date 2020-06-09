---
title: Windows 10 建立 Machine Learning 開發環境
id: install-machine-learning-environment-in-windows-10
author: Yi-Min Cai
mathjax: false
date: 2020-06-09 17:28:00
categories: Machine Leraning
tags:
    - Machine Learning
    - Tensorflow
    - Windows
    - Miniconda
    - Visual Studio Code
    - Python
---
# 安裝Python環境（Miniconda）

開啟Chrome (or any others browsers) 下載 [Miniconda](Collecting markdown>=2.6.8)，Miniconda 是 Anaconda 的輕量版本它，使用它是為了彈性調整 Python 環境，開發人員常常會有Python pip/pip3 被自己搞壞的經驗，而使用它之後，若環境損壞只需要在建立一個虛擬環境即可！

<!-- more -->

首先，開啟Miniconda的[下載頁面](https://www.notion.so/yimincai/Windows-Machine-Learning-d29eb73a4d26400ab8dabdd7f56fe202)

![docs-conda-io](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fdocs-conda-io.png?alt=media&token=8142b31a-4550-42ba-a848-825b5d259561)

選擇下載64位元的Miniconda(Python 3.7)版本

![download-conda](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fdownload-conda.png?alt=media&token=b6757c26-bfce-414f-8f1b-9ea6aaa2deba)

安裝Miniconda它，點選『Next』

![install-conda-next](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-next.png?alt=media&token=1ba09768-ef1d-4422-af76-9fa2e58162b2)

同意 User License Agreement，點選『I Agree』

![install-conda-i-agree](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-i-agree.png?alt=media&token=b8f63fa6-4c7b-4c94-9605-e7a38da7af3b)

選擇『Just Me』、『Next』

![install-conda-just-me](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-just-me.png?alt=media&token=c9d309da-889d-4680-82a6-65c2022ead4d)

選擇安裝位置，這邊我採用預設值，也可以依個人習慣點選『Browse .. 』選擇其它安裝位置，『下一步』

![install-conda-destination-folder](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-destination-folder.png?alt=media&token=2e3e7311-a338-402e-98ea-c21755da76ff)

將兩個選項都勾選起來，預設中只勾選了下方的『Register Miniconda3 as my default Python 3.7』，勾選『Add Miniconda3 to my PATH environment variable』是為了讓使用者可以在Command Line 中使用Conda 函數，**在後續建立 Python 虛擬環境時會用到**，所以我們將它勾選起來

![install-conda-add-to-path](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-add-to-path.png?alt=media&token=70189f02-dbf6-4a6a-af02-2d25c5d391c0)

等待安裝完成 .. 安裝完成後選擇『Next』

![install-conda-complete](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-complete.png?alt=media&token=33f45798-45c2-4e33-9aa1-d64cf1f85973)

這樣就安裝完成了，按下『Finish』吧！如果對使用文件有興趣也可以閱讀一下哦！

![install-conda-finish](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Finstall-conda-finish.png?alt=media&token=b286c4de-76d0-42ab-a603-6a776811aeaf)

# 建立 Miniconda 的 Python 虛擬環境

接下來我們來建立 Miniconda 的 Python 虛擬環境，首先我們需要開啟 Command Line ，點選 `Win`  之後搜尋『Command』就會出現啦！

![search-command](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fsearch-command.png?alt=media&token=09648bf7-5f42-4135-9b10-5a329a342198)

黑黑的視窗看起來挺神秘的 .. 

![open-command](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fopen-command.png?alt=media&token=b2659361-b92d-426d-9f5e-cc10113986c2)

我們輸入 `conda info` 確認剛剛安裝的 Miniconda 是否有安裝成功吧！
嗯 .. 版本號等等資訊都出現就代表成功安裝啦！如果出現 `command not found : conda` 的話，代表你沒有將 Conda  加入系統環境變數哦，請回頭確認安裝步驟吧！

![conda-info](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-info.png?alt=media&token=0841bd1e-d003-4a00-8b83-41ecd0ba2ee8)

Conda 在預設情況下會有個『Base』的 Python 環境，但我們不要使用它，我們要用我們自己建立的虛擬環境，輸入 `conda env list` 可以看到我們目前安裝了哪些環境

接下來輸入，這邊我指定了虛擬環境的名稱為『MachineLearning』，並指定Python版本號為『3.6』版

```bash
conda create --name ml python=3.6
```

Usage : 

```bash
conda create --name <輸入任何名稱作為該虛擬環境的名稱> python=<版本號>
```

![conda-create-venv](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-create-venv.png?alt=media&token=0fd78c6e-c7a0-4bfd-b057-f2ab166bf74e)

這樣就開始安裝了！

![conda-venv-check-install-dependencies](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-venv-check-install-dependencies.png?alt=media&token=01ba2b2e-bb00-4aa1-918a-b0c6b437aa1f)

它問我是否要安裝 .. 當然要呀！輸入 `y`

![conda-venv-y](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-venv-y.png?alt=media&token=9d02015a-d5f9-40b5-a2fd-9f1642d3d87d)

安裝中 ..

![conda-venv-installing](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-venv-installing.png?alt=media&token=41de40b9-50c5-493d-b9d6-365d66d8241c)

安裝完成

![conda-venv-installed](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-venv-installed.png?alt=media&token=0416468d-9500-4787-81fe-d6182fd8ffed)

再查看一次我們所有的 conda env 環境吧，新出現了一個 MachineLearning 環境了！

```bash
conda env list
```

![conda-env-list](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-env-list.png?alt=media&token=38d87d39-7955-4faf-94d1-d70eae2bd3d4)

輸入 `conda activate MachineLearning` 來啟動它吧

```bash
conda activate MachineLearning
```

這樣就啟動了，前面還會帶一個 `(MachineLearning)` 來提示我們目前是在哪一個環境哦

![conda-activate-venv](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-activate-venv.png?alt=media&token=ba8177ed-778c-42ae-afe1-734b8cf0f051)

輸入 `pip install tensorflow==2.1` 安裝機器學習所需要的Python 套件

![conda-pip-install-tensorflow](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-pip-install-tensorflow.png?alt=media&token=fee08c1e-e04a-4b52-a8f8-b959672f7450)

安裝中 .. 近500MB呢！

![conda-pip-install-tensorflow-installing](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-pip-install-tensorflow-installing.png?alt=media&token=91b55180-54cc-49da-a0ef-6f0b04ee403a)

安裝完成

![conda-pip-install-tensorflow-installed](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fconda-pip-install-tensorflow-installed.png?alt=media&token=156785d2-cc37-4fd1-ad09-46d2e25bd1d5)

# 安裝 Visual Studio Code

安裝好開發環境，接下來準備一個好用的編輯器來寫Code吧！

到 [Visual Studio Code 官方網站](https://code.visualstudio.com/)下載軟體，選擇『Download』

![vscode-website](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-website.png?alt=media&token=aae36eda-2495-4c00-b091-93c7737bbd5e)

選擇『User Installer 64-bit』就會下載了

![vscode-download](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-download.png?alt=media&token=88c5169f-b453-46eb-9009-aa0cd2149c24)

開啟檔案安裝它吧，選擇『I accept the agreement』、『Next』

![vscode-install-i-accept](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-install-i-accept.png?alt=media&token=ecb233cb-b34c-4a89-bb6e-f8c84135908f)

全部勾選，然後『Next』

![vscode-additional-tasks](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-additional-tasks.png?alt=media&token=ca6b0a40-9277-451f-a56a-1635ec801e54)

安裝它囉～

![vscode-ready-to-install](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-ready-to-install.png?alt=media&token=a6d339c7-dcce-462e-8a6e-f93e2f3f7d69)

安裝中 ..

![vscode-installing](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-installing.png?alt=media&token=77f30071-f192-45c3-94e8-df9c333fbecf)

安裝完成，點選『Finish』開啟VS code吧

![vscode-install-finish](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-install-finish.png?alt=media&token=ee78e6c4-2b89-46cf-ad9f-ec689ff631f3)

這是Visual Studio Code軟體的畫面，首先我們要先安裝一些幫助開發的Visual Studio Code輔助套件選擇紅框處

![vscode-open-extension](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-open-extension.png?alt=media&token=6223c75b-6542-414b-9b95-633c88ca18ec)

搜尋『Python』選擇第一個然後安裝它吧！

![vscode-search-and-install-python-extension](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-search-and-install-python-extension.png?alt=media&token=d3af6622-9f9d-46ef-b93b-4afd0ce0bf4b)

呼～準備工作終於完成了，建立檔案然後開始寫Code吧！

# 測試開發環境

選擇『File』→ 『New File』

![vscode-open-new-file](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-open-new-file.png?alt=media&token=25e3884c-18c0-4fd1-ae11-cf57507b1ce3)

![vscode-new-file-overview](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-new-file-overview.png?alt=media&token=efb2f9e8-7de4-4257-8af9-44df63de65cc)

輸入以下測試Code ，來源：[TensorFlow 2 quickstart for beginners](https://www.tensorflow.org/tutorials/quickstart/beginner)

```python
import tensorflow as tf

mnist = tf.keras.datasets.mnist

(x_train, y_train), (x_test, y_test) = mnist.load_data()
x_train, x_test = x_train / 255.0, x_test / 255.0

model = tf.keras.models.Sequential([
  tf.keras.layers.Flatten(input_shape=(28, 28)),
  tf.keras.layers.Dense(128, activation='relu'),
  tf.keras.layers.Dropout(0.2),
  tf.keras.layers.Dense(10)
])

predictions = model(x_train[:1]).numpy()
predictions

tf.nn.softmax(predictions).numpy()
loss_fn = tf.keras.losses.SparseCategoricalCrossentropy(from_logits=True)
loss_fn(y_train[:1], predictions).numpy()
model.compile(optimizer='adam',
              loss=loss_fn,
              metrics=['accuracy'])

model.fit(x_train, y_train, epochs=5)
model.evaluate(x_test,  y_test, verbose=2)

probability_model = tf.keras.Sequential([
  model,
  tf.keras.layers.Softmax()
])

probability_model(x_test[:5])
```

存檔，檔名後綴要有 `.py` 哦！

選擇Save type : All Files

![vscode-save-type-all-files](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-save-type-all-files.png?alt=media&token=192efd69-0285-4beb-87af-0830a0d337c3)

![vscode-enter-file-name](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-enter-file-name.png?alt=media&token=3308364d-61d2-46af-a24b-56d1c3a125b4)

選擇『Select Python Interpreter』選擇剛剛建立的虛擬環境『MachineLearning』

![vscode-select-interpreter](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-select-interpreter.png?alt=media&token=96760349-9e7e-461e-81d6-1ea43fd05ea9)

當右下角跳出此畫面時，選擇『Install』

![vscode-install-pylint](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-install-pylint.png?alt=media&token=f4d9325d-c9d2-440d-8b25-8d48cb607772)

選擇使用『Pip』安裝

![vscode-pip-install-pylint](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-pip-install-pylint.png?alt=media&token=826a11b2-e74e-4f11-a34b-98483c3c4f3a)

安裝完成

![vscode-pylint-installed](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-pylint-installed.png?alt=media&token=f4338244-b70f-40f3-a791-1cd0ea69cc91)

選擇『Run Python in Terminal』程式就開始執行囉！

![vscode-run-file-in-terminal](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-run-file-in-terminal.png?alt=media&token=2a172a4d-1f1a-458f-bdd1-489083cb23be)

執行結果：

![vscode-example-result](https://firebasestorage.googleapis.com/v0/b/hexo-neil-blog-db.appspot.com/o/blog-img%2Finstall-machine-learning-environment-in-windows-10%2Fvscode-example-result.png?alt=media&token=915eedc8-eba7-4532-8f33-7c2dc0a49f5d)