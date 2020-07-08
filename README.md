# YoloV3ForCustomDataset
Course offered by Udemy. Created and taught by Valentyn Sichkar.


[Course Certficate]()

[Section 1 : Object Detection Using Simple Thresholding](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section1/01SimpleObjectDetectionByThresholdingWithMask.ipynb)

[Section 2 : Object Detection From Image Pretrained YOLO On COCO Dataset](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section2/02YoloV3PretrainedImageDetection.ipynb)

[Section 2 : Object Detection From Camera Using Pretrained YOLO On COCO Dataset](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section2/02YoloV3PretrainedCamera.ipynb)

[Section 2 : Object Detection From Real Time Video Using Pretrained YOLO On COCO Dataset](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section2/02YoloV3PretrainedRealTime.ipynb)

[Section 3 : Labelling Dataset In YOLO v3 Format](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section3/03DataPreparation.ipynb)

[Section 4 : Converting Annontations](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section4/04ConvertingAnnotations.ipynb)

[Section 4 : Creating Custom Datset In YOLO v3 Format](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section4/04DataPreparation.ipynb)

[Section 4b : Joining Labelled and Custom Datset In YOLO v3 Format](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section4b/04JoiningDatasets.ipynb)

[Section 5 : Converting Annontations for Traffic Signal Dataset](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section5/05ConvertingAnnotations.ipynb)

[Section 5 : Labelling Traffic Signal Dataset in YOLO v3 Format](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/blob/master/Section5/05DataPreparation.ipynb)

# Resources not included in the repository due to size

[Clone this repository for OIDv4 ToolKit](https://github.com/EscVM/OIDv4_ToolKit)

[Link for YOLO Network Weights trained on COCO Dataset (Used in Section 2)](https://drive.google.com/drive/folders/1ec5eIn1G9xs-SfdXEhjCLDEc1HHJ_USv?usp=sharing)

[Link for CSV File Containing Train Annotations (Used in Section 4)](https://drive.google.com/file/d/1HUSi5Iu3Y3GjJ1qJcRz6JkM_wtgILy9y/view?usp=sharing)

[Link for Traffic Dataset Download FullIJCNN2013.zip (Used in Section 5)](https://sid.erda.dk/public/archives/ff17dc924eba88d5d01a807357d6614c/published-archive.html)

[Link for yolov3.weights (Used in Darknet)](https://drive.google.com/file/d/1lwzseO2rlwcithPUhnIjIOVztk0rmRrP/view?usp=sharing)

## Important commands for dataset preparation and execution and checking the result

### To Prepare Images in YOLO Format

1) Install LabelImg using pip install LabelImg
2) Draw bounding boxes around the objects and save it in YOLO Format.

### Section 3 : Extracting Frames from Video

1) Install ffmpeg
2) Go to the directory of the video and type ffmpeg -i filename.mp4 -vf fps=4 image-%d.jpeg
3) Extracted images will be the in directory of the video
4) Draw bounding boxes around the extracted video using LabelImg
5) Prepare the dataset in YOLO Format using 03DataPreparation Notebook

### Section 4 : Installing OIDv4 toolkit for downloading images from a huge dataset

1) Clone the OIDv4 Repository [https://github.com/EscVM/OIDv4_ToolKit]
2) Activate your python environment and navigate to the directory where the repository was cloned and type the following command : pip install -r requirements.txt
3) To verify type the following command : python main.py -h
4) After verifying type the following command : python main.py downloader --classes Car Bicycle_wheel Bus --type_csv train --multiclasses 1 --limit 9
5) 9 Images of the classes Car Bicycle_wheel and Bus will be downloaded and two csv file will also be downloaded in the OID Folder.
6) One CSV file will contain annotations and the other will contain and the class description.
7) In order to verify type the following command : python main.py visualizer
8) Rename the Car_Bicycle wheel_Bus folder to Car_Bicycle_wheel_Bus to avoid errors
9) Convert annotations from the csv file using 04ConvertingAnnotations notebook
10) Prepare data in YOLO Format using 04DataPreparation notebook


### Section 4b : Joining the labelled and custom datasets

1) Copy only the images that we downloaded from the huge dataset [Section4](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/tree/master/Section4/Dataset/train/Car_Bicycle_wheel_Bus) and the images we extracted from the video [Section 3](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/tree/master/Section3) to a new folder LabeledCustom.

2) Run the 04JoiningDatasets in Section 4b to join the dataset and prepare it in YOLO Format.

### Section 5 : Traffic Dataset

1) Download the traffic dataset from the link provided
2) Convert annotations from the csv file using 05ConvertingAnnotations notebook
3) Prepare data in YOLO Format using 05DataPreparation notebook


### Note : In all notebooks use the proper directory 

### Note : In Sections 3,4,4b,5 if you want to check if we have prepared the images correctly create a classes.txt file in the same order and open labelImg and verify

### Section 6 : Darknet

1) Install Tensorflow with GPU Support using thistutorial from Jeff Heaton [Tensorflow GPU](https://www.youtube.com/watch?v=qrkEYf-YDyI)

2) Install darknet using the this tutorial [Darknet Installation](https://medium.com/analytics-vidhya/installing-darknet-on-windows-462d84840e5a)

3) Create the folder weights and add yolov3.weights

In the data folder, add the test-image.jpg and test-video.mp4

##### Command to check installation of darknet

1) For image file 
Go to darknet root directory and type : darknet.exe detector test cfg/coco.data cfg/yolov3.cfg weights/yolov3.weights -thresh 0.85 -ext_output data/test-image.jpg

2) Output will be stored as predictions.jpg

3) For video file
Go to darknet root directory and type : darknet.exe detector demo cfg\coco.data cfg\yolov3.cfg weights\yolov3.weights
-thresh 0.85 -dont_show data\test-video.mp4 -out_filename result.avi

4) Output will be stored as result.avi
