# Synthetic Dental X-Ray Generation and Segmentation Analysis
This project aims at developing a GAN model to generate synthetic orthopanoramic dental X-ray images, and training and evaluating a YOLO-based segmentation model on real and synthetic datasets. The main focus is to assess how well a segmentation model trained on real data generalizes to synthetic images and to identify its potential limitations. Several GAN architectures have been tested (StyleGAN2-ADA, Pix2Pix). The synthetic data performance has been evaluated with a YOLOv8-seg model. 

The whole project and all of its models have been trained on Kaggle utilising its limited free resources. Two T4 GPUs with 16gb of VRAM were utilized to train all the models present in the Repository.

This repository includes:
- Training and testing codes;
-[A link to the datasets used;](https://drive.google.com/drive/u/0/folders/1SoLyhwrIlIb3yWc00GjHQ1wihF4UbhC7)
- Project presentation

The project has been handled in sections and this repository is structured following that same logic.
The work has been divided into three sections: **Image Generation**, **Segmentation** and **Evaluation**.

# Image Generation
Different GAN architectures have been tested. 
- a **StyleGAN2-ADA** model to generate realistic synthetic orthopanoramic images. It was trained on a mix images dataset (**DENTEX**, **TUFTS**) which were pre-processed in order to match training criteria and optimize convergence.
- a **Pix2Pix** model to generate realistic synthetic orthopanoramic images by filling segmentation masks. It was trained on a mixed dataset comprising of segmentation labels and images (DENTEX, UFBA-425) that were preprocessed in order to match training criteria and optimize convergence. During pre-processing, the Segment Anything Model (**SAM**) was leveraged to refine and enhance the quality of the dataset masks, improving the conditional generation results.
- A **Real-ESRGAN** Super Resolution model to upscale synthetic images and obtain better image clarity and realistic results. It was trained using the preprocessed datasets from the styleGAN2-ADA training. This model was fundamental for obtaining High resolution images (512x512) from low resolution synthetic GAN-generated images (265x256). This approach ensured superior results despite hardware constraints and shorter training windows (utilizing 2x NVIDIA T4 GPUs with 16GB VRAM).


# Segmentation
The segmentation process is based on YOLOv8 model

# Evaluation and Ablation study

# REPOSITORY STRUCTURE

The **SEGMENTATION** and **GAN** directories contain the kaggle notebooks in which the model training was developed. Each notebook imports the necessary datasets from a google drive in which they are stored.
- GAN
    - pix2pix-training: In this notebook, a pix2pix model is trained to generate realistic 256x256 orthopanoramic images from a segmentation mask.
    - realesrgan-training: In this notebook, the real-ESRGAN Super Resolution model is trained to upscale orthopanoramic images from 256x256 to 512x512.
    - styleGAN2-ADA-training: In this notebook, a styleGAN2-ADA model is trained to generate realistic 256x256 orthopanoramic synthetic images from scratch.
- SEGMENTATION
    - yolo_aug: In this notebook, a YOLOV8-seg model is trained to correctly identify and segment teeth structures on real orthopanoramic images.
    - SAM: In this notebook, a Segment Anything Model (SAM) was deployed to refine the existing teeth masks and standardize the dataset.


The **EVAL_ABL** directory contains kaggle notebooks in which evaluation and ablation studies were conducted.
- EVAL_ABL
    - notebook 1 descrizione
    - notebook 2 descrizione
  
