# Project Name

My model is trained to detect traffic signs and stop signs in a photo, video, or live stream. 

![VTjAzGN](https://github.com/user-attachments/assets/f04c6f8c-5bbd-47e3-8869-a5f2062fe391)

## The Algorithm

I trained my model by using train.py on my Jetson Orin Nano. It trains each epoch one at a time to be able to detect traffic signs and stop signs based on the dataset I downloaded. It augments and normalizes the data so that it can classify traffic signs and stop signs.

## Running this project

1. SSH into your Jetson Orin Nano
2. download open images datasets for traffic signs and stop signs using open_images_downloader.py
3. train them using train.py
4. test it out:
for an image:
cd into /jetson-inference/python/training/detection/ssd
then run:
NET=~/jetson-inference/python/training/detection/ssd/models/traffic_signs_detect_model

detectnet   --model=$NET/modelname.onnx   --labels=$NET/labels.txt   --input-blob=input_0   --output-cvg=scores   --output-bbox=boxes imagepath imagename.jpg

for a video:
detectnet --model=models/my_model.onnx \
          --labels=models/labels.txt \
          --input-blob=input_0 \
          --output-cvg=scores \
          --output-bbox=boxes \
          --threshold=0.5 \
          input_video.mp4 output_video.mp4

for a livestream:
detectnet --model=models/my_model.onnx \
          --labels=models/labels.txt \
          /dev/video0

https://youtu.be/Ej1NK8Bz8uA
