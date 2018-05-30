# tool_human_pose_predict
Using openCV and Deep learning openPose Tensorflow we predict the pose of a tool and upper human and relate them.

The goal of this project was to use a single camera to detect the pose of both a surgeon and the tool held by a surgeon to accurately represent the correct orientation of a tool for a particular image-guided surgical navigation method not mentioned here. I wanted to relate the pose of the human with the pose of the tool using minimal equipment.  Here I use deep learning methods from the openPose project done by CMU, except I use the tensorflow version [tf-pose-estimation](https://github.com/ildoonet/tf-pose-estimation) that turned out to be very useful and work alright if you want to run openPose and you don't have a screaming GPU or want to mess with CUDA.

This project consists of 2 parts:

1) Basic Human Upper-Body Pose Direction Prediction 
2) Basic Tool Pose Direction Prediction

## Basic  Human Pose Prediction

To predict Human Pose we use a modified version of tf-pose-estimation which I extract and show only the upper points that we need for the human.  Then I use `solvePnP` from openCV to predict a general direction of where the torso is facing. There are definitely better ways, but it does alright even with the minimal points and lack of complete rigidity.  Face pose does much better.

## Basic Tool Pose Direction Prediction

For this segment we first generate and print out ARUCO markers 1-4 to be used as a marker on the tool.  This needs to be attached to a 4 sided object (I use cardboard) which can then be positioned around the tool (I use a pair of scissors for example).

Then the ARUCO detection code is used to detect the orientation of the scissors.  This might need some additional work to get it perfect.

## Output

You can see 2 circles on the screen at output.  Since I really only care about the direction of the human and tool on the horizontal plane and within a general 4 quadrants (hence the 4 sided marker cube, since the navigation program does the rest) I just show the orientations of the tool and the human using this. 

## To Run
```
TODO: Write code to run project.
```

## Video

Here is a gif of my final output.  It worked surprisingly better than what I expected, but still is quite a rough prototype.

[Tool/Human Pose Predict](https://www.youtube.com/watch?v=dwwHXLx3BIo)
