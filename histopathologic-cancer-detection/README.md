# Notebook Directory

## Contained in this notebook are three models, an image test generator, and a file sorter

### folder-seperator
- separating the cancerous and non cancerous tissue slides to their respective folders
- pushing 80% of the files to a training folder and the remaining 20% to a testing folder

### image-manipulation
This notebook is responsible for cropping the image to 32x32 pixels, since the know cancer cells are within this region.

### cnn-32x32
This notebook is responsible for running tensorflow.keras on 32x32 pixel images.

### cnn-96x96
This notebook is responsible for running tensorflow.keras on 96x96 pixel images.

### cnn-96x96-resnet50
This notebook is responsible for running the pre-trained tensorflow.keras.resnet50 on 96x96 pixel images.

### cnn-96x96-inceptinov3
This notebook is responsible for running the pre-trained tensorflow.keras.inceptinov3 on 96x96 pixel images.
