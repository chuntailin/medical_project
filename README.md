# medical_project
```
HU 40~70 (liver)
HU 0~200, 60~80 (tumor)

* HU值的比較
* 未來 Anchor size 用非 2 的倍數
* 增加 augmentation 資料總量
* 增加 training 的正負比例


------------ tumor --------------
------------HU 60~80--------------
# version 1
Configure在train_medical中有記錄
Train 0~120 | Val 121~130
使用fliplr, flipud, rotation作為augmentation

# version 2
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), GaussianBlur
Anchor使用(8, 16, 32, 64, 128)

dice = 0.4008466658834948

# version 3
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), GaussianBlur
Anchor使用(32, 64, 128, 256, 512)

dice = 0.3744609061419301

# version 4
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.4035303849237215

# version 5
Configure在train_medical中有記錄
加入一些沒有包含tumor的病人slices
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.4332146535762361

# version 6
新的training dataset (transform_nii.py中更改成.getfdata()) (unbalance data)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.3487582858677195

# version 7
新的training dataset (transform_nii.py中更改成.getfdata()) (balance data)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.2937081228783093

# version 8
新的training dataset (liver mask)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.5413352897560811

# version 9
新的training dataset (liver mask crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.450529523571362

# version 10
使用前後三張slice作為一組training input
新的training dataset (liver mask)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.5399604686045054

# version 11
使用前後三張slice作為一組training input
新的training dataset (liver mask crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.5459720829205902

# version 12
使用前後三張slice作為一組training input
新的training dataset (liver mask crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)
Step_Per_Epoch = 500 (原為50)
Validation_Steps = 100 (原為50)
Image Dimension = 256x256
Train_ROI_Per_Image = 80 (原為32)
Detection_Min_Confidence = 0.5 (原為0.01)
RPN_Train_Anchors_Per_Image = 256 (原為512)

dice = 0.5586750152456664

# version 13
使用前後三張slice作為一組training input
新的training dataset (liver mask crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)
Step_Per_Epoch = 500 (原為50)
Validation_Steps = 100 (原為50)
Image Dimension = 256x256
Train_ROI_Per_Image = 80 (原為32)
Detection_Min_Confidence = 0.5 (原為0.01)
RPN_Train_Anchors_Per_Image = 256 (原為512)
RPN_NMS_Threshold = 0.8 (原為0.7)
Max_GT_Instance = 20 (原為50)

dice = 0.5656402679338933

# version 14
使用前後三張slice作為一組training input
新的training dataset (liver mask crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)
Step_Per_Epoch = 500 (原為50)
Validation_Steps = 100 (原為50)
Image Dimension = 256x256
Train_ROI_Per_Image = 80 (原為32)
Detection_Min_Confidence = 0.5 (原為0.01)
RPN_Train_Anchors_Per_Image = 256 (原為512)
RPN_NMS_Threshold = 0.8 (原為0.7)
Max_GT_Instance = 10 (原為50)

dice = 0.5656131019198679

# version 15 (use weights of version 14 as initial weights)
dice = 0.0.5444565094221852

# version 16 (user resnet101 and training on AsGPU)
dice = 0.569390024508367

------------ tumor --------------
------------HU -150~250--------------
# version 1
新的training dataset (liver mask)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用fliplr, flipud, rotation作為augmentation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.16826601751939377

# version 2
新的training dataset (liver mask and crop)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用fliplr, flipud, rotation作為augmentation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.14089266146078752


------------ liver --------------
------------HU 40~70--------------
# version 2
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(8, 16, 32, 64, 128)

dice = 0.9093483334546196

# version 3
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
Anchor使用(32, 64, 128, 256, 512)

dice = 0.9156577538940395

# version 4
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
只訓練一個class (liver)
Anchor使用(32, 64, 128, 256, 512)

dice = 0.9161298141245707

# version 5
新的training dataset (transform_nii.py中更改成.getfdata()) (unbalance data)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
只訓練一個class (liver)
Anchor使用(32, 64, 128, 256, 512)

dice = 0.8226065502030823

# version 6
新的training dataset (transform_nii.py中更改成.getfdata()) (balance data)
Configure在train_medical中有記錄
Train 0~115 ｜Val 116~125 ｜ Test 126~130
使用scale, shear, PiecewiseAffine(scale), fliplr, flipud, rotation
只訓練一個class (liver)
Anchor使用(32, 64, 128, 256, 512)

dice = 0.5039709064599046

# version 5 (未來放前後三張slice) [2, 2, 2]  ->  [1, 2, 3]

```
