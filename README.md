# ImageClassifier
**Author:** Viktor Törnblom

## Introduction
ImageClassifier is a Python-based application designed for classifying images using a machine-learning classifier algorithm. It is specifically tailored for processing FlowCam output and categorizing images into predefined classes, either "Junk", "Missed" or "Protists".

## Prerequisites
- Anaconda or Miniconda

## Installation

*  Create and activate the conda environment:

```
conda create -n image_classifier python=3.12
conda activate image_classifier
```
 * Install required modules:

```
conda install pandas scikit-learn
pip install opencv-python
```

## Run ImageClassifier

```
conda activate image_classifier
python \path\to\script\main.py -raw_dir example_dir
```

'Example dir' should contain the raw FlowCam output data (the script uses the tif files and the metadata CSV file).

The following directory will be generated after running the script, where the subdirectories 'Junk' and 'Protist' contain the images sorted into their corresponding class. 
```
└── Output_example_dir
    ├── report.txt
    └── Predicted_images
        ├── Junk
        ├── Missed
        └── Protist
```

#### Manual reclassification

In case you are unsatisfied with the classification made by the classifier, you may reclassify the images manually. This is done by moving the images in the 'Predicted_images' directory into the folder you find suitable. Then run the script `re_eval.py` inside the **Output_example_dir**. The new stats will be appended to the report file:

```
 Report - 4-LRM1b-day0-2         (2024-06-26 10:52)
=========================
Sample Volume Imaged (ml): 0.01773

Categories
Junk: 420
Missed: 21
Protist: 559

Estimated conc. (protists/ml): 31528.48

---------------------------------------------------------------
Manual reclassification          (2024-06-26 10:56)

Categories
Junk: 416
Missed: 21
Protist: 565

Estimated conc. (protists/ml): 31866.89
```
