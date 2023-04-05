# Models to predict porosity using ultrasounds

## Introduction
As a PhD student, my research focused on developing models to predict XCT (X-ray computed tomography) images from ultrasonic data.  A clear correlation was found between the images obtained through the methodology explained in the [previous project](/P1_Relation_XCT_&_Ultrasonics). 

At this time the challenge consisted in developing models to predict the XCT image from the ultrasonic data. For this task the challenge was to measure different properties of the ultrasonic data. One option was to do the traditional approach in the field, computing only the attenuation of the ultrasonic signals. However, I decided to compute several further ultrasonic features and let the models decide which were the most relevant.

<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">   For the prediction of the XCT image a comprehensive set of  features could be computed from the ultrasonic signals.
</div>
&nbsp;

## 1. Extracting Features from the Signals and Feature Selection

The ultrasonic data consists of a collection of signals that can be interpreted. I applied several operations to extract features from the data, and performed feature selection using various algorithms such as filtering by the F-test, mutual information statistics, recursive feature extraction (RFE) with linear regression, and filtering by feature importance of a regression tree.

<img src="images/P2_imgs/Ascan_con_puntos.png?raw=true"
        width="39%" /> <img src="images/P2_imgs/correlation_matrix_c6.png?raw=true"
        width="60%" />

## 2. Models and Error Analysis

Once I identified the most relevant ultrasonic features, I trained the models and performed error assessment using various techniques for data visualization and error assessment. Interpretability and explainability of the models were crucial factors in the whole process, and only models that yielded a weight of the used features were used. Four models: Lineal, multilineal, regression tree and random forest were trained. The most informative technique was the visualization of the MSE and error as a heatmap. The following images are an example of it: 

<img src="images/P2_imgs/c4_eval_pred_real.png?raw=true"
        width="658" /> 
<img src="images/P2_imgs/Error_analysis_data_visualization.png?raw=true"
        width="658" />

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> The models were successful in the estimating the XCT. but there was a need to improve the dispersion in the graph of measured versus predicted.
</div>
&nbsp;

## 3. Final Improvement of the Models: Superpixels and the Prediction in Homogeneous Regions

The sliding window process of the methodology caused the dispersion in the graph of measured versus predicted. Modeling edge regions with sudden changes in porosity content, combined with the influence of the resolution difference between XCT and UT, introduced noise in the models. To solve this issue, I added a step to estimate porosity in regions with uniform ultrasonic values using the superpixel [SLIC](https://scikit-image.org/docs/dev/api/skimage.segmentation.html#skimage.segmentation.slic)  algorithm on the attenuation image. This step resulted in much more uniform estimations of the XCT porosity.

<img src="images/P2_imgs/Superpixels.png?raw=true"
        width="100%"/>
<img src="images/P2_imgs/Superpixels_pred_vs_measured.png?raw=true"
        style="width: 80%;display:flex;margin:auto"/>
&nbsp;

## 4. Follow-up Work: Developing Models to Estimate Porosity

The prediction of the porosity measured in the XCT was a success. The most relevant features were obtained, the models and its predictions were assessed by different techniques, and the estimation using homogenous regions reduced the error standard deviation. If you're really curious and want to dive deep into our work, you can check out the presentation we gave at the [MMLDT-CSET conference](https://www.morressier.com/o/event/6128fdff7000f900128c7f3b/article/612f6735bc98103724100767).

My next goal was to develop models to estimate porosity in different composite materials. The unknown influence of the different morphology, such as the shape, size, and distribution of the porosity, posed a challenge in estimating porosity. In my subsequent projects,[Segmentation of the porosity in 3D using CNNs](/P3_Segmentation_Porosity_3D), and in the [Classification of the porosity based on signal analysis](/P4_Classification_porosity), I tell the different approaches to address this challenge.