# face-recognition-notes 


## 人臉辨識(face recognition) - 使用 深度學習(TensorFlow) 和 OpenCV - 1/20


### 深度學習

一個函數集，自己訓練出來的(經過大量的訓練過程，最終計算出一個最佳函數，得出最佳解，我們主要提供他規則)

### 為什麼要研究深度學習 ? 單純使用 opencv 沒辦到辦到 人臉辨識嗎 ?

可以 。可以透過 opencv 的 Face Recognition 辦到臉部辨識。

### 那為什麼在網路上找 Face Recognition ，相關近期資料卻都是 深度學習(TensorFlow) 搭配 OpenCV ?

目前猜測是辨識精準度的問題。

單純使用 OpenCV 完成臉部辨識 : 使用人工的方式截取臉部特徵值

使用 OpenCV +  深度學習(TensorFlow) 完成臉部辨識 : 深度學習會自動截取臉部特徵值

考慮到辨識對象可能長的很相似，所以對辨識精準度的要求要比較高。


因為這些原因，所以我研究臉部辨識這議題，我是針對深度學習下去研究，opencv 單純只是幫我偵測出人臉。

### 研究專案

參考專案 : [BossSensor](http://ahogrammer.com/2016/11/15/deep-learning-enables-you-to-hide-screen-when-your-boss-is-approaching/)

BossSensor 流程 :

<b>步驟一 </b> : 收集圖片，圖片只保留臉部的部份，因為如果有背景以及其他不必要的部份，會影響訓練以及辨識.

方法: 使用opencv截取人臉的部份。(在opencv裡，可以透過 haarcascade_frontalface_default.xml 來偵測出目前是否為人臉)

<b>步驟二 </b> : 開始建立 機器學習(Machine Learning) 的 model
 
方法 : 透過 Keras  卷積深度神經網路（Convolutional Neuron Networks, CNN） 建立 model

大家為什麼選 卷積深度神經網路（Convolutional Neuron Networks, CNN） ?

因為卷積神經網路 (深度學習結構)在<b> 圖像 </b>和<b> 語音辨識 </b>方面能夠給出更優的結果。

* Keras 介紹

Keras的後端有 TensorFlow(tf) 以及 Theano(th)

TensorFlow(tf) 表達模式 - (100,3,16,32)  

Theano(th) 表達模式 - (100,16,32,3)     

100,3 這部份是指 100張 RPG 三通道的圖片

16代表高   32代表寬

訓練和測試使用同一種後端。

在訓練的時候，我們會先把照片轉成大小一致(64*64)

dataset --> build Model --> train Model  --> save Model

<b>步驟三 </b> : 開始辨識

load Model --> 透過相機截取臉部 --> 將大小轉成(64*64) --> 比對 (開始辨識)

### 相關議題  Microsoft Face API 背後技術

由於 Microsoft Face API 的辨識速度很快，而且上傳給他的圖片也只有幾張而已，猜測他們的技術是比對兩張圖片的特徵值，

而不是使用深度學習


### 目前深度學習的應用

以 google舉例

* Gmail 自動判斷約99%的垃圾郵件

* Google Now 的語音辨識，透過學習，辨識率越來越精準

* Google 相簿的自動分類 (對照片自動下標籤)



