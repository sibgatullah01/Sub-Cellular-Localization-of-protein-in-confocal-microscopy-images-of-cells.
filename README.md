# Sub-Cellular-Localization-of-protein-in-confocal-microscopy-images-of-cells.
The project taken as a Thesis Project for the Master of Science in Bioinformatics, leverages the power of Deep Learning to identify the location of protein in the cells. The project used the dataset provided by The Human Protein Atlas database.
The dataset contains confocal microscopy images in four grey channels. The four grey chennels represent four different different dye used for different biomarkers in cells.
Dye used are blue coloured DAPI for Nucleus, Yellow Alexaflour for Endoplasmic Reticulum, Red coloured Alexaflour for Tubulina and green coloured Aalexaflour for protein of interest. Based on these dyes, four different single channeled images are produced.
Images contain human cells. Each imageis a field view image of cell that has multiple cells in them of single cell line. Each cells have protein in them, represented as green dye. Images are annotated or labelled based on the location of protein in different sub-cellular compartments(Organalles). There 19 such labels
Our goal is to build a model to detect and extract individual cells from images, and then classify the cells into 19 category based on location of protein.

**Methodology**

First the four single channeled images are combined to get on RGB images. We used simple np.stack operation for combining the images.
Mask R-CNN with detectron2 is trained to detct and extract cells.
Extracted cells show large amount of variation so we resize the image with padding and size ration in ordere maintain aspect ration and minimize the information loss.

The extract cells are highly imbalanced and needed to be balanced. So we used imblearn RandomOverSampler to balance the dataset by resampling the minority class.
After preprocessing is complete, several CNN classification models are trained, including Resnet50V2, DenseNet169, VGG16, and 8-layer custom built model.

