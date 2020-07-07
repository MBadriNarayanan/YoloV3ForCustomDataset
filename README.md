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


## Important commands for dataset preparation and execution and checking the result

### To Prepare Images in YOLO Format

1) Install LabelImg using pip install LabelImg
2) draw bounding boxes around the objects and save it in YOLO Format

### Extracting Frames from Video

1) Install ffmpeg
2) Go to the directory of the video and type ffmpeg -i filename.mp4 -vf fps=4 image-%d.jpeg
3) Extracted images will be the in directory of the video 
4) Prepare the dataset in YOLO Format

### Installing OIDv4 toolkit for downloading images from a huge dataset

1) Clone the OIDv4 Repository [https://github.com/EscVM/OIDv4_ToolKit]

#### Darknet

Create the folder weights and add yolov3.weights

In the data folder, add the test-image.jpg and test-video.mp4

##### Command to check installation of darknet

a)For image file 
Go to darknet root directory and type : darknet.exe detector test cfg/coco.data cfg/yolov3.cfg weights/yolov3.weights -thresh 0.85 -ext_output data/test-image.jpg
<br/>
Output will be stored as predictions.jpg

b) For video file
Go to darknet root directory and type : darknet.exe detector demo cfg\coco.data cfg\yolov3.cfg weights\yolov3.weights
-thresh 0.85 -dont_show data\test-video.mp4 -out_filename result.avi
<br/>
Output will be stored as result.avi
