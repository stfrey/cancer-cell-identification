# Notebook Directory

## Contained in this notebook are three models, an image test generator, and a file sorter

### cohort-tissue-slides-sorter
This notebook is responsible for...
- separating the cancerous and non cancerous tissue slides to their respective folders
- pushing 80% of the files to a training folder and the remaining 20% to a testing folder

### image-generator
This notebook is responsible for...
- testing openslide to open the `SVS` files.
- observing the changes in detail when the level and tile size is changed.
- observing the changes in tile count when the level and tile size is changed.
- observing the changes in detail when cropping and compressing the image at a set level and tile size.
- testing functions to run through all images inside of a folder.


### cnn-wholeslide-compressed
This notebook is responsible for running tensorflow.keras on wholeslide images compressed to a pixel size of 600x600.

### cnn-wholeslide-cropped
This notebook is responsible for running tensorflow.keras on wholeslide images cropped to the center 600x600 pixel region

### cnn-tiles
This notebook is responsible for running tensorflow.keras on the second highest magnification level with a pixel count of 8320x8320 in the center of the slide.
