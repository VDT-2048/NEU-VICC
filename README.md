# NEU-VICC
# Dataset acquisition and processing
We build an image acquisition system to effectively collect visible and infrared images in multiple scenes. As shown on the left in Figure, our image acquisition system consists of a Kinect V2 camera, a tripod, and a mobile platform. Kinect V2 includes an RGB camera, an IR camera, and a depth camera, which can meet our visible and infrared image needs. The resolution of the RGB camera is 1920×1080, and that of the IR camera is 512×424. To simulate the overhead angle of the surveillance camera, we mount the Kinect V2 camera on a tripod. In addition, the Kinect V2 camera supports vertical Angle adjustment to take images from different vantage points. At present, some intelligent surveillance cameras can realize pedestrian tracking and automatically change the shooting angle according to the location of the pedestrian. We fixed the tripod to a mobile platform with universal wheels and rotated the mobile platform to simulate the way an intelligent camera would shoot. 
This paper mainly studies person Re-ID task, which does not involve person detection. Therefore, in order to reduce the impact of background clutter, we process the raw image and crop the person. Due to the increasing accuracy and detection efficiency of the current object detection algorithm, we did not use traditional manual cropping. Instead, we used the YOLO V5 object detection algorithm to detect pedestrians and then crop the bounding box of the pedestrian. As shown on the right of Figure, the YOLO V5 can accurately detect pedestrians in visible and infrared images.

![The overview of dataset building](https://github.com/VDT-2048/NEU-VICC/assets/101933818/98fa6699-5c30-41be-a421-b8b12519c948)

# Dataset Description
Using the above image acquisition system and processing method, we construct the first cross-modality clothes-changing dataset. Our dataset consists of images of four visible scenes and two infrared scenes. We show the location of our 6 cameras and the shooting details in Figure 5. Cameras 1 and 2 are placed in the room and hall, respectively, to capture visible pedestrian images of the indoor scenes. To capture pedestrian images under different lighting conditions and backgrounds, we place camera 4 and camera 5, respectively, in the gate and in the plaza to capture visible pedestrian images in outdoor scenes. As seen in Figure 5, compared with the indoor scene, the outdoor scene has a broader range of pedestrian activities and more complex background clutter. To compensate for the poor imaging of RGB cameras in dark conditions, we use infrared cameras 3 and 6 to capture infrared images of pedestrians in dark halls and passages, respectively. Our dataset contains 16,632 visible images and 8,374 infrared images of 107 pedestrians. Figure 6 shows the number of persons per camera. In each scene, a pedestrian has about 50 consecutive images with different poses and perspectives.
![The plan of the shooting scene](https://github.com/VDT-2048/NEU-VICC/assets/101933818/2c07f805-0ae2-415b-9a35-9b06c2b87640)

![Overview of NEU-VICC dataset](https://github.com/VDT-2048/NEU-VICC/assets/101933818/ea115e4f-df27-4f4e-ace6-451f0254dda8)

Current cross-modality person Re-ID datasets assume that pedestrians will not change clothes in different cameras, such as SYSU-MM01 and RegDB datasets, which limits the application of cross-modality person Re-ID in intelligent security. For example, suspects may change their clothes to avoid capture. To address this problem, the clothes of the same person in different cameras are different in our NEU-VICC dataset. As shown in Figure 7, if one person appears in all 6 cameras, he has at least four different outfits; if appearing in only 3 cameras, he has at least three different outfits.

![The scheme for clothes-changing](https://github.com/VDT-2048/NEU-VICC/assets/101933818/71aaa72a-de3b-41e6-91ef-81f9ce43abda)

In addition, to further narrow the gap between our dataset and the real surveillance camera system, we added some challenging scenarios: 1) Different people wear the same or similar clothes (see Figure 8a). 2) In sunny weather, if the camera shoots against the sunlight, overexposure will occur, failing to see the details of the pedestrian (see Figure 8b). 3) Surveillance cameras don't always capture full pedestrian images. When pedestrians are covered by vehicles, wearing masks or hats, surveillance cameras can only capture partial features of pedestrians (see Figure 8c). 4) Pedestrians often make intrusive gestures in the presence of surveillance cameras, such as lowering their heads to play with their mobile phones or carrying backpacks or handbags (see Figure 8d).
![The examples of some challenging scenarios in our NEU-VICC dataset](https://github.com/VDT-2048/NEU-VICC/assets/101933818/a29f47cb-33b6-4aad-80eb-16f1186ca4a6)

# Semantic-Constraint Clothes-Changing Augmentation Network (SC3ANet)
The Semantic-Constraint Clothes-Changing Augmentation Network (SC3ANet) contains three main components: 1) Semantic-Constraint Clothes-Changing (SC3) module, guiding the model to learn clothes-irrelevant features. 2) The two-stream backbone network that learns modality-specific and modality-sharable representations. 3) The Dual-Granularity Constraint Loss (DGCL) module, mitigating inter-modality and intra-class differences.
![The proposed framework](https://github.com/VDT-2048/NEU-VICC/assets/101933818/92a896d7-c7a6-48aa-af62-35fd9ebb9afa)


# Download the dataset
The dataset and code are available at: https://pan.baidu.com/s/1nOETHkQuweLQDVVLfOapkA?pwd=esxp 

# Paper
https://www.sciencedirect.com/science/article/abs/pii/S092523122301233X

# Related Survey
RGB-T Image Analysis Technology and Application: A Survey [J]. Engineering Applications of Artificial Intelligence, 2023, 120, 105919. https://www.sciencedirect.com/science/article/abs/pii/S0952197623001033
