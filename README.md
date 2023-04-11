This was a side project I started in 2021 in which I used molybdenum disulfide (MoS2) transmission electron microscopy data at two magnification levels (500,000x and 200,000x) from my work to identify the nanostructure of MoS2 using the FastAI dataloader and unet_learner classes. MoS2 under certain reaction conditions forms aligned vertical nanosturcturs as shown in the image below with one example of such nanostructure marked in red.
<br></br>
<img src="/TEM_test_images/MoS2 example.png" alt="tem example of molybdenum disulfide/MoS2 marked in red"/>


I created segmentation mask images manually using VGG Image Annotator (VIA V2; https://www.robots.ox.ac.uk/~vgg/software/via/) and generated images based on the masking based on the tutorial here: https://towardsdatascience.com/generating-image-segmentation-masks-the-easy-way-dd4d3656dbd1

After creating the image masks, I trained ResNet-34 model on 15 cycles with following results:
<br></br>
<img src="/Screenshot 2023-04-10 at 16-44-08 Fastai_Vision_MoS2_Prediction - Jupyter Notebook.jpg" alt="fastai training and validation losses for 15 cycles"/>

As shown, the training and validation loss drops to <40% with no further changes in results.

After training, I have 3 test images shown below: 1) a TEM of MoS2 image that wasn't used in training or validation sets for the model at 50000X magnification and 2)  a TEM of MoS2 image that wasn't used in training or validation sets for the model at 20000X magnification.

For the first image, I have good matching with very little of the MoS2 nanostructure missed as the image is at a similar magnification to the training and validation data.
<br></br>
<h3>Original image:</h3>
<br></br>
<img src="/TEM_test_images/395.png" alt="tem result of molybdenum/Mo and molybdenum disulfide/MoS2"/>
<br></br>
<h3>Identified MoS2:</h3>
<br></br>
<img src="/TEM_test_images/test image 1 result.png" alt="tem result with ML-identified MoS2 nanostructure"/>

The second image, however, has poor identification of the MoS2 nanostructure due to the lower magnification of the results, resulting in the nanostructure being hard to distinguish from the unreacted molybdenum (Mo). Another issue might be the dependence on contrast for identifying the MoS2 nanostructure.
<br></br>
<h3>Original image:</h3>
<br></br>
<img src="/TEM_test_images/537.png" alt="tem result of molybdenum/Mo and molybdenum disulfide/MoS2"/>
<br></br>
<h3>Identified MoS2:</h3>
<br></br>
<img src="/TEM_test_images/test image 2 result.png" alt="tem result with ML-identified MoS2 nanostructure"/>

This was tested with the third image, which was taken from literature (Jung, Yeonwoong, et al. Nano letters 14.12 (2014)), which was a lower magnification image of tungsten disulfide (WS2) at around 50000X. This image has better contrast compared to the second image and as a result, an improved detection of the nanostructure.
<br></br>
<h3>Original image:</h3>
<br></br>
<img src="/TEM_test_images/WS2 example.png" alt="tem result of tungsten/W and tungsten disulfide/WS2"/>
<br></br>
<h3>Identified MoS2:</h3>
<br></br>
<img src="/TEM_test_images/test image 3 result.png" alt="tem result with ML-identified MoS2 nanostructure"/>
