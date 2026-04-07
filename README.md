# Synthetic Dental X-Ray Generation and Segmentation Analysis
This project aims at developing a GAN model to generate synthetic ortopanoramic dental X-ray images, and training and evaluating a YOLO-based segmentation model on real and synthetic datasets. The main focus is to assess how well a segmentation model trained on real data generalizes to synthetic images and to identify its potential limitations. Several GAN architectures have been tested (StyleGAN-ADA2, Pix2Pix). The synthetic data performance has been evaluted with a YOLOv8-seg model. 


This repository includes:
- Training and testing codes;
- A link to the datasets used;
- Project presentation

The projects has been handled in sections and this repository is structured following that same logic.
The work has been divided into three sections: **Image Generation**, **Segmentation** and **Evaluation**.

# Image Generation
Different GAN architectures have been tested. 
- a **StyleGAN2-ADA** model to generate realistic synthetic orthopanoramic images. It was trained on a mix images dataset (**DENTEX**, **TUFTS**) which were pre-processed in order to match training criteria and optimize convergence.
- a **Pix2Pix** model to generate realistic synthetic orthopanoramic images by filling segmentation masks. It was trained on a mixed dataset comprising of segmentation labels and images (DENTEX, UFBA-425) that were preprocessed in order to match training criteria and optimize convergence. During pre-processing, we leveraged the Segment Anything Model (**SAM**) to refine and enhance the quality of the dataset masks, improving the conditional generation results.
- A **Real-ESRGAN** Super Resolution model to upscale synthetic images and obtain better image clarity and realistic results. It was trained using the preprocessed datasets from the styleGAN2-ADA training. This model was fundamental for obtaining High resolution images (512x512) from low resolution synthetic GAN-generated images (265x256). This approach ensured superior results despite hardware constraints and shorter training windows (utilizing 2x NVIDIA T4 GPUs with 16GB VRAM).


# Segmentation
The segmentation process is based on YOLOv8 model

# Evaluation and Ablation study


\## aggiungere descrizione di come si lanciano i vari script
