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

[Link for yolov3.weights (Used in Section 6)](https://drive.google.com/file/d/1lwzseO2rlwcithPUhnIjIOVztk0rmRrP/view?usp=sharing)

[Link for darknet53.conv.74 (Used in Section 6)](https://drive.google.com/file/d/1TvQkxcfS92lvYEYusMnBYFsHX4Bb8We-/view?usp=sharing)

## Important commands for dataset preparation and execution and checking the result

### To Prepare Images in YOLO Format

* Install LabelImg using pip install LabelImg
* Draw bounding boxes around the objects and save it in YOLO Format.

### Section 3 : Extracting Frames from Video

* Install ffmpeg
* Go to the directory of the video and type ffmpeg -i filename.mp4 -vf fps=4 image-%d.jpeg
* Extracted images will be the in directory of the video
* Draw bounding boxes around the extracted video using LabelImg
* Prepare the dataset in YOLO Format using 03DataPreparation Notebook

### Section 4 : Installing OIDv4 toolkit for downloading images from a huge dataset

* Clone the OIDv4 Repository [OIDv4](https://github.com/EscVM/OIDv4_ToolKit)
* Activate your python environment and navigate to the directory where the repository was cloned and type the following command : pip install -r requirements.txt
* To verify type the following command : python main.py -h
* After verifying type the following command : python main.py downloader --classes Car Bicycle_wheel Bus --type_csv train --multiclasses 1 --limit 9
* 9 Images of the classes Car Bicycle_wheel and Bus will be downloaded and two csv file will also be downloaded in the OID Folder.
* One CSV file will contain annotations and the other will contain and the class description.
* In order to verify type the following command : python main.py visualizer
* Rename the Car_Bicycle wheel_Bus folder to Car_Bicycle_wheel_Bus to avoid errors
* Convert annotations from the csv file using 04ConvertingAnnotations notebook
* Prepare data in YOLO Format using 04DataPreparation notebook


### Section 4b : Joining the labelled and custom datasets

* Copy only the images that we downloaded from the huge dataset [Section4](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/tree/master/Section4/Dataset/train/Car_Bicycle_wheel_Bus) and the images we extracted from the video [Section 3](https://github.com/MBadriNarayanan/YoloV3ForCustomDataset/tree/master/Section3) to a new folder LabeledCustom.

* Run the 04JoiningDatasets in Section 4b to join the dataset and prepare it in YOLO Format.

### Section 5 : Traffic Dataset

* Download the traffic dataset from the link provided
* Convert annotations from the csv file using 05ConvertingAnnotations notebook
* Prepare data in YOLO Format using 05DataPreparation notebook


### Note : In all notebooks use the proper directory 

### Note : In Sections 3,4,4b,5 if you want to check if we have prepared the images correctly create a classes.txt file in the same order and open LabelImg and verify

### Section 6 : Darknet

* Install Tensorflow with GPU Support using thistutorial from Jeff Heaton [Tensorflow GPU](https://www.youtube.com/watch?v=qrkEYf-YDyI)

* Install darknet using the this tutorial [Darknet Installation](https://medium.com/analytics-vidhya/installing-darknet-on-windows-462d84840e5a)

* Create the folder weights and add yolov3.weights

* In the data folder in the darknet directory add the test-image.jpg and test-video.mp4 files

##### Command to check installation of darknet

* For image file 
Go to darknet root directory and type : darknet.exe detector test cfg/coco.data cfg/yolov3.cfg weights/yolov3.weights -thresh 0.85 -ext_output data/test-image.jpg

* Output will be stored as predictions.jpg

* For video file
Go to darknet root directory and type : darknet.exe detector demo cfg\coco.data cfg\yolov3.cfg weights\yolov3.weights
-thresh 0.85 -dont_show data\test-video.mp4 -out_filename result.avi

* Output will be stored as result.avi


#### After checking if darknet works

* Copy the ts_data.data from the Traffic Dataset and custom_data.data from Car_Bicycle_wheel_Bus dataset to the cfg folder in the darknet directory
* Open the yolov3.cfg file in the cfg folder in the darknet directory and copy its contents to four different files namely yolov3_ts_train.cfg, yolov3_ts_test.cfg, yolov3_custom_train.cfg, yolov3_custom_test.cfg and save it in the cfg folder.
* Open the two files for training, uncomment lines # batch=64 # subdivisions=16 and change the value of batch to 32. Delete the lines batch=1 , subdivisions=1 . Save results. 
* Open two files for testing and delete lines # batch=64 , # subdivisions=16 . Save results. 
* Next is changing max_batches (i.e) total number of iterations for training and the general formula used is  max_batches = classes * 2000 (but not less than 4000)
* Steps are calculated as 80% and 90% from max_batches.
* For example, if number of classes is equal to 2, then:
  * max_batches=4000
  * steps=3200,3600
* Next, it is needed to update number of classes in every of three yolo layers in the end of
the configuration files. Also, it is needed to update number of filters in convolutional layers right before such every yolo layers but not anywhere else. It is needed in order to properly connect convolutional layer that is right before yolo layer in accordance with number of classes in dataset.
* General equation that represents how to calculate proper number of filters in three convolutonal layers right before every of three yolo layers is as following 
 *  filters = (classes + coordinates + 1) * masks
* For example, for COCO dataset it will be as following: filters = (80 + 5) * 3 = 255
