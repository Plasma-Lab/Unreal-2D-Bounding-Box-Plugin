

# Unreal 2D Bounding Box Plugin

Welcome to the documentation of the Unreal 2D Bounding Box Plugin. A plugin designed to generate synthetic Image Detection datasets by exporting the bounding boxes of meshes in an Unreal scene.

## Labeling Actors
For each element in your scene you wish to track, add two ***actor tags*** to your element's actor: the first tag is your label (e.g., "car"), and the second tag must be "BB". 
The first tag will be used in the label file. The second tag is just here to tell the plugin to track the actor.

![actor tags](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/tags.PNG?raw=true)

## Setup the camera

The plugin uses a custom camera to be able to extract the 2D bounding boxes.
The camera is in the "content" folder of the plugin with the name **BP_Bounding_Box_Camera**.  Drop the camera in the scene and point it in direction of the tracked objects.
You can see what the camera sees by opening the file next to it called **RT_Capture**.

![files](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/files.PNG?raw=true)

![camera](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/camera.PNG?raw=true)

## Setup bounding box tracking

In your Level Blueprint, add the blueprint "**Setup 2D Bounding Boxes**" to the **Event BeginPlay** node.

![setup](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/beginplay.PNG?raw=true)

By default, the plugin will take 1920x1080 screenshots but you can choose a different resolution by editing the **Camera_SizeX** and **Camera_SizeY** variable in this node.
*Note: If you edit the size, press Play once and stop, it will have updated the camera size, you can check the view in the **RT_Capture** file.*

## Take captures

Now to take screen captures with bounding box label file, just use the **Take Screenshot With Bounding Box** blueprint.
You can either bind this blueprint to a keyboard key and tie the camera to your player view or program camera movements and automaticaly fire screenshots. (The plugin doesn't support this, you have to set this up yourself.) 

![screenshot](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/screenshot.PNG?raw=true)

Just set a path to save the captures, press Play and fire the blueprint!
It will create 2 folders when taking the captures:

- images: contains the capture files as .png
- labels: contains the label files as .csv

# What's in the label file?
![csv](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/csv.PNG?raw=true)

The label file contains 5 columns:
- label of the tracked mesh
- X1
- y1
- X2
- y2

The first Xy couple is the coordinates of the top left of the bounding box, the second one is the bottom right.

You can use the included python notebook to visualize the boxes or get the [notebook here](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/2D_Bounding_boxes.ipynb).

![results](https://github.com/Plasma-Lab/Unreal-2D-Bounding-Box-Plugin/blob/main/BB.PNG?raw=true)
