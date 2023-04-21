# Early-detection-of-3D-printing-issues
The aim of this competition is to forecast a particular type of flaw that occurs in 3D printing, which is under extrusion. Although 3D printing is a modern technique for producing objects from various 3D models, it is vulnerable to errors, and one way to identify such errors is by using a close-up camera positioned close to the printer nozzle.

# Attempts

## Custom CNN module

I tried a simple CNN architecture achieving test accuracy of around 64%. Model consists of CNN layers, Max pool layers, and Fully connected layers.

## Residual Attention Module

This model includes a unified backbone called Attention-56 network, which comprises multiple stacked attention modules and residual blocks. Following the flattening layer, the network is divided into four independent fully connected output heads, each responsible for one parameter. These heads classify their respective parameters as either low, good, or high. The attention modules are composed of two branches: a trunk branch containing residual blocks and a mask branch that carries out down- and up-sampling operations.

This model achieves a test accuracy of around 74%.

## Reference
* Fei Wang, Mengqing Jiang, Chen Qian, Shuo Yang, Cheng Li, Honggang Zhang, Xiaogang Wang, Xiaoou Tang: “Residual Attention Network for Image Classification”, 2017; [http://arxiv.org/abs/1704.06904 arXiv:1704.06904].

* Brion DAJ, Pattinson SW. [Generalisable 3D printing error detection and correction via multi-head neural networks.] (https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9378646/pdf/41467_2022_Article_31985.pdf) Nat Commun. 2022 Aug 15;13(1):4654. doi: 10.1038/s41467-022-31985-y. PMID: 35970824; PMCID: PMC9378646. 
