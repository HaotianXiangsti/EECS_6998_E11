# EECS_6998_E11
Repo for course project of EECS_6998_E11

**Currently A More Detailed and Comprehensive Cloud Drive Version can be find at** https://drive.google.com/drive/folders/1lRZiazvJreX7Wa0dwjSKEV10RZZXxERV?usp=sharing

**It is a completed version.** 

**Cause I encountered issues of pushing the whole dataset to the repo. And every others' push is lagged.**

Want to get a better result than [ForesterNet](https://stanfordmlgroup.github.io/projects/forestnet/) NeurIPS 2020 in prediciting drivers of a deforest situation

The task is to investigate drivers of deforestation in Indonesia. The original task is an image segmentation task over Landsat 8 Satellite Images and a multi-class classification task based on the Image Segmentations.

The procedure is first train a CNN backbone until it can correctly perform image segmentation for images in the dataset. Then, with this pretrained backbone, the author perform driver classification based on the fusion between segmented parts and their corresponding multi-modal information (i.e. environment information, climate information and geo information).

The obstacles are:

* The driver for a forest loss region may change during time. (The usage of the land may change temporally) The size and usage of one region has a spatial-temporal related change
* In a fixed resolution image, there may exist more than one forest regions. Thus, we cannot perform classification directly from the whole image.
* Satellite Images have different resolutions due to different years or due to the access of the dataset makers.
* The paper only released the Dataset, no open-source code,

In my opinion, my first task is to replicate the paper with a CNN structure and simple backbone, such as Unet with Resnet 50 in it.

Then, I want to substitute the CNN backbone with SAM or just ViT to see if  it has better precision. And I want to have a decent embedding module to embedded Auxiliary Information before fusing with the Image Segmented Parts.

Finally, I want to turn the model as the backbone for a active learning pipeline. I want to propose such a framework for people investigating drivers of deforestation in other country and can save their time and money in image annotation.

**The [dataset](https://drive.google.com/drive/folders/1JtOt-g6NpLXU9xHyKfy-oR-WTpEH3A5D?usp=sharing) can be found in my Google Drive.**

The Original Flowchart of the Paper:

<img src="https://github.com/HaotianXiangsti/EECS_6998_E11/blob/main/IMGS/ForestNet_fig1.png">

---
Milestones I want to achive:

* Try Different Advanced CV Backbones.
* Introduce Multi-Modal Fusion in Image Segmentation and Improve its IOU score.
* A better way to embedded the Multi-Modal Information
* With a fine-tuned best Segmentation Model, I want use it as a backbone in an active-learning pipeline and introduce some unsupervised methods or ensemble methods to select frames which needs to be sampled.

---

**The Multi-Modal Information Categoray is shown below:**

<img src="https://github.com/HaotianXiangsti/EECS_6998_E11/blob/main/IMGS/Screenshot%202023-10-23%20222946.png">

**The Proposed Active Learning Pipeline is shown below:**

<img src="https://github.com/HaotianXiangsti/EECS_6998_E11/blob/main/IMGS/Active%20Learning_ForestNet.drawio.png">

---

**Updated from Oct. 23**

I proposed a notebook in the weekend but I wrongly deleted it before pushing to the repo. But I can describe what I did in the weekend and rebuild it this week.

* Just Finished My PhD Interviews and Accepted an Oral Offer. Thus, I devote much more time to the project.
* I build up a Dataloader to firstly load dataset.
* My first idea is to use a pretrained CV backbone from HuggingFace. I tried DETR (End-to-End Object Detection with Transformers) first to extract features and upsampled them. Next do a 2 class segmentation. The unfine-tuned result is not good. I think is mainly because the DETR is originally used for Object Detection and it failed to segment correctly on a satellite image.


