# EfficientNetV2 Smaller Models and Faster Training笔记



Summary keywords

+ faster training speed

+ better parameter efficiency

Why

+ Training efficiency has gained significant interests recently.  NFNets, ResNet-RS, Lambda Networks, BotNet, Vision Transformers. However, these methods often come with expensive overhead on parameter size, as shown in Figure 1(b).  



![image-20210604161311220](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20210604161311220.png)  



+ the training bottlenecks in EfficientNets:
  + training with very large image sizes is slow
  + depthwise convolutions are slow in early layers
  + equally scaling up every stage is sub-optimal

How

+ We use a combination of training-aware neural architecture search and scaling, to **jointly optimize training speed** and **parameter efficiency**.
+ The models were searched from the search space enriched with new ops such as **Fused-MBConv**.
+ To compensate for this accuracy drop, we propose an improved method of **progressive learning**, which adaptively adjusts regularization (e.g., dropout and data augmentation) along with image size.

Contributions

+ We introduce **EfficientNetV2**, a new family of smaller and faster models. Found by our training-aware NAS and scaling, EfficientNetV2 outperform previous models in both training speed and parameter efficiency.
+ We propose an improved method of **progressive learning**, which adaptively adjusts regularization along with image size. We show that it speeds up training, and simultaneously improves accuracy.
+ We demonstrate up to 11x **faster training speed** and up to 6.8x **better parameter efficiency** on ImageNet, CIFAR, Cars, and Flowers dataset, than prior art.



label smooth

mixup

Learning rate is first warmed up





progressive learning

+ Image Size
+ RandAugment
+ Mixup alpha
+ Dropout rate
+ cosine learning rate decay



![image-20210604171145263](C:\Users\86138\AppData\Roaming\Typora\typora-user-images\image-20210604171145263.png)  





Scaling up data size is more effective than simply scaling up model size in high-accuracy regime