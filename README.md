# YOLO

Each cell의 bounding box의 [x,y,w,h]는 상대적이다. x,y는 0~1 사이값, w는 onject의 width가 cell보다 크면 w>1, h는 object의 height가 cell보다 크면 h>1.

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/RelativeBoundingbox.JPG" width="50%">

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/labelcell.JPG" width="50%">

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/predcell.JPG" width="50%">

Predictions will look very similar, but we will output two bounding boxes.

Prediction은 Wide와 tall에 따른 2개의 다른 bounding boxes를 출력하기 때문에  1 probability score + bounding box(4 parameters)가 2개이다.

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/predcell.JPG" width="50%">

#### 20 different classes + 1 probability score + bounding box(x,y,w,h : 4 parameters) ==> 25

#### 20 different classes + 2 * (1 probability score + bounding box(x,y,w,h : 4 parameters)) ==> 30

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/target_prediction.JPG" width="50%">

#### torch.flatten -> start_dim=1 ; (B, C, W, H)에서 Batch는 a number of examples이므로 제외하고 C,W,H차원으로 Flatten

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/start_dim=1.JPG" width="80%">

#### Architecture config로 모델설계하기, if문으로 dtype에 따라 레이어 구성하기

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/config.JPG" width="80%">

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/config2model.JPG" width="80%">

최종적으로 nn.Sequential에 *를 사용하여 list안에 들어있는 모든 Layers들을 Unpack

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/unpacklayers.JPG" width="80%">

#### 0~19 class, 20번째 index=class probability, class probability를 indexing하면 차원이 하나 줄어들기 때문에 이를 다시 복원하기 위해 unsqueeze(3)을 해준다.

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/Yolo_Loss.JPG" width="80%">

..., 2:4 meaning

<img src="https://github.com/hyeseongkim0/YOLO/blob/main/images/dotdotdot.JPG" width="80%">
