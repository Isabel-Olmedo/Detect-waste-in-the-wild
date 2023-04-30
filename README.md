# 🍃 DETECT WASTE IN THE WILD WHIT YOLOv7    🌎🍃

![](https://raw.githubusercontent.com/Isabel-Olmedo/Detect-waste-in-the-wild/main/resources/portada.jpg)

![](https://img.shields.io/badge/Object--detection-%20-orange) ![](https://img.shields.io/badge/YOLO-v7-blue) ![](https://img.shields.io/badge/TACO--trash-dataset-blue)

## Motivation

Detect garbage in different environments and also the type of waste.
Then, it could be implemented for a waste classifier that performs this task autonomously.

## [YOLOv7](https://github.com/WongKinYiu/yolov7 "YOLOv7")

YOLO (You Only Look Once) is a model for generating element detections. By default this model is pretrained to detect 80 classes.

- Guide to train your own custom dataset whit YOLO, [here](https://github.com/ultralytics/yolov5/wiki/Train-Custom-Data "here").

We will be fine tuning YOLOv7 on a waste in the wild detection dataset.

## Dataset

**Dataset used for this project: Taco-trash** 🌮

Taco-Trash is a image dataaset od waste in the wild. It contains images of litter taken under diverse environments: woods, roads and beaches.

- [Taco-trash dataset](https://www.kaggle.com/datasets/kneroma/tacotrashdataset?select=data) from kaggle
- Contains 1500 images

## COCO image annotation format

COCO format is a JSON structure that determines how labels and metadata are saved for an image dataset.

The dataset Taco-trash use this format.

- ##### Code for dataset analysis -> [analyze_dataset.ipynb](https://github.com/Isabel-Olmedo/Detect-waste-in-the-wild/blob/main/analyze_dataset.ipynb) 🔎
- ##### Code for show all bounding box annotations and their label names  -> [show_boundig_box.ipynb](https://github.com/Isabel-Olmedo/Detect-waste-in-the-wild/blob/main/show_boundig_box.ipynb) ⬜

TACO-Trash dataset was labeled whit COCO format, to be able to do the training whit YOLOv7 the images labels need to be in the YOLO labeling format and the images and their labels need to be in a specific folder structure.

#### Folders structure:

###### - images 📁

- train  📂
  - img1.jpg 🖼️
  ...
- val 📂
- test 📂

###### - labels 📁

- train 📂
  - img1.txt 📄
  ...
- val 📂
- test 📂
- ***images***: each folder whitin the folder 'images' has the images that were labeled corresponding to each subset (train, val and test).
- ***labels***: Folder whit their corresponding txt of these images.

##### The code corresponding to do this preprocessing is in [prepare_dataset.ipynb](https://github.com/Isabel-Olmedo/Detect-waste-in-the-wild/blob/main/prepare_dataset.ipynb)

## Fine Tuning YOLOv7 on the Taco-Trash detection dataset 👩‍💻

To do the training we used Google Colab.

- Code in **[detect_waste.ipynb](https://github.com/Isabel-Olmedo/Detect-waste-in-the-wild/blob/main/detect_waste.ipynb)**

## Running inference 🏁

Let's run inferences on a image and images folder using the trained model and check out results. Yolov7 can also be used to detect objects in video.

In this project was used a confidentiality of 0.25, since our precision is not favorable.

- Code -> **[inference.ipynb](https://github.com/Isabel-Olmedo/Detect-waste-in-the-wild/blob/main/inferences.ipynb)**

## Results  📉

To do the training use Google Colab (GPU) and only allows run for 29 epochs, therefore the precision metric was not very favorable.

- We got an accuracy of 0.527
- During training we got mAP of 0.125 and 0.0943
- We are getting mAP of 0.214 and 0.168 respectively on the dataset.

Our model needs to be trained during more epochs to improve its metrics.

![banner](https://raw.githubusercontent.com/Isabel-Olmedo/Detect-waste-in-the-wild/main/resources/detected_waste.jpg)
