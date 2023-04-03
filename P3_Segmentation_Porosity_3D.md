## Segmentation of the porosity using CNNs
### Introduction. 
The porosity is the main defect when manufacturing composite materials. For that reason every composite component of the aerospace industry is inspected using ultrasounds to certify its quality. The inspections have a share approximately between the 15-25% of the final cost of the component. In previous posts we saw how I developed a methodology and models to estimate the amount of porosity using ultrasounds(UT) and X-ray computed tomography (XCT). In this post the goal is to show the work carried out to improve the information UT provides about the size, shape, and distribution of the porosity, which has been proved to have an impact in the performance of composite components.

One approach consists to perform the ultrasonic inspection with the greatest resolution possible, to try to see how far this imaging technology can reach in terms of definition and clarity. The porosity is usually formed of voids, with the larger ones measuring up to several hundred micrometers, and the smaller ones around the dozens of micrometers. Probably the main obstable is the trade-off between the parameters that impact in the resolution of the ultrasonic image. To provide some examples, the higher the ultrasonic frequency, the better resolution. However, high frequencies may not be able to go through the thickness of the material, and therefore would not provide the information of the porosity in all the part.  

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;">    In the improvement of the resolution of imaging, probably the main obstable is the trade-off between the parameters that impact in the resolution.
</div>

&nbsp;
### 1. The collaboration with the ITEFI and the optimization of the ultrasonic inspections.
The first obstacle I faced was that I had no ultrasonic equipments available at my home experimental lab, the [IMDEA Materiales](https://materials.imdea.org/), to perform the inspections with the resolution I wanted. The equipments that I needed were the so called phased arrays, more info about them [here](https://www.olympus-ims.com/en/ndt-tutorials/phased-array/). Luckily, I was able to contact with [Jorge Camacho](https://www.itefi.csic.es/en/staff/camacho-sosa-dias-jorge) from the Spanish Research Council (CSIC), and at the end of the day establish a collaboration between his group and one of my PhD director's group, Federico Sket. Then we carried out the inspections of my materials with several phased arrays, using different frequencies. To keep it simple, we found the most optimal frequency was the 10 MHz. But the best result, the one that did surprise us, came after a meeting when we realized that we needed to focus more in the scan direction, and that a possible way to do so was by using an acoustic lense. The way this instrument works is equivalent to the effect of an optical lense such as the ones used in microscopy. With the phased array of 10MHz and a lense the resolution of the images enabled to distinguish most of the medium or large sized voids, yet, in some cases the UT seemed to yield false positives, probably produced by structures other than porosity (resin rich areas, composite plies...). The video below shows a composite part measured by XCT (left), and phased array (UT) right, it can be appreciated the similarities between the voids in XCT (black regions) and the same voids seen in UT (white structures).

<img src="images/P3_imgs/Optimization_UT.png?raw=true"
        width="100%" /> 
<video src="images/P3_imgs/XCT_PA_Comparison_portfolio_edited.mp4" controls="controls" class="center" style="width: 50%;"> </video> 
&nbsp;
<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">   We thought that the use of convolutional neural networks(CNNs), would help in the segmentation of the true voids in the phased array UT.
</div>

&nbsp;
### 2. Labeling the ground truth.
To train the CNN two approaches were studied: to use the XCT as ground truth, therefore, doing an multimodal(XCT/UT) image registration process; or to label manually the ground truth. The image below show the difference in the labels for each case:  

<img src="images/P3_imgs/Manual_labels_VS_XCT_labels.png?raw=true"
        width="90%" class="center" /> 

&nbsp;
### 3. CNN Segmentation of the porosity in 3D data.
Finally, a CNN network like the one shown below was trained for the two possible ground truth. The manual labels outperformed the XCT ones, as it can be seen in the metrics. Probably the XCT labels were not adequate due to the resolution (and size) differences between the label and the UT structure.

```Latex
\begin{table}[h]
\centering
\begin{tabular}{l|l|l|}
\cline{2-3}
                                     & XCT labels & Manual labels \\ \hline
\multicolumn{1}{|l|}{Avg Training Precision:} & 0.33       & 0.74      \\ \hline
\multicolumn{1}{|l|}{Avg Training Recall:}    & 0.33       & 0.75      \\ \hline
\multicolumn{1}{|l|}{Avg Training F1:}        & 0.31       & 0.75      \\ \hline
\end{tabular}
\caption{Training evaluation metrics.}
\label{table:trainingresults}
\end{table}
```
$$
\begin{table}[h]
\centering
\begin{tabular}{l|l|l|}
\cline{2-3}
                                     & XCT labels & Manual labels \\ \hline
\multicolumn{1}{|l|}{Avg Test Precision:} & 0.29       & 0.53      \\ \hline
\multicolumn{1}{|l|}{Avg Test Recall:}    & 0.43       & 0.89      \\ \hline
\multicolumn{1}{|l|}{Avg Test F1:}        & 0.30       & 0.63      \\ \hline
\end{tabular}
\caption{Test evaluation metrics.}
\label{table:testresults}
\end{table}
$$

<img src="images/P3_imgs/CNN_struct.png?raw=true"
        width="100%" class="center" />
<img src="images/P3_imgs/Segmentation_results.png?raw=true"
        width="80%" class="center" />

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> The segmentation was better for the CNN trained on the manual labels, its results were a good start. However, to infer in 3D and use the segmented volume to other processes, the performance needs to be improved.
</div>

&nbsp;
### 4. Follow-up Work: To improve the segmentation overall performance of porosity in UT.

Big steps were performed in the assessment of porosity size, shape, and distribution using UT. The optimization of the UT techniques, together with the development of CNNs enable the segmentation of the voids. It is true the results still need to improve to be of used, but it is also true that we carried out important milestones. There are possible ways of improving the performance such as the use of further input features from the ultrasonic signal, greater datasets, and even further optimization of the ultrasonic equipment. 
