# edge_ai_yolov5_distance_github
### 先下載 yolov5 
> git clone https://github.com/ultralytics/yolov5
### 建立虛擬環境 
>### conda create yolov5 python=3.8
### 到yolov5資料截安裝所有需要的套件
>### yolov5 資料夾內 pip install -r requirements.txt
### 下載 edge_ai_yolov5_distance
>### 把edge_ai_yolov5_distance資料夾內的資料複製到yolov5資料夾
>git clone https://github.com/charlie123129/edge_ai_yolov5_distance/tree/main


### 建立mydata資料夾放入自己的資料
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
    ──> 測試資料(影片)
    
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

下載labelimg，進行圖片的標註
參考連結[labelimg](https://hackmd.io/@osense-rd-public/H1ekDPqBt
)進行安裝



### 在data資料夾中建立mydata.yaml
>train: mydata/images/train  
>val: mydata/images/train  
>test:  # test images (optional)
names:
  0: car
  1: people
  2: motorcycle
  3: bicycle
  4: bus
  

### 開始訓練模型
- python train.py
    >選擇 yolov5 pretrained model(n,s,m,l,x)
    >設定epochs
    >調整batch size

 
### 模型推論
 - python detectokfps.py
     >weights 路徑修改到在train.py訓練好的模型best.pt
 
 