# In Summary

This repo focuses on better augmentation for contrastive learning

Just small changes in augmentations can lead to significant performance improvement.

We worked with Moco-v1 on 4 dataset( CIFAR-10, CIFAR-100, STL-10, ImageNet-100 )


# Introduction

### Baseline code : 

(one gpu) https://colab.research.google.com/github/facebookresearch/moco/blob/colab-notebook/colab/moco_cifar10_demo.ipynb 

(n gpu) https://github.com/facebookresearch/moco.git  

### Original augmentations:

![old_aug](https://user-images.githubusercontent.com/77424795/118074702-71077c80-b3e9-11eb-8a37-6d54a4792a10.PNG)

### Our augmentations

![new aug](https://user-images.githubusercontent.com/77424795/118074708-7664c700-b3e9-11eb-9685-8f1c0d16fcf1.PNG)

additional changes: 1) Use of Albumentations library 2) Mixed Precision modifications for one gpu code 3) Implementations for Triple Crop

I set other argument as default except for augmentation for clear comparison ( no mlp-head, no-gaussian blur, asymmetric loss )

Specificaly, changes in the code are as follows.

1) Use of Albumentations library
  
  
  
    original baseline used pytorch library's transformation function, I changed it to Albumentations library for two reasons. 1. more diverse set , 2. more fast
    if you use same set of augmentations, Albumentations library is (much) faster than pytorch library (see albumentations's documentations ) 
  
  
  
2) 4 transformations -> 7 transformations ( Additional transformations : Solarize , CLAHE, RandomBrightContrast )

all the data gathered are in Excel file, and optimal code so far is uploaded as MOCO-Augmented.py

# Future research

1) Faster-Auto Augment
   
   fast hyper-parameter search for optimal augmentation pipeline
   
 2) Loss modifications
   
    modify loss to debias negative sample in the queue
   
 3) Imagenet Training
 
    Apply these augmentation pipeline to Imagenet
   
 4) SimCLR , BYOL , Swav
 
    Apply these augmentations pipeline to other SOTA models
   
 5) Hard-negative mixing
 
 6) Interpolations for Multi-crop augmentations
 
 
 
   
