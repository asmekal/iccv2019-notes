# iccv2019-notes
personal notes from iccv2019

## Intro

Over 7,500 participants, 4 days of main conference + 60 workshops and 12 tutorials.
~1200 accepted papers (20% orals) on the main conference alone.

It was absolutely infeasible to track everything so I almost completely skipped the following topics
- Autonomous driving
- 3D, Point clouds
- Video analysis
- Computer Vision in medical images

I spend a few time to:
- Domain adaptation, Zero-shot, few-shot, unsupervised, self-supervised, semi-supervised. **TL;DR** motivation - to learn as fast as humans with less/no data by few examples. In practice it still works poor enough and can not compare to supervised methods. **At the current stage we can not do this successfully enough, but when we will it will be a giant step forward.**
- Knowledge distillation, federated learning. **TL;DR** many papers have controversal results - sometimes it works, sometimes don't, sometimes very useful, sometimes useless. **You can try but do not expect much**
- Deepfakes in images and videos. **TL;DR** you can not completely trust any digital image/video anymore. There are huge movement in the area and already several datasets present. The problem is - when you know the "deepfake attack" method and trained on on the data which was produced with this method you can take ~70-95% accuracy (which is itself not much), but *when you don't know the method your deepfake detector may be close to random (50%)*

I took a closer look on:
- Semantic and instance segmentation, object detection
- New architectures, modules, losses, augmentations, optimizetion methods
- Neural architecture search
- Interpretibility
- Text detection and recognition
- Network compression
- GANs, style transfer

## Augmentation

- [7/10]["We show that increasing the robustness to carefully selected common perturbations, can make neural networks more robust to unseen common perturbations. We also prove that adversarial robustness and robustness to common perturbations are independent. Our results make us believe that neural network robustness should be addressed in a broader sense."] Are adversarial robustness and common perturbation robustness independant attibutes

- 

## Semantic segmentation

