# Video-based Elevated Skin Temperature Detection - Work In Progress

## Introduction
In this work, we propose a non-contact video-based approach that detects when an individual's skin temperature is elevated beyond the normal range. The detection of elevated skin temperature is critical as a diagnostic tool to infer the presence of an infection or an abnormal health condition. Detection of elevated skin temperature is typically achieved using contact thermometers or non-contact infrared-based sensors. The ubiquity of video data acquisition devices such as mobile phones and computers motivates the development of a binary classification approach, the Video-based TEMPerature (V-TEMP) to classify subjects with non-elevated/elevated skin temperature. We leverage the correlation between the skin temperature and the angular reflectance distribution of light, to empirically differentiate between skin at non-elevated temperature and skin at elevated temperature. We demonstrate the uniqueness of this correlation by 

1) revealing the existence of a difference in the angular reflectance distribution of light from skin-like and non-skin like material and 
2) exploring the consistency of the angular reflectance distribution of light in materials exhibiting optical properties similar to human skin. 


https://user-images.githubusercontent.com/129078932/228007006-e0f545da-07f0-4580-897b-2b41ef0b84fc.mov



Finally, we demonstrate the robustness of V-TEMP by evaluating the efficacy of elevated skin temperature detection on subject videos recorded in 
1) laboratory controlled environments and 
2) outside-the-lab environments. 

Some of the results we obtained using our approach are shown below. 

![](https://github.com/CMU-Humanoids/skin-temp/blob/main/Graphical_Abstract.tif)

V-TEMP is beneficial in two ways

1) it is non-contact-based, reducing the possibility of infection due to contact and 
2) it is scalable, given the ubiquity of video-recording devices

## Contributions

In this paper, we develop an approach to infer the presence of elevated skin temperature from the video of a person's face. In summary, our main contributions are:

1) Mathematical foundation for elevated skin temperature detection based on skin angular reflectance properties
2) Demonstration of the uniqueness of facial skin reflectance properties that allow the detection of elevated skin temperature
3) Experimental validation of approach in controlled and outside-the-lab settings to demonstrate robustness of the approach
4) Video dataset of subjects with normal skin temperature and artificially elevated skin temperature 

## Method

In this work, we utilize an RGB camera instead of an infrared camera, which allows the integration of the method with a smartphone application or other camera-based systems such as digital cameras, thereby increasing its potential scale and accessibility due to the ubiquity of video-recording devices [[1]](http://openaccess.thecvf.com/content/ICCV2021W/V4V/html/Revanur_The_First_Vision_for_Vitals_V4V_Challenge_for_Non-Contact_Video-Based_ICCVW_2021_paper.html),[[2]](https://link.springer.com/chapter/10.1007/978-3-031-14771-5_22). Studies [[3]](https://www.sciencedirect.com/science/article/pii/S1350449515000523), [[4]](https://asmedigitalcollection.asme.org/IMECE/proceedings-abstract/IMECE2012/127/260549) found that the measured skin temperature drops by more than $4^o$ F with an angular deviation of $45^o$ and above from normal incidence. Arieli et al. have empirically studied the differences in the magnitude of apparent skin temperature drop with a change in infrared camera viewing angle for different skin temperatures. The study also found that the apparent drop in skin temperature with increasing viewing angle is steeper for higher skin temperatures. 

In order to leverage the dependence of the change in apparent skin temperature with camera angle using a facial video, we calculate the skin reflectance at different instances, corresponding to different camera angles. Measuring the absolute skin temperature using the calculated skin reflectance requires knowledge of ambient temperature and skin-specific parameters such as emissivity, which are difficult to measure using a facial video. To circumvent the need to measure skin-specific and atmospheric properties, we calculate an intermediate ratio called the `Radiatively Inspired Reflectance ratio' (RIR ratio) instead of attempting to calculate the absolute temperature. We utilize the calculated RIR ratio and the camera viewing angle to determine the HOT factor from the lookup function we generated from the results of the study by Arieli et al., which documented the changes in apparent skin temperature with the camera viewing angle. To determine the RIR ratio and the camera viewing angle at each frame of the video, we need to track the subject's face throughout the video using a face tracking algorithm. We employ a real-time face tracking algorithm called ZFace for obtaining facial regions-of-interest (ROI). After extracting the facial ROIs, we obtain the reflectance of the ROI by computing the mean pixel intensity. The RIR ratio is calculated as

$$\frac{T_i}{T_j} \approx \left[\frac{\tau_{atm}~\left(I_{p_i} - 1\right) + 1}{\tau_{atm}~\left(I_{p_j} - 1\right) + 1} \right] ^{1/4}$$

where $T_i$ and $T_j$ are the temperatures of the skin at two different head poses ($i$ and $j$), $\tau_{atm}$ is the transmittivity of the atmosphere, $I_{p_i}$ and $I_{p_j}$ are the pixel intensities of the tracked facial landmark at the two head poses $i$ and $j$. Head pose $i$ is the base head pose (defined by the head pose in the first frame of the video), where the head is aligned with the camera line of sight. Head pose $j$ is the head pose at any instant in the video. The difference in the yaw angle with respect to the first frame of the video provides a measure of subject head angular deviation for the particular frame ($|yaw_i - yaw_j|$). The RIR ratio and the subject head angular deviation are provided as input to the lookup function which outputs the HOT factor value. The HOT factor is used to classify subjects into having elevated or normal skin temperature, using a binary threshold classifier. 

![](https://github.com/CMU-Humanoids/skin-temp/blob/main/Screenshot%202023-03-27%20at%201.38.42%20PM.png)


## Dataset

Coming soon.

## Running the script

Coming soon.

## Citation

If you use any of the data or resources provided on this page in any of your publications we ask you to cite the following work.

Dasari, A., Revanur, A., Jeni, L. A., & Tucker, C. S. (2023). Video-based Elevated Skin Temperature Detection. IEEE Transactions on Biomedical Engineering.

