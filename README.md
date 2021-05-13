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

additional changes: 1) Use of Albumentations library 2) Mixed Precision modifications (for one gpu code) 3) Implementations for Triple Crop (Triple_Crop.py)

### Examples:
![cat](https://user-images.githubusercontent.com/77424795/118076617-7ebf0100-b3ed-11eb-86d2-e476a1c40d5a.png)

   
# Result
![CIFAR-10](https://user-images.githubusercontent.com/77424795/118076822-e1180180-b3ed-11eb-8cc7-61fcd924b0e1.png)
![CIFAR-100](https://user-images.githubusercontent.com/77424795/118076830-e5441f00-b3ed-11eb-99ee-c2f665c719fe.png)
![STL-10](https://user-images.githubusercontent.com/77424795/118076837-e9703c80-b3ed-11eb-8d31-29d7c842142b.png)
![ImageNet-100](https://user-images.githubusercontent.com/77424795/118077392-f6416000-b3ee-11eb-879c-f3ae8eaaa105.png)

# Analysis

