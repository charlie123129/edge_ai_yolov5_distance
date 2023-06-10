# edge_ai_yolov5_distance
#### 參考文件與成果展示:[【人工智慧與邊緣運算實務期末報告】基於YOLOv5之距離量測](https://hackmd.io/YMHAvP2JS-mq_fR6kTGGgA)
### 先下載 yolov5
```
git clone https://github.com/ultralytics/yolov5
```
### 建立虛擬環境
```
conda create --name yolov5 python=3.8
```

### 切換到虛擬環境
```
conda activate yolov5
```

### 到yolov5資料內安裝所有需要的套件
```
pip install -r requirements.txt
```
### 下載 edge_ai_yolov5_distance
>### 把edge_ai_yolov5_distance資料夾內的資料複製到yolov5資料夾
```
git clone https://github.com/charlie123129/edge_ai_yolov5_distance
```

### 建立mydata資料夾放入自己的資料
#### 下載labelimg，進行圖片的標註 

>可以參考Osense RD的[labelimg安裝及使用](https://hackmd.io/@osense-rd-public/H1ekDPqBt
)
```
images
├──> train
    ├──> people
        ├──> aaa1.jpg
        ├──> aaa2.jpg
        ├──> ...
    ├──> bicycle
        ├──> bbb1.jpg
        ├──> bbb2.jpg
        ├──> ...
    ├──> motorcycle
        ├──> ccc1.jpg
        ├──> ccc2.jpg
        ├──> ...
    ├──> car
        ├──> ddd1.jpg
        ├──> ddd2.jpg
        ├──> ...
    ├──> bus
        ├──> eee1.jpg
        ├──> eee2.jpg
        ├──> ...
├──> test
    ├──> 測試資料(影片)
    
labels
├──> train
    ├──> people
        ├──> aaa1.txt
        ├──> aaa2.txt
        ├──> ...
    ├──> bicycle
        ├──> bbb1.txt
        ├──> bbb2.txt
        ├──> ...
    ├──> motorcycle
        ├──> ccc1.txt
        ├──> ccc2.txt
        ├──> ...
    ├──> car
        ├──> ddd1.txt
        ├──> ddd2.txt
        ├──> ...
    ├──> bus
        ├──> eee1.txt
        ├──> eee2.txt
        ├──> ...
├──> test

```


### 在data資料夾中建立mydata.yaml
```
train: mydata/images/train  
val: mydata/images/train  
test:  # test images (optional)
names:
  0: car
  1: people
  2: motorcycle
  3: bicycle
  4: bus
``` 
### 程式
#### 開始訓練模型
利用pycharm打開檔案
```
python train.py
```
>選擇 yolov5 pretrained model(n,s,m,l,x)

>設定epochs

>調整batch size

>yaml檔的路徑要更改到建立的mydata.yaml

>device 可是設定在cpu或是cuda上 (建議cuda)


    
也可以下載我已經訓練好的模型

模型: [yolov5n](https://drive.google.com/drive/folders/1K6Cmw5afntxrE60opEUkKJL9bbef1Wjy?usp=drive_link)，[yolov5s](https://drive.google.com/drive/folders/13robTq2GvFvhzL27MX-V72BDdnh63vPD?usp=drive_link)，[yolov5l](https://drive.google.com/drive/folders/1PJ6Dm10NBw5YAPmJ3Z93ivkFzhHN8WiM?usp=drive_link)，[yolov5x](https://drive.google.com/drive/folders/1IFoxxRb1d622zvpLBirgcpCRqSMEqLEb?usp=drive_link)


 
#### 模型推論
```
python detectokfps.py
```
>調整weights路徑修改到目標模型

>device 可以設定在cpu或是cuda上進行推論 


#### 標註的準確度比較
```
python val.py
```
>調整weights路徑修改到目標的模型

>device 可以設定在cpu或是cuda上進行 (建議cuda)


#### 模型轉換優化比較
```
python benchmarks.py
```
>調整weights路徑修改到目標的模型

>device 可以設定在cpu或是cuda上進行 (建議cuda)



#### 模型轉換
```
python export.py
```
>調整weights路徑修改到目標的模型

>device 可以設定在cpu或是cuda上轉換 (建議cuda)

