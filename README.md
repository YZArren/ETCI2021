# ETCI2021
This is the method of the etci2021 champion team

# Requirements
CUDA 11.0
Python 3.7
Pytorch 1.7
Torchvision 0.8.2
medpy 0.4.0
batchgenrators 0.21

# Introduction
The competition involves a supervised learning task—participants will develop algorithms to identify flood pixels after training their algorithm against a training set of synthetic aperture radar (SAR) images. Because the rivers where the floods are are mostly slender structures, this increases the difficulty of identification. We tried popular algorithms but failed to obtain satisfactory results. We note that in segmentation, both semantic information and spatial information are the key to the success of the network. U-Net achieves this through a decoder, which receives semantic information from the bottom of the U and recombines it with a high-resolution feature graph obtained directly by the encoder by skipping the connection.Unlike other segmented networks, such as FCN and Deeplab before it, this allows U-Net to fine subdivide the structure very well.Inspired by nnU-Net, we use nnU-Net to implement flood identification experiments.Our approach, both visually and using the intersection over union (IOU) score , achieves excellent performance.

![image](https://github.com/YZArren/ETCI2021/blob/main/pic/net.png)

# Results
* input picture:</p>
![image](https://github.com/YZArren/ETCI2021/blob/main/pic/org1.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/org2.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/org3.png)
* Ground Truth</p>
![image](https://github.com/YZArren/ETCI2021/blob/main/pic/mask1.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/mask2.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/mask3.png)
* Our Methed</p>
![image](https://github.com/YZArren/ETCI2021/blob/main/pic/infer1.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/infer2.png)   ![image](https://github.com/YZArren/ETCI2021/blob/main/pic/infer3.png)

# Usage
1.Because of the data preprocessing method in nnunet, the original 2D image needs to be converted to nii.gz format.Here we refer to this [case](https://github.com/MIC-DKFZ/nnUNet/blob/master/nnunet/dataset_conversion/Task120_Massachusetts_RoadSegm.py).

2.After completing data transformation, run the following code for infer.
```
python predict.py -i input_folder -o output_folder
```
# ETCI2021 Leaderboard
|RANK|TEAM|IOU SCORE|
|------|:------:|:------:|
|**1**|**Arren(Our)**|**0.7681**|
|2|Skawakita|0.7671|
|3|sayak|0.7654|
|4|shagun1511|0.7506|
|5|neptuneai|0.7466|

# Acknowledgements
our code is based on nnUNet, Thanks to Fabian Isensee for the codes of nnU-Net.
