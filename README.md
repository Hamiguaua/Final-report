# 基於深度學習建構卷積神經網路模型演算法，實現影像辨識分類

# 前言

隨著人工智慧的不斷發展，深度學習這項技術也越來越重要，許多人都開始學習機器學習。本文將透過專案開發實例，帶領大家從零開始設計並實作一套基於深度學習的影像辨識演算法。
學習本章內容，你需要掌握以下基礎知識：

1.Python 基礎語法

2.電腦視覺函式庫（OpenCV）

3.深度學習框架（TensorFlow）

4.卷積神經網路（CNN

---

# 一、基礎知識介紹

1.Python
  Python 是一種高階程式語言，結合了解釋型、編譯型、互動性與物件導向等特性，屬於腳本語言。
  學習連結：Python 學習
  
2.OpenCV
  OpenCV 是一套開源且跨平台的電腦視覺函式庫，實作了許多影像處理與電腦視覺相關的通用演算法。在本設計中，主要用於影像的擷取以及影像前處理等功能。
  學習連結：OpenCV 學習
  
3.TensorFlow
  TensorFlow 是由 Google 開源的運算框架，能夠良好地支援各種深度學習演算法。本課程設計中的影像辨識部分所採用的深度學習（Deep Learning）演算法，即是使用 TensorFlow 框架來實作。
  學習連結：TensorFlow 學習
  
4.CNN
  卷積神經網路（Convolutional Neural Networks，CNN）是一類包含卷積運算且具有深層結構的前饋式神經網路（Feedforward Neural Networks），是深度學習（Deep Learning）的代表性演算法之一。
  學習連結：CNN 學習

  ---

# 二、資料集蒐集

在進行影像辨識之前，首先需要蒐集資料集（資料集下載），接著對資料集進行前處理，之後才能透過深度卷積神經網路進行特徵學習，並建立分類模型。
對於資料集的要求而言，在卷積神經網路（CNN）中，由於輸入影像向量的權重參數數量是固定的，因此在使用卷積神經網路（CNN）對資料集進行模型訓練之前，必須先進行影像前處理，以確保輸入影像的尺寸固定且一致。

<img width="231" height="546" alt="人工智慧 drawio (1)" src="https://github.com/user-attachments/assets/bd1345a1-9f04-4721-bfbc-693e44255eeb" />

圖一　分類網路模型流程圖

# 程式

**安裝套件**

<img width="628" height="185" alt="螢幕擷取畫面 2025-12-28 205745" src="https://github.com/user-attachments/assets/efa11ff3-85db-4e25-ab7c-d0c57cdc0b6f" />

---

**初始化與屬性設定**

<img width="657" height="237" alt="image" src="https://github.com/user-attachments/assets/2d9d247c-a798-4947-9dec-0a8604d14cce" />

---

**圖片處理相關**

<img width="695" height="508" alt="image" src="https://github.com/user-attachments/assets/162a7f09-703f-4272-9141-c7ef724c3e3e" />

---

**模型建立與訓練**

<img width="580" height="619" alt="image" src="https://github.com/user-attachments/assets/c0f654a3-b76d-47d0-b8ee-2ac129da74ab" />

<img width="727" height="594" alt="image" src="https://github.com/user-attachments/assets/e49fb419-1e3d-4b5b-b76a-75e23330a63f" />

---

**預測與結果顯示**

<img width="600" height="727" alt="image" src="https://github.com/user-attachments/assets/c6f9be5c-7e13-442d-af7b-71c97c975b9a" />

---

<img width="453" height="155" alt="image" src="https://github.com/user-attachments/assets/f75ebcc2-5083-4524-ad92-3b4794dc4fc9" />


**建立分類器:**

        classifier = SafeImageClassifier(image_path)

image_path 是資料集根目錄。會自動掃描資料夾，將每個子資料夾視為一個類別。初始化時會列出類別名稱。

**圖片處理:**

        classifier.resize_images()
        
將每個類別資料夾中的圖片 resize 成固定大小（200×200）。

避免訓練時因為尺寸不同造成錯誤。
        
        classifier.generate_csv()

生成 CSV，記錄每張圖片路徑與對應標籤。

CSV 方便後續讀取訓練資料。

---

**建立模型:**

        classifier.build_model()

建立 CNN 模型：

        3 層卷積 + 最大池化 + BatchNorm、 GlobalAveragePooling、 Dense + Dropout、 最後輸出類別數的 softmax

編譯模型，設定損失函數與優化器。

---

**訓練模型**

        classifier.train(epochs=10, batch_size=2)

讀取 CSV 中的圖片與標籤。

將標籤 one-hot encoding。

切分訓練集與驗證集（80%/20%）。

開始訓練模型。

---

# 結果圖

<img width="580" height="612" alt="image" src="https://github.com/user-attachments/assets/4accef56-40ed-4388-83a3-9a09cb2c5e25" />

