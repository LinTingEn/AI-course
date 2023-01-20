---
layout: post
title: Capstone-Project
author: [Charles Huang and Ting-En Lin]
category: [project]
tags: [jekyll, ai]
---

## 期末專題：車位辨識及其應用

### 專題描述
我們希望藉由YOLO實現判斷停車狀況。<br>
[kaggle:parking detection](https://www.kaggle.com/code/ulysses1103/parked-detection)<br>

### 專題實作步驟概述
1. 拍出各種停車狀況的照片。<br>
2. 一一選取各照片中欲辨識之狀況，手動添加標籤，例如：停在格子之中、停在線上或皆非。<br>
3. 將所有照片匯入模型中訓練，使機器自行意會、計算各種狀況的特徵。<br>
4. 測試將隨機狀況之圖片匯入模型，使其辨識。<br>
5. 比較其判斷結果。<br>

**蒐集資料**<br><br>
首先我們得先準備足夠的訓練資料，在自身活動範圍附近尋找適當的汽、機車停車狀況，找尋適當的角度進行拍攝，接著標註每一筆數據。<br><br>

**手動添加標籤**<br><br>
以這張圖為例，可以看到圖中兩台車一台車是停在格子裡，一台車則是隨意停靠路邊。分別對左邊的貼標籤```legal```以及右邊的```illegal```<br>
![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/labels.png?raw=true)<br>

**kaggle的部分**
 <br>
 
 ```
 git clone https://github.com/jz-huanng/yolov5
 
 ```

**custom yaml file**

```
# Train/val/test sets as 1) dir: path/to/imgs, 2) file: path/to/imgs.txt, or 3) list: [path/to/imgs1, path/to/imgs2, ..]

path: ../images  # dataset root dir
train: train  # train images (relative to 'path') 128 images
val: val  # val images (relative to 'path') 128 images
test:  # test images (optional)

# Classes
nc: 2  # number of classes
names: ['legal', 'illegal']  # class names
```



### 辨識結果
| image num | epoch | results | description |see results on kaggle |
| --: | -- | -- | --: | --|
| 15 | 100 |  ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/num15.png?raw=true) | labelled wrong<br>這些應該被貼上```illegal```而不適```legal``` |version 8 | 
| 15(fine-tuned) | 80 | ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/fine-tune.png?raw=true)<br>![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/labels2.png?raw=true) | labelled imprfect 但是不是機器學到方格? | version 9| 
| 15(fine-tuned) | 80 | ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/no_result.png?raw=true)| 沒有辨識出來 | version 9| 
| 15(fine-tuned) | 160 | ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/epoch160.png?raw=true)| 目前下來唯一一張有辨識到illegal | version 10| 
| 15(fine-tuned) | 160 | ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/epoch160_2.png?raw=true)| 和epoch 80結果一樣 | version 10| 
|44|80|![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/version11.png?raw=true)||version 11|
|44|160|![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/parking-detection/version13.png?raw=true)|幾乎成功!|version13|



<br>

>quote




<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>


***train***
![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/train.png?raw=true)
### kaggle實作
---

[kaggle:parking detection](https://www.kaggle.com/code/ulysses1103/parked-detection)<br>


[yolov5](https://github.com/ultralytics/yolov5)

### ARCHIVE棄存
---
在資料夾data放進images 和 labels
 ![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/directory.png?raw=true)

**imperfect outcome**

![](https://github.com/jz-huanng/AI-course/blob/gh-pages/images2/bad_outcome.png?raw=true)

結果不理想原因應該在於蒐集資料的角度

### 參考資料
[Image Annotation](https://rkuo2000.github.io/AI-course/lecture/2022/10/13/Object-Detection-Exercises.html
)<br><br>

[yolov5](https://github.com/ultralytics/yolov5)

*This site was last updated {{ site.time | date: "%B %d, %Y" }}.*

