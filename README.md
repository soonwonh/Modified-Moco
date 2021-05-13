# In Summary

This repo focuses on better augmentation for contrastive learning

Just small changes in augmentations can lead to significant performance improvement.

We worked with Moco-v1 on 4 dataset( CIFAR-10, CIFAR-100, STL-10, ImageNet-100 )


# Introduction

### Baseline code : 

(one gpu) https://colab.research.google.com/github/facebookresearch/moco/blob/colab-notebook/colab/moco_cifar10_demo.ipynb 

(n gpu) https://github.com/facebookresearch/moco.git  

![aug](https://user-images.githubusercontent.com/77424795/118077509-2a1c8580-b3ef-11eb-9149-50de399c979d.png)  

Additional changes: 1) Use of Albumentations library 2) Mixed Precision modifications (for one gpu code) 3) Implementations for Triple Crop (Triple_Crop.py)  

![cat](https://user-images.githubusercontent.com/77424795/118076617-7ebf0100-b3ed-11eb-86d2-e476a1c40d5a.png)

   
# Result
![CIFAR-10](https://user-images.githubusercontent.com/77424795/118076822-e1180180-b3ed-11eb-8cc7-61fcd924b0e1.png)
![CIFAR-100](https://user-images.githubusercontent.com/77424795/118076830-e5441f00-b3ed-11eb-99ee-c2f665c719fe.png)
![STL-10](https://user-images.githubusercontent.com/77424795/118076837-e9703c80-b3ed-11eb-8d31-29d7c842142b.png)
![Imagenet-100](https://user-images.githubusercontent.com/77424795/118077866-fa21b200-b3ef-11eb-8e29-ad77273653e1.png)


# Analysis

