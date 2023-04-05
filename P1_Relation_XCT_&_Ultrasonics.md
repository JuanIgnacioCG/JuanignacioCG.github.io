# Relation between X-ray computed tomography (XCT) and Ultrasound (UT) for the study of porosity

## Introduction

As the start of my PhD thesis in industrial inspection of composite materials, I explored the relationship between X-ray computed tomography (XCT) and Ultrasound (UT) for the study of porosity. 

<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">    <strong>The Opportunity:</strong> The application of machine learning to improve existing ultrasonic techniques.
</div>
&nbsp;

While XCT provides a 3D volume with high resolution and detail of defects (20um), it demands more expensive equipment and higher inspection and analysis times than UT. On the other hand, UT does not provide enough detail, and its results can be difficult to interpret at times. However, We believed that machine learning models that learn patterns through the relationship between ultrasonics and XCT would improve existing ultrasonic techniques. 

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> We believed that machine learning models that learn patterns through the relationship between ultrasonics and XCT would improve existing ultrasonic techniques.
</div>
&nbsp;

## 1. Hypothesis 1: The XCT and UT techniques can be related to study the amount of porosity in a composite material

 To explore this relationship, I formulated the hypothesis that XCT and UT techniques could be related to study the amount of porosity in a composite material. the following videos show the 3D volumes of each technique. A render of four ultrasonic volumes and the inspection area with its supports, and one segmented binary volume of XCT that contains porosity as white structures.

<video src="images/P1_imgs/mini_video ultrasonidos_confondo.mp4" controls="controls" style="width: 70%;"> </video> <video src="images/P1_imgs/c4_rendered.mp4" controls="controls" style="width: 25%;"> </video>
&nbsp;

## 2. Work carried out: Developing a Methodology to Automate Volume Measurements

To collect data from the available composite material, I carried out inspection by XCT and ultrasonic testing, coded the methodology, and automated the computation of volumes. I also developed a methodology to automate the measurement of properties in the 3D volumes of XCT and UT, as shown in the following images:
<img src="images/P1_imgs/Methodology_layout.png?raw=true"/>
<img src="images/P1_imgs/Props_process.png?raw=true"/>
&nbsp;

## 3. Outcome: Communicating Results with Images

<img src="images/P1_imgs/img_different_window.png?raw=true" width="100%"/>

The images obtained by applying the methodology were used to form a final graphic to communicate the results. The 2D projection of the binary XCT and the attenuation of the ultrasonic volume are clearly correlated, but this relationship is affected by the scale of resolution of each technique. 
&nbsp;

## 4. Follow-up Work: Developing Models to Estimate Porosity

My next goal was to predict the XCT image from the ultrasonic data. In the next [project](/P2_Models_to_predict_porosity), I present the data science methodology with data splitting techniques, modeling, and error analysis to develop models to estimate porosity measured in XCT by features of the ultrasonic data.