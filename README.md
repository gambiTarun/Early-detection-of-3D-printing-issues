# Early-detection-of-3D-printing-issues
This is the repository for my attempt at this [Kaggle Competition](https://www.kaggle.com/competitions/early-detection-of-3d-printing-issues). The aim of this competition is to forecast a particular type of flaw that occurs in 3D printing, which is under extrusion. Although 3D printing is a modern technique for producing objects from various 3D models, it is vulnerable to errors, and one way to identify such errors is by using a close-up camera positioned close to the printer nozzle.

# Attempts

## Dataset

### Dataset Description
This project involves a dataset containing images from 7 different 3D printers. For each 3D printer, there are between 6 to 20 prints, with each print having a series of snapshots taken from the nozzle camera approximately every 0.5 seconds.

Each print is labelled as either a "good print" or one purposefully set to produce "under extrusion". It is important to note that all snapshots within the same print share the same label.

### Objective
The goal is to build a Machine Learning model that can accurately classify the images into "good print" or "under extrusion". The challenge here is to avoid overfitting, where the model performs well on the training data but fails to generalize to unseen data.

### Dataset Files
train.csv - The training data set of over 81000 labeled images
test.csv - The test data set of over 25000 unlabeled images
sample_submission.csv - A sample submission file in the correct format
images - Folders for the images, named after the printer IDs.

### Columns in the Dataset
img_path - The path of the snapshot.
printer_id - The ID of the 3D printer. It can be used during training, but not allowed during testing.
print_id - The ID of the print. It can be used during training, but not allowed during testing.
has_under_extrusion - The label for the image. 1 means under extrusion is present, while 0 means the image shows a good print.

Note: printer_id and print_id are not to be used during testing as they are highly correlated to the ground truth and would result in overfitting to the characteristics of specific printers or prints.

## Custom CNN module

I trained a simple CNN architecture model achieving test accuracy of around 64%. Model consists of CNN layers, Max pool layers, and Fully connected layers.

## Residual Attention Module

This model includes a unified backbone called Attention-56 network, which comprises multiple stacked attention modules and residual blocks. Following the flattening layer, the network is divided into four independent fully connected output heads, each responsible for one parameter. These heads classify their respective parameters as either low, good, or high. The attention modules are composed of two branches: a trunk branch containing residual blocks and a mask branch that carries out down- and up-sampling operations.

This model achieves a test accuracy of around 74%.

## Reference
* Fei Wang, Mengqing Jiang, Chen Qian, Shuo Yang, Cheng Li, Honggang Zhang, Xiaogang Wang, Xiaoou Tang: “Residual Attention Network for Image Classification”, 2017; [http://arxiv.org/abs/1704.06904 arXiv:1704.06904].

* Brion DAJ, Pattinson SW. Generalisable 3D printing error detection and correction via multi-head neural networks. Nat Commun. 2022 Aug 15;13(1):4654. [doi: 10.1038/s41467-022-31985-y](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9378646/pdf/41467_2022_Article_31985.pdf). PMID: 35970824; PMCID: PMC9378646. 
