# Mangrove-Tree-Counting-DL-CV

### Tech/Tools Used
-__Deep Learning/ Computer Vision:__ YOLOv8 for object detection, custom HSV filter for domain-specific post processing
__Python Libraries:__ NumPy, Matplotlib

## 1. Problem 
Mangroves are disappearing rapidly, accurately estimating the population density of mangroves is a major challenge. Existing research for tree counting are mainly designed for commercial species like oil palm and olive trees.

## 2. Dataset
The data collection was conducted manually for a few days, took place along the Straits of Malacca, Malaysia, right infront of The Shore Hotel and Residences, an area known for its accessible mangrove vegetation. Images were taken in different angles from the side view of mangrove trees, under different presentations and reflection of natural phenomena (rising tide, changes in weather, etc).

This custom dataset consisting ___610 images___, hereby referred to as TheStraitsMangrove24. The images were then annotated utilising Roboflow, and split into train, validation, and test set in ___7:2:1 ratio___.

The dataset is accessible upon request.

## 3. Methodology
Deep learning model, specifically YOLO, were utilised as the baseline object detection module. Several versions of YOLO (YOLOv5,YOLOv8, and YOLOv11) in small(s) variant were chosen for this project. 

Upon experiments, __YOLOv8__ performs well and achieved better result than YOLOv11 despite the latter being a newer and more advanced version. This was attributed to the limited size of dataset which significantly influences the training dynamic of deep learning models. 
1. __Model Complexity:__ YOLOv11 introduces a more complex architecture with many parameters. Such a high-capacity model may not generalise well and is prone to overfitting. In contrast, YOLOv8 has lighter architecture with fewer parameters, which are less prone to overfitting on small datasets.
2. __Data efficiency:__ YOLOv11 strengths are more evident when trained on larger scale datasets, while YOLOv8 is optimised for data efficiency and has been widely adopted in low resource environments.
<img width="615" height="256" alt="image" src="https://github.com/user-attachments/assets/3bb1fd47-501e-4f9f-8107-6994bbfc9b84" />

YOLO performs satisfactory in detecting tree trunks however still exhibits limitations in challenging scenarios, particularly under low-light conditions or when other object share similar characteristics with tree trunks. Therefore, this study proposes a __Hybrid Trunk Detection (HTD) Model__ to enhance detection and overcome limitations of YOLO. The HTD Model leverages YOLOv8's robust object localization capabilities, followed by a domain-specific __computer vision filter (HSV)__ to confirm the presence of actual tree trunks within each predicted bounding box.

## 4. Evaluation
Result of YOLOv8 and proposed HTD Model, where HTD outperforms the baseline model YOLOv8:
<img width="649" height="230" alt="image" src="https://github.com/user-attachments/assets/0b9aebe3-dcd4-44b8-aa15-8766404c6a14" />

Visualisation result of the HTD Model, where it clearly excluded non tree trunks object in similar textures, reduce misclassification of overlapping tree trunks:
<img width="1627" height="837" alt="image" src="https://github.com/user-attachments/assets/8ecd1323-8cf4-4127-997a-5fcf1bd36c8c" />
<img width="1611" height="456" alt="image" src="https://github.com/user-attachments/assets/6be2cb72-a685-45f0-bca3-3feac2065fb0" />


