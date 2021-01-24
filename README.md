# Modified-Moco

This repo aims to improve upon Moco 

(baseline code can be accessed from https://colab.research.google.com/github/facebookresearch/moco/blob/colab-notebook/colab/moco_cifar10_demo.ipynb )


I modified Augmentation Pipeline, which leads to 1.7% improvement upon baseline. (82.6% -> 84.3%)



I set other argument as default except for augmentation for clear comparison ( no mlp-head, no gaussian-blur , asymmetric loss )



Specificaly, changes in the code are as follows.




1) Use of Albumentations library
  
  
  
  original baseline used pytorch library's transformation function, I changed it to Albumentations library for two reasons. 1. more diverse set , 2. more fast
  if you use same set of augmentations, Albumentations library is (much) faster than pytorch library (see albumentations's documentations )
  
  
  
2) 4 transformations -> 6 transformations ( Additional transformations : Solarize , CLAHE )

 
3) Gradual Augmentations
   
   
   I increased hyperparameter in every 50 epochs ( i.e. stronger augmentations in every 50 epochs )
   As the training proceed, model can classify most of input easily. Easy(low logits) sample doesn't contribute to the loss enough, so we make the model learn from 
   harder(high logits) sample in every 50 epochs. This is related to hard negative mining / mixing problems. Also effect of 1) can be explained this way. 
   


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
 
 
 
   
