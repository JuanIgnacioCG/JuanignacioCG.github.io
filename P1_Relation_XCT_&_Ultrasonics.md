## Relation between X-ray computed tomography (XCT) and Ultrasound (UT) for the study of porosity

<!-- **Relation between X-ray computed tomography (XCT) and Ultrasound (UT) for the study of porosity:**  -->
### Introduction. 
This was the start of my PhD thesis. The field area is the industrial inspection, particularly of composite materials.


<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">    <strong>The Opportunity:</strong> The application of machine learning to improve existing ultrasonic techniques.
</div>

 In the one hand, XCT provides a 3D volume with very high resolution and detail of the defects (20um), but it demands more expensive equipment, and higher inspection and  analysis times than ultrasonic testing. On the other hand, ultrasonic testing does not provide enough detail and its results are difficult to interpret in occasions.

 <div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> Machine learning models that learnt patterns through the relation of ultrasonics and XCT would improve existing ultrasonic techniques.

### 1. Hypothesis 1: The XCT and UT techniques can be related to study the amount of porosity in a composite material.

The first video shows the segmented binary volume of XCT where you can see the porosity as the white structures. The next video is a render of 4 ultrasonic volumes and the inspection area with its supports. .

<video src="images/P1_imgs/mini_video ultrasonidos_confondo.mp4"
       controls="controls"
       style="max-width: 730px;">
</video>
<video src="images/P1_imgs/mini_video c4_rendered.mp4"
       controls="controls"
       style="max-width: 730px;">
</video>


### 2. Work carried out: Develop a methodology to automate the measurement of properties in the 3D volumes of XCT and UT.

It was time to start to get data from the available composite material. The work included carrying out inspection by XCT and ultrasonic testing, the coding of the methodology and the automation in the analysis of the results.
<img src="images/P1_imgs/Methodology_layout.png?raw=true"/>
<img src="images/P1_imgs/Props_process.png?raw=true"/>


### 3. Outcome: An image shows the clear correlation between the measurement of porosity in XCT, and the attenuation obtained from the UT.

<img src="images/P1_imgs/img_different_window.png?raw=true"/>

### 4. Followup work: Develop models to estimate porosity measured in XCT by features of the ultrasonic data.

The next goal is to be able to predict the porosity quantity from ultrasonic features. In the next project link, the data science methodology with the data splitting techniques, modeling, and error analysis is presented. 
