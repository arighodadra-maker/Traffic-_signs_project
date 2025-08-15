# Project Name

My project detects traffic signs in an image, downloaded video, or a live stream and alerts drivers that there is a sign nearby. 

![add![VTjAzGN](https://github.com/user-attachments/assets/6ab79ce5-e3c1-44d6-af4b-60f40f396998)

## The Algorithm

I used the jetson orin nano, VS code, train.py, and resnet to train my model. It trains one epoch at a time to classify the signs based on my dataset. It depends on the data I feed it. It augmented and normalized the data according to the dataset.

## Running this project

1. go to open images and search "traffic sign" and "stop sign"
2. download both datasets into VS code
3. train it using train.py
4. test it using these commands:
for completed videos:
detectnet --model=models/my_model.onnx \
          --labels=models/labels.txt \
          --input-blob=input_0 \
          --output-cvg=scores \
          --output-bbox=boxes \
          --threshold=0.5 \
          input_video.mp4 output_video.mp4

for live stream
detectnet --model=models/my_model.onnx \
          --labels=models/labels.txt \
          /dev/video0

for images:
cd into /jetson-inference/python/training/detection/ssd
then run:
NET=~/jetson-inference/python/training/detection/ssd/models/traffic_signs_detect_model

detectnet   --model=$NET/ssd-mobilenet.onnx   --labels=$NET/labels.txt   --input-blob=input_0   --output-cvg=scores   --output-bbox=boxes imagepath imagename.jpg
change paths as needed

[View a video explanation here](video link)
