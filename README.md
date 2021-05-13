# In Summary

This repo focuses on better augmentation for contrastive learning

Just small changes in augmentations can lead to significant performance improvement.

We worked with Moco-v1 on 4 dataset( CIFAR-10, CIFAR-100, STL-10, ImageNet-100 )


# Introduction

### Baseline code : 

(one gpu) https://colab.research.google.com/github/facebookresearch/moco/blob/colab-notebook/colab/moco_cifar10_demo.ipynb 

(n gpu) https://github.com/facebookresearch/moco.git  

![aug](https://user-images.githubusercontent.com/77424795/118077509-2a1c8580-b3ef-11eb-9149-50de399c979d.png)  

Downcrop : smaller hyper-parameter of RandomResizedCrop  
aug+ : Solarize + CLAHE + RandomBrightness

Additional changes: 1) Use of Albumentations library 2) Mixed Precision modifications (for one gpu code) 3) Implementations for Triple Crop (Triple_Crop.py)  

![cat](https://user-images.githubusercontent.com/77424795/118076617-7ebf0100-b3ed-11eb-86d2-e476a1c40d5a.png)

   
# Result
![CIFAR-10](https://user-images.githubusercontent.com/77424795/118076822-e1180180-b3ed-11eb-8cc7-61fcd924b0e1.png)
![CIFAR-100](https://user-images.githubusercontent.com/77424795/118076830-e5441f00-b3ed-11eb-99ee-c2f665c719fe.png)
![STL-10](https://user-images.githubusercontent.com/77424795/118076837-e9703c80-b3ed-11eb-8d31-29d7c842142b.png)
![Imagenet-100](https://user-images.githubusercontent.com/77424795/118077866-fa21b200-b3ef-11eb-8e29-ad77273653e1.png)  
for training time & GPU memory consumption, we denoted relative value (and absolute value in parentheses)
![STL_chart](https://user-images.githubusercontent.com/77424795/118077945-20dfe880-b3f0-11eb-9334-5702402c0f61.png)
![Imagenet_chart](https://user-images.githubusercontent.com/77424795/118077986-30f7c800-b3f0-11eb-8229-376c7ddd8e35.png)

# Analysis

![image](https://user-images.githubusercontent.com/77424795/118088494-221a1100-b402-11eb-8e5d-459074acda32.png)
![image](https://user-images.githubusercontent.com/77424795/118088573-39f19500-b402-11eb-8fd4-d7ce2d8a0002.png)  
from the contrastive loss of our result, we can plot Accuracy-Mutual Information graph as follows  
![image](https://user-images.githubusercontent.com/77424795/118088717-6f967e00-b402-11eb-9779-a56b38d07d6f.png)  
We can see that reducing mutual information is helpful and effective for contrastive learning.  
Furthermore, we can also find that reducing quantity of information (number of bits) is helpful. Downcrop reduce final image size for training.  
The solarize function cuts the information in the image in half by replacing pixel values above a defined threshold(128, here) with a negated value. ( 0 ~ 128 -> 0 ~ 128, 129 ~ 256 -> 128 ~ 0) We analyzed the reason is that it is located in the right part of above graph (too much noise part) where the conventional augmentation contains a lot of noise for the task.
![image](https://user-images.githubusercontent.com/77424795/118088738-79b87c80-b402-11eb-9cc7-05ea38846d95.png)

### In supervised setting, Downcrop deteriorates performances

## Grad-CAM
![image](https://user-images.githubusercontent.com/77424795/118090290-5b538080-b404-11eb-9646-7534987b3e53.png)
