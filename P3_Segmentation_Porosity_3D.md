# Segmentation of the porosity using CNNs

## Introduction

Have you ever wondered how the aerospace industry ensures the quality of composite materials used in manufacturing? Well, one of the most important factors to consider is porosity. To certify the quality of composite components, ultrasonic inspections are conducted, which can account for up to 25% of the component's final cost. In this post, we explore a methodology that improves the information provided by ultrasonic imaging and its impact on the performance of composite components.

Porosity is typically formed by voids ranging in size from several hundred micrometers to dozens of micrometers. A challenge is to balance the parameters that affect the resolution of ultrasonic imaging. For example, higher ultrasonic frequency can provide better resolution, but it may not be able to penetrate the thickness of the material, thereby failing to provide porosity information throughout the part.

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;">    The trade-off between resolution-impacting parameters is likely the primary obstacle in enhancing imaging resolution.
</div>
&nbsp;

## 1. The collaboration with the ITEFI and the optimization of the ultrasonic inspections

I took the initiative to start a collaboration with [Jorge Camacho](https://www.itefi.csic.es/en/staff/camacho-sosa-dias-jorge) from the Spanish Research Council to tackle the main obstacle I faced in my home experimental lab at [IMDEA Materiales](https://materials.imdea.org/) - the lack of ultrasonic equipment to inspect my materials with the desired resolution. With the help of phased arrays,more info about them [here](https://www.olympus-ims.com/en/ndt-tutorials/phased-array/), we were able to optimize the inspection frequency and discovered that using an acoustic lens could significantly improve the resolution of the images. My perseverance in finding a solution and the expertise of Jorge and Guillermo, led to a discovery that even surprised us. Check out the video below to see the similarities between the voids in XCT and the ones seen in phased array UT.

<img src="images/P3_imgs/Optimization_UT.png?raw=true"
        width="100%" /> 
<video src="images/P3_imgs/XCT_PA_Comparison_portfolio_edited.mp4" controls="controls" style="width: 50%;display:flex;margin:auto"> </video>
&nbsp;

The resolution of images improved significantly, enabling us to distinguish most medium or large-sized voids. However, we also experienced false positives, which may have been produced by structures other than porosity (e.g., resin-rich areas, composite plies).
&nbsp;
<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">   After optimizing the ultrasonic techniques, we were able to visualize individual voids through ultrasounds for the very first time. However, a new hurdle emerged as we needed to differentiate genuine defects from false positives. .
</div>
&nbsp;

## 2. Labeling the ground truth

To address this issue, we used convolutional neural networks (CNNs) to segment genuine defects in phased array UT. We considered two approaches for training the CNN: using XCT as the ground truth or labeling the ground truth manually. We found that the manual labels outperformed the XCT ones, as they were more adequate due to resolution and size differences between the label and the UT structure. 

<img src="images/P3_imgs/Manual_labels_VS_XCT_labels.png?raw=true"
        width="100%" class="center" />
&nbsp;

## 3. CNN Segmentation of the porosity in 3D data

After diligent efforts, we successfully trained a CNN model to segment porosity using a customized dataset of 2D images. The trained model was then utilized to analyze 3D data by treating it as a series of 2D slices. While the initial results are promising, with an F1 average between 0.6-0.7, further refinements are necessary to achieve optimal performance.

<img src="images/P3_imgs/Metrics_table.png?raw=true"
        style="width: 80%;display:flex;margin:auto"/>

<img src="images/P3_imgs/CNN_struct.png?raw=true"
        width="100%" class="center" />
<img src="images/P3_imgs/Segmentation_results.png?raw=true"
        width="80%" class="center" />

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> The CNN trained on manually labeled data produced superior segmentation results, which was an encouraging start. Nonetheless, for the segmented volume to be utilized in other processes and for 3D inference, performance improvements are necessary.
</div>
&nbsp;

## 4. Follow-up Work: To improve the segmentation overall performance of porosity in UT

Significant progress has been made in evaluating porosity characteristics, including size, shape, and distribution, through ultrasonic techniques. By optimizing these techniques and developing convolutional neural networks, we have been able to segment voids, although further improvement is necessary for practical application. Nevertheless, we have achieved important milestones, and there are ways to enhance the performance, such as incorporating additional input features from the ultrasonic signal, expanding datasets, and fine-tuning the used CNN and ultrasonic equipment.

If you wish to delve into the details of the work, you can refer to the paper that was presented at the [NDE4.0](https://www.ndt.net/search/docs.php3?id=27674) conference. 