- [9/10][Adversarial training for quality improvement + uncertainty estimation] [I Bet You Are Wrong: Gambling Adversarial Networks for Structured Semantic Segmentation](http://openaccess.thecvf.com/content_ICCVW_2019/html/CVRSUAD/Samson_I_Bet_You_Are_Wrong_Gambling_Adversarial_Networks_for_Structured_ICCVW_2019_paper.html)

- [8/10] Asymmetric Non-local Neural Networks for Semantic Segmentation (proposed efficient non-local block, seem to improve quality compared to other architectures on the same backbone)

- [8/10] Convex Shape Prior for Multi-object Segmentation Using a Single Level Set Function. (reformulate loss for convex objects -> performance improve)

- [6/10] Dynamic Multi-scale Filters for Semantic Segmentation (very strange and suspicious layer which surprisingly improves accuracy)

- [6/10][Detect unknown objects using optical flow] Towards segmenting everything that moves

## Instance segmentation

## Object detection

## Text detection and recognition

- SNICER: Single noisy image denoicing and rectification for improving licence plate recognition

- State-of-the-art in action: unconstrained text detection



## Content generation, generative models, GANs

- [10/10 BEST PAPER ICCV2019] SinGAN: Learning a Generative Model from a Single Natural Image [video](https://www.youtube.com/watch?v=Xc9Rkbg6IZA). Use generators and discriminators on multiple resolutions and train on single image patches. Multiple applications without additional training including super resolution, image editing, single image animation, paint2image. Code available.

- [6/10] Once a MAN: Towards Multi-target attack via learning multi-target adversarial network once. **TL;DR** Single model to produce adversarial examples towords any class (surprisingly, all the previous works use one model for one class, in this work - one work for all classes)

- Dance Dance Generation: Motion Transfer for Internet Videos

- I bet you are wrong: gambling adversarial networks for semantic segmentation

- Markov decision process for video generation

-

## Compression

- [9/10] [Automated Multi-Stage Compression of Neural Networks](http://openaccess.thecvf.com/content_ICCVW_2019/papers/LPCV/Gusak_Automated_Multi-Stage_Compression_of_Neural_Networks_ICCVW_2019_paper.pdf) - tensor decompositions, two repetitive steps:
compression and fine-tuning, 10-15x compression rate with 1-2% metric drop (depend on dataset). [pytorch code](http://openaccess.thecvf.com/content_ICCVW_2019/papers/LPCV/Gusak_Automated_Multi-Stage_Compression_of_Neural_Networks_ICCVW_2019_paper.pdf)

- [6/10][Yolo compression success story, known techniques applied properly] SlimYOLOv3: narrower faster and better for real-time

- [??? TODO] [Workshop: Compact and Efficient Feature Representation and Learning in Computer Vision 2019](http://www.ee.oulu.fi/~lili/CEFRLatICCV2019.html)

## Other

- Real time aerial suspicious analysis (asana): system for identification and re-identification of suspicious individuals in crowds using the bayesian scatter-net hybrid network

- 

# Workshops
## Workshop: Image and Video Synthesis: How, Why and What If?
-[decompose into parts] hierarchical text2image (bbox->mask->image)
-generate by modifying part of the image
-[unsupervised] landmark autoencoder
-[small trick] best-of-many objective for diversity

-[early stage research] decompose gans according to physics (e.g. background + foreground). in general image = shape + textures + lightning
-[huge success] correlation in gans between objects and activations in some neurons 
(turning on/off some neuron activation we can edit produced images). 
correlation can be found automaticly, David Bau


# Early notes (27-28 Oct)

## Workshop: Multi-Discipline Approach for Learning Concepts - Zero-Shot, One-Shot, Few-Shot and Beyond

Invited talk (author http://www.ceessnoek.info/)

few-shot object detection without annotation (his ICCV2019 paper) (no need for bbox ground truth, only object presences)

object2action (detect object in every frame and estimate their movement?) Localize actions
+no need for videos (zero-shot == no videos)
https://arxiv.org/pdf/1510.06939.pdf

adding language avareness (objects are not really independant, if there is a football player, there is likely a ball)
action tricks:
- >penalize objects thta are not unique for an action
- >promote objects that have high uniqueness among action regardless theri relation to the action (leaks, lol)

Sportlight speedrun

- Enhancing Visual Embeddings through Weakly Supervised Captioning for Zero-Shot Learning
- ProtoGAN: Towards Few Shot Learning for Action Recognition
- Picking groups instead of samples: A close look at Static Pool-based Meta-Active Learning
- Adversarial Joint-Distribution Learning for Novel Class Sketch-Based Image Retrieval
- Weakly Supervised One Shot Segmentation
- Object Grounding via Iterative Context Reasoning

## Workshop: Low Power Computer Vision

- MUSCO: Multi-Stage Compression of neural networks (skoltech oseledets)


## Workshop: Image and Video Synthesis: How, Why and What If?
-hierarchical text2image (bbox->mask->image)
-generate by modifying part of the image
-landmark autoencoder
-best-of-many objective for diversity

-decompose gans according to physics (e.g. background + foreground). in general image = shape + textures + lightning
-correlation in gans between objects and activations in some neurons (turning on/off some neuron activation we can edit produced images). correlation can be found automaticly, David Bau

## TODO

- FW-GAN (Flow navigated warping gan for video virtual try-on)

- Learning lightweighted LANE CNNs by self-attention distilation

- Incremental class discovery for semantic segmentation with RGBD...

- Lifelong GAN: Continual learning for Conditional Image Generation

- Image generation from small datasets via Batch Statistic Adaptation

- (force machines look same regions as humans helps, but the annotation cost?) Taking a HINT: Leveraging Explanations to Make Vision and Language Models More Grounded

- detecting the unexpected by image resynthesis (anomaly detection)

- recurrent u-net for resource constrained segmentation

- efficient segmentation: learning downsampling near semantic boundaries

- continual learning by asymmetric loss approximation with single-side overestimation

- the sound of motions

- generative adversarial minority oversampling

- memorizing normality to detect anomaly: memory-augmented deep autoencoder for unsupervised anomaly detection

- sc-fegan: face editing generative adversarial network with user's sketch and color

- adaptive inference cost with convolutional neural mixture models

- fooling network interpretation in image classification

- recursive visual sound separation using minus-plus net

- LIP: Local Importance-based Pooling

- Global Feature Guided Local Pooling

- Local Relation Networks for Image Recognition

- AttentionRNN: Structured Spatial Attention Mechanism

- Be Your Own Teacher: Improve the performance of CNN via Self-distillation

- ??? ... Shot Neural Architecture Search via Self-Evaluated Template Network


