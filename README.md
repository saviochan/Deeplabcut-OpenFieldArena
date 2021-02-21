# Deeplabcut-OpenFieldArena
A Deeplabcut network trained to label mice in open field arena with topdown view.

<p align="center">
  <img width="500" height="500" src="https://user-images.githubusercontent.com/17475995/87319236-f7fc7780-c4ee-11ea-9ecb-1e373cfc64b4.jpg">
</p>

### Network configuration
The network was initialized using the pretrained network mobilenet_v2_1.0. Training dataset was augmented with the imgaug method. The network was continously trained with manually annotated videos until satisfactory results were obtained. In total, 1674 frames were labelled and ~3000000 iterations were performed. 

### Network performance 
The network was evaluated to have a 1.13px train error and 4.82px test error, using a scale factor(train-test ratio) of 0.8. We have a short 2-min video demonstrating the accuracy of our tracking: [demo](videos)

We also compared the labelling performance with a commercial video tracking software called Ethovision. As shown in speed plot below, our DLC model has comparable performance with commerical options.

#### Speed plots generated from DLC labelling data and Etho labelling data
![Speed_plot](https://user-images.githubusercontent.com/17475995/87333167-5848e480-c502-11ea-915d-f59b97f5ccbf.jpg)

### Labelling configuration
<img align="right" width="206" height="303" src=https://user-images.githubusercontent.com/17475995/87318159-94be1580-c4ed-11ea-95db-6585e17d91b4.png>
These are the body parts labelled:

- Nose
- Left ear
- Right ear
- Centroid (Body center)
- Left lateral(Left hip-joint in anatomical terms)
- Right lateral (Right hip-joint in anatmoical terms)
- Tail base
- Tail end

>**Note**: Snout, Tail base and Tail end are relative unstable key points, meaning they might be occassionally off-target in some frames.

## Step-by-Step tutorial
Follow these simple steps to start running analysis on your machine with our trained network!

### Step 1: Pre-processing of videos
To get the best results, please adjust the video to follow the specifications below:
- format: .avi
- speed: 1X
- resolution: 1080px x 1080px
- frame rate: 10fps

We used a free editor software called VSDC Free Video Editor:http://www.videosoftdev.com/free-video-editor/download
>**Note**: Changing the frame rate and resolution hinders the performance of the network.

### Step 2: Download the network
1. Download the folder [here](/downloads)
2. Create a new project in DLC
3. Place the downloaded folder in the `dlc-model` folder in your project
4. Go to the subfolder `dlc-model/iteration-0/YourprojectnameDatecreated-trainset95shuffle1.`. Rename the subfolder by replacing the text `Yourprojectname` with your project name and `Date created` with the date created
- eg. OpenFieldTestJul13-trainset95shuffle1
5. You are good to go! Click the `analyze video` tab in the DLC GUI. If you are using our network, you should see `Using snapshot-950000 for model .........../dlc-models/iteration-0/........-trainset95shuffle1` pop up in the command prompt.



