# Cancer Cell Identification

![image](https://github.com/stfrey/Cancer-Cell-Identification/blob/master/Images/TissueSlides.png)

## Introduction
Cancer cell identification is commonly performed through visually analyzing tissue slides, which are extremely complex, large files. Generally, doctors often look for abnomrally shaped cells with different arrangements than the surrounding tissue and larger nuclei to identify cancerous cells [1]. To mimic this analysis, I trained a Convolutional Neural Network (CNN) to identify these abnormally shaped cells and label the slide as non-cancerous or cancerous. I ensured the difference in cells would not be a factor by using kaggle competition data of the same cancer cells [2], and squamous and adenocarcinoma cancer cells found in the lung [3].

## Sources of Data & Libraries
- Kaggle Histopathology Dataset [2]
- TCIA (The Cancer Imaging Archive) [3]

## Results & Discussion
### Kaggle Dataset CNN
The Kaggle dataset was straight forward to use and model on, because Kaggle competition datasets are usually already clean and ready to model. I first started by splitting the training data into training and validation folders, which were set to be a 80/20 split. By doing this, I was able to predict on a known dataset as to make a confusion matrix for further analysis.

The first model I ran was a CNN with dropout layers and L2 regularizers over the entire 96x96 pixel image. This model resulted in a 63.5% accuracy, which is not much better than the baseline of 59.4%. The sensitivity, or percentage of correct cancerous predicitions was 66.4%. The sensitivity score was far to low to be considered an good model, because type II errors need to be reduced to almost zero when handeling cancer data. Due to the low sensitivity score, I determined the next stop would be focusing on the 32x32 pixel region the cancer cells were in. By only changing the region and keep the model consistant, the accuracy increased to 79.1% and the sensitivity increased to 82.3%, which is far better than the initial sensitivity score but still not high enough. 

There are two other models included within the folder that need to be run off of AWS or a more powerful computer. Both of them include a pretrained model to possibly improve the accuracy and sensitivity, ResNet50 and Inception V3. 

### TCIA Dataset CNN
My next step was to work with real world data by using the Squamous and Adenocarcinoma lung cancer slides found in the TCIA database. This database had tissue slides sectioned by organ and type of cancer, which made it vary easy to ensure the model would be trained on the sample type of cells. It also had slides that were completely healty; making the modeling hopefully that much better at picking up on what's healthy and whats not. Before I was able to run a model on these images, I had to understand how to work with the SVS file tpye. Each one of these files are 100 to 800 MB when downloaded, but once openned could take tens of gigabytes of memory. Enough to crash my own computer. 

![svsfile](https://github.com/stfrey/Cancer-Cell-Identification/blob/master/Images/svs_pyramid.png)
This image from Rebecca Stone's Blog highlights the structure of these files, and how to work with them to get the desired image [4]. Using this information, I was able to obtain a whole slide image and compress it to a 600x600 pixel image or crop a 600x600 pixel image out of the center. Both of these have their own limitations, such as decreased resolution, no insurance the cancer cell will be in the cropped portion of the image, and distortated cell structures for the compressed image. To really ensure good data would be going into the model, I used the second to largest maginfication to obtain a 4320x4320 pixel image from the center of the slide. This too would also fall in the same trap as the cropped image, so more steps would need to taken to obtain multiple images for one tissue slide. 

Similar to the pretrained models for the Kaggle dataset, I was unable to run these models since the file sizes were too large and would need a more powerful computer.

## Conclusion & Next Steps
In conclusion a Convalutional Neural Network can by trained on cancer cell images; however, better resolution, computer power, and more storage is need. If those needs were met, knowing the specific locations of cancer cells and training on them could led to an optimized model similar to the kaggle competition 32x32 pixel model. To do so, which are the next steps, I need to download more tissue slides to Amazons S3 storage and run models off of their EC2 instances. Iterating over the data I can get from TCIA and other possible databases will assist with real world applications and act as a guide for future developments. I would also be interested in running these models to predict tissue types: lung; heart; brain, since that would be a limiting factor in the future.


## References
[1] American Cancer Society, https://www.cancer.org/treatment/understanding-your-diagnosis/tests/testing-biopsy-and-cytology-specimens-for-cancer/what-doctors-look-for.html

[2] Kaggle Competition Dataset, https://www.kaggle.com/c/histopathologic-cancer-detection

[3] TCIA Dataset, https://www.cancerimagingarchive.net/collections/

[4] Rebecca Stone's Blog, https://ysbecca.github.io/programming/2018/05/22/py-wsi.html
