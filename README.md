# 🔬 Cell Counting & Cell Segmentation

## Overview
The objective of this project is to utilize deep learning to perfrom the basic Microscopy tasks
Cell Counting & Cell Segmentation. Each tasks has its own file:

Cell Counting is trained on 
>cell_counting.ipynb

with the dataset
>BBBC005_v2_images

Cell Segmentation is trained on
>cell_segmentation.ipynb

with the dataset
>BBBC005_v2_ground_truth

## 🧫 Context - Cell Counting
**Cell Counting** is the simple task of counting the number of cells in an image. 
This task can be used to keep track of cells that survive an intervention or experiement. 

ex: Cells drawn form a cancer cell line, will be counted after an anticancer compound is applied to them. 
Deep learning systems will help keep track of living cells without human intervention, thus helping analysis
and reports of the experiement.

With Deep Learning techniques, **DeepChem** and **data modeling**, we automate and scale the cell tracking process to
derive faster, more reliable results without the need for human intervention. 

**Cell Lines** are cells cultivated from a given source, grown stabely in laboratories.

## Data - Cell Counting
**BBBC005_v1_images** is a data set of cell images derived from Broad Bioimage Benchmark Collection. 
Each image is processed as NumPy's (10, N, M, 3) format or (i images, N pixels heigh, M pixels wide, RGB Values)
Each image of cells has information recorded into its file title. For example: 

SIMCEPImages_P24_C100_F48_s03_w2.TIF

SIMCEPImages_**well**_C**cells**_F**blur**;_s**samples**_w**stain**.TIF

**well**: standard 384-well plate format used where rows are named A-P with columsn 1-24. Ramge(A-P,1-24)

**cells**: number of cells in the image. Range(1-100)

**blur**:  amount of focus blur applied. Range(1-48)

**sample**: number of samples. Range(1-25)

**stain**: 1s are cell body stains. 2s are nuceli stains. Range(1 or 2)

Our goal of cell counting can be achieved by string interpolating the filename into seperate variables and storing their values.
**Cells** will be our target variable. The other variables won't help too much as predictors at least not for cell counting.

## 🧫 Context - Cell Segmentation
**Cell Segmentation** is the more complex task of distinguishing cells and background in an image. 
**Segmentation Masks** are the binary or grayscale images that segmentation models are trained on. They are images that essentially 
"color in" each cell as a binary pixel. A common way to get these segmentation masks is to use human segmenters to generate 
the images neede by hand. 

## Data - Cell Segmentaion
**BBBC005_v1_ground_truth** is a folder containing human generated cell segmentations for teh first 1200 images in **BBBC005_v1_images**.
Our goal is to use these cell segmentation images as labels to train the our neural network, with BBBC005_v1_images as our records.

We can use the library ImageDataset from DeepChem to store each segmentation image as storable information. 
