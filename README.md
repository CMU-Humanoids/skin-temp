# Video-based Elevated Skin Temperature Detection

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

## Dataset

The 'Data' folder contains a dataset of 28 subjects we collected for our study. 
TBD

## Running the script

TBD

## Citation

If you use any of the data or resources provided on this page in any of your publications we ask you to cite the following work.

Dasari, A., Revanur, A., Jeni, L. A., & Tucker, C. S. (2023). Video-based Elevated Skin Temperature Detection. IEEE Transactions on Biomedical Engineering.

