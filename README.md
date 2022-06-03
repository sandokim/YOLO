# YOLO

Each cell의 bounding box의 [x,y,w,h]는 상대적이다. x,y는 0~1 사이값, w는 onject의 width가 cell보다 크면 w>1, h는 object의 height가 cell보다 크면 h>1.

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/RelativeBoundingbox.JPG" width="50%">

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/labelcell.JPG" width="50%">

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/predcell.JPG" width="50%">

Predictions will look very similar, but we will output two bounding boxes.

Prediction은 Wide와 tall에 따른 2개의 다른 bounding boxes를 출력하기 때문에  1 probability score + bounding box(4 parameters)가 2개 이다.

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/predcell.JPG" width="50%">

#### 20 different classes + 1 probability score + bounding box(x,y,w,h : 4 parameters)

#### 20 different classes + 2 * (1 probability score + bounding box(x,y,w,h : 4 parameters))

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/predcell.JPG" width="50%">
