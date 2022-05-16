# Object and Velocity Detection

## Github Link - https://github.com/rohan2810/object-detection
## Drive Link (video data collection + with csv of sphero runs) - https://drive.google.com/drive/folders/19V8njKMYWYhGU0-PjzF-p8a0mEBT6n5U?usp=sharing

<br>
<br>

## Disclaimer - Github does not allow weights or revisions to the yolov5 folder - please read README file on how to upload weights

## Instructions for only testing results of project

#### Object Detection
- Copy the runs folder into the yolov5 folder
- Please install pytorch using the first line given in yolo_detections.ipynb
- Please ignore and do not run the following two lines
-     !git clone https://github.com/ultralytics/yolov5) as yolov5 is already set up
-     !python train.py --img 320 --batch 16 --epochs 200 --data dataset.yml --weights yolov5s.pt --workers 2
- Please run all the other given lines besides the above two to see the object detection model identifying the sphero

#### Velocity Detection
- For testing purposes, we have provided an excel sheet for you to use which has all of our data collected - irobot/excel/combined.xlsx
- If you desire to use your own data, follow the steps provided in the sections below
- Open lstm_prediction_model.ipynb
- If on Google Colab please upload the combined.xlsx to Colab directly
- Run all the steps/code provided and all the results for velocity detections should be shown



<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />
<br />


## Instructions for setting up project from scratch and running project yourself

- The first step is to open the roboflow_yolo.ipynb file.
- Start running all the lines provided in the given script
- We have provided the roboflow API where we have labeled images of the Sphero (object which we want to detect)
- Running this script should take a while due to training the data through several epochs.
- Process can take anywhere from 30 minutes to multiple hours depending on hardware specifications.
- After running each and every line provided in the roboflow_yolo.ipynb file, you will see generated weights which you can export to yolov5. The folder structure should be yolov5/runs/train/real_exp/weights.

#### Object Detection
- Copy the runs folder and the trim_35 folder or copy your own weights generated if you decided to retrain the model into the yolov5 folder
- Please install pytorch using the first line given in yolo_detections.ipynb
- Please ignore and do not run the following two lines 
-     !git clone https://github.com/ultralytics/yolov5) 
-     !python train.py --img 320 --batch 16 --epochs 200 --data dataset.yml --weights yolov5s.pt --workers 2
- Please run all the other given lines besides the above two to see the object detection model identifying the sphero

#### Preprocessing Data Steps
- A sample video has been uploaded to test procedure - irobot/videos/trim_36.mp4
- Open area.ipynb
- Run the second code block - getFramePerSecond script
- Once the run is finished you will see frames generated under irobot/frames/trim36
- Open the file irobot/sphero_data/36.csv
- The number of frames generated should approximately match the number of rows in the csv sheet
- Copy the trim_36 folder into the yolov5 folder
- Go back to the area.ipynb script and cd into yolov5 (the line has been written on the area.ipynb file)
- After that, run the !python detect.py line to extract the areas from the frames
- Once the process finishes, the generated txt and images should show up under runs/detect/exp
- Copy the exp folder into irobot/yolo_output_frames
- Go into the labels folder for exp and run command prompt
- For windows run the line to combine everything into all.txt
-         (for /l %a in (1 1 846) do @type "%a.txt")>all.txt
- For mac run the line to combine everything into all.txt
-         cat *.txt > all.txt       
- Replace the number 846 above in the for line to the number of txt files generated in the exp/labels folder
- Once done, open the irobot/excel/trim36.xlsx file
- Import the txt all.txt generated from before into the excel sheet
- You may delete the column which has all zeros, but please keep the second column with the area
- Copy the Time(s) and Velocity Total(cm/s) columns from the file file irobot/sphero_data/36.csv
- Once copied, paste it onto trim36.xlsx and you should see all the time, areas, and corresponding velocities

#### Velocity Detection
- For testing purposes, we have provided an excel sheet for you to run which has all of our data collected - irobot/excel/combined.xlsx
- If you desire to use your own data, format your excel document from the object detection results just like the one provided
- Open lstm_prediction_model.ipynb
- If on Google Colab please upload the combined.xlsx to Colab directly
- Run all the steps/code provided and all the results for velocity detections should be shown
