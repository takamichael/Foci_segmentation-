# Foci_segmentation-
Purpose of this model is to identify bright foci in fluorescent images. The dataset is composed of mitochondrial and nuclear flourescent tags

For the main training set data, 628 files, focusing heavily on mitochondrial foci, were utilized. A total of 179 images lacking proper cell segmentation were used to facilitate model training, 
supplemented by 13 images of Cox4p-GFP and 16 of Rpn11p-mCherry foci that were augmented. A separate hand-curated validation set contained 25 files from an independent Cox4p-mCherry-tagged
experiment not included in the training set data. Augmentation techniques such as CutMix, random erasing, horizontal and vertical flipping, random rotations, translations, gaussian blur (sigma of 2),
and random gaussian noise were implemented to enhance model robustness. The weights were initialized using the yeast U-Net model, designed for 512x512 input images and segmentation. 
However, the image size for training and foci detection was reduced to 40x40. Cells were identified using our segmentation pipeline, and the mother cells were cropped. 
To maintain a consistent 40x40 image size, padding was added and blank areas were filled with the minimum intensity value found within the cropped cell. For model training, 
we employed the Binary Cross-Entropy with Logits Loss (BCEWithLogitsLoss) function, Adam optimizer, and an initial learning rate of 0.0001. 
The model underwent 50 epochs of training with a batch size of 25.
