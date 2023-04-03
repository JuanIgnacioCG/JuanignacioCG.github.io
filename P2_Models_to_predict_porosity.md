## Models to predict porosity using ultrasounds

### Introduction. 
A clear correlation was found between the images obtained through the methodology explained in the [previous project](/P1_Relation_XCT_&_Ultrasonics). At this time the challenge consisted in developing models to predict the XCT image from the ultrasonic data. For this task the challenge was to measure different properties of the ultrasonic data. One option was to do the traditional approach in the field, computing only the attenuation of the ultrasonic signals. However, I decided to compute several further ultrasonic features and let the models decide which were the most relevant.

<div style="background-color: #EDF7FF; border-color: #7C9DBF; border-left: 5px solid #7C9DBF; padding: 0.5em;">   For the prediction of the XCT image a whole set of  features could computed from the ultrasonic signals. Its selection and the development of machine learning models.
</div>

&nbsp;
### 1. Extracting features from the signals & feature selection.
The ultrasonic data can be represented as a collection of signals like the one shown below. The signals are interpretable, the three peaks are produced by physical events, and particularly the data points between the first and second peaks are the ones with the most information. A battery of operations (area, entropy, peaks analysis,...) were applied to obtain several features.

<img src="images/P2_imgs/Ascan_con_puntos.png?raw=true"
        width="49%" /> <img src="images/P2_imgs/correlation_matrix_c6.png?raw=true"
        width="49%" />

Afterwards, we had to perform the selection of the most relevant features to predict the XCT image. For that purpose several tasks were performed, including lineal correlation among features, and feature selection algorithms such as filtering by the F-test, by mutual information statistics, a recursive feature extraction (RFE) with lineal regression, and filtering by feature importance of a regression tree.  

&nbsp;
### 2. Models and error analysis.
Once we knew the most relevant ultrasonic features, it came the time to predict the XCT image. The training of models and error assessment steps were included into the methodology explained in the first part of the [project](/P1_Relation_XCT_&_Ultrasonics). The explainability and interpretability of the models played a huge factor in the whole process. Only models that yield a weight of the used features were used. Additionally, the error was assessed in different ways, being the visualization of the mean squeared error and the error were probably the most intuitive. 

<img src="images/P2_imgs/c4_eval_pred_real.png?raw=true"
        width="658" /> 
<img src="images/P2_imgs/Error_analysis_data_visualization.png?raw=true"
        width="658" />

<div style="background-color: LightYellow; border-color: LightYellow; border-left: 5px solid Orange; padding: 0.5em;"> The models were successful in the estimation of XCT. However, the dispersion in the graph of measured versus predicted was targeted as a thing to improve.
</div>

&nbsp;
### 3. Final improvement of the models. Superpixels and the prediction in homogenous regions.
The dispersion in the graph of measured versus predicted was caused from the sliding window process of the methodology. At the time of modeling edge regions with sudden changes in the porosity content, together with the influence of the resolution differecen between XCT and UT; were introducing noise in the models. A different approach consisted in adding a step to estimate in regions with uniform ultrasonic values. These regions were computed using the superpixel [SLIC](https://scikit-image.org/docs/dev/api/skimage.segmentation.html#skimage.segmentation.slic) algorithm on the attenuation image. It resulted in much uniform estimations of the XCT porosity. 

<img src="images/P2_imgs/Superpixels.png?raw=true"
        width="80%" />

&nbsp;
### 4. Follow-up Work: Developing Models to Estimate Porosity

The prediction of the porosity measured in the XCT was a success. The most relevant features were obtained, the models and its predictions were assessed by different techniques, and the estimation using homogenous regions reduced the error standard deviation. The next problem came with the data from a different composite material. The different morphology: the shape, size and distribution of the porosity, had an unknown influence in the estimation of porosity. My next goal was to be able to assess these parameters using only the ultrasonic signal. In the project, [Segmentation of the porosity in 3D using CNNs](/P3_Segmentation_Porosity_3D), and in the [Classification of the porosity based on signal analysis](/P4_Classification_porosity) I develop different approaches to tackle this problem.
