# Problem Statement
- Given a grocery store shelf image, detect all products present in the shelf image (detection only at product or no-product level)
- Implement a single shot object detector with only "one" anchor box per feature-map cell.

# Dataset Preperation
- Used ProductImagesFromShelves in order to extract image co-ordinates for every product on every shelf
- Used image width and height to calculate bounding box xmax and ymax co-ordinates

# Data Augmentation
- Crop every image randomly for 6 Trials, if there is no product in any cropped image then do not use that image.
- This helps in creating Train and Eval Datasets of sizes 24010 and 11415 respectivey
- Also used augmentation parameters ssd_random_crop and random_horizontal_flip in SSD Mobilenet V1 config file

# Detection Network 
- MobileNet V1
- Changed aspect_ratios, min_scale, and max_ratio parameters in config file of the pretrained model to use only 1 anchor box per feature-map cell.
- The network has been trained for 50000 steps
- Experimented with aspect ratios 1.0, 0.5 and 0.33
- The aspect ratio giving the highest mAP is 0.5 with scale of 0.5

# Training Parameters/Hyper-Parameters
- Used RMS Prop Optimizer with initial_lr of 0.004 and decay_factor of 0.95
- Also used momentum_optimizer_value of 0.9 and decay of 0.9
- Most of the paramter used are unchanged from the actual config

# Notebooks and Files
- SSD_Training.ipynb - Notebook that shows how model was trained and which checkpoint was saved
- SSD_Evaluation.ipynb - Notebook that shows evaluation of the trained model on the test set
- SSD_Testing.ipynb - Notebook that can be used to test the model by passing an image
- ssd_mobilenet_da_20000.config - MobileNetV1 config file
- images - Folder containing test images

# Instructions to run the test notebook/file
- Install all the requirements from requirements.txt file and extract model.zip
- Start jupyter-notebook or jupyter-lab
- Open SSD_Testing.ipynb, and run the given cells one by one
- To run the file ssd-training.py, supply argument --image="path-of-image". To check all the valid arguments type python ssd_training.py -h

# Clarification of values in metrics.json
- mAP - Value computed across all IoU thresholds, IoU=0.50:0.95
- precisio - Computed by keeping IoU threshold as 0.75
- recall - Value computed across all IoU thresholds, IoU=0.50:0.95
- Reached mAP of 0.683 using just a single anchox box per feature-map cell
