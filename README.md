## MRI SEGMENTATION WITH PYTORCH-UNET/BRATZ-2023
Brain tumors are among the deadliest diseases worldwide, with gliomas being particularly common. Physicians and radiologists rely on MRI and CT scans for diagnosis. However, this process is susceptible to human error and can be time-consuming, especially when a timely diagnosis is critical. To assist radiologists, deep learning is being utilized. Deep learning has demonstrated remarkable performance in medical imaging over the years. Consequently, a large dataset is being used to train AI models to ensure accurate diagnosis and facilitate early treatment of the disease.


![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM.gif)

## DATASET STRUCTURE

All BraTS23 mpMRI scans are available as NIfTI files, categorized as T2 Fluid Attenuated Inversion Recovery (Flair), native T1 (T1), T2-weighted (T2), and post-contrast T1-weighted (T1Gd). These scans were obtained using different clinical protocols and various scanners from multiple institutions.

Annotations include GD-enhancing tumor (ET — label 3), peritumoral edematous/invaded tissue (ED — label 2), and necrotic tumor core (NCR — label 1). 


![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM2.png)

image from [Baid et al](https://arxiv.org/pdf/2107.02314v1)

For details --> [BRATZ-2023](https://www.synapse.org/#!Synapse:syn51156910/wiki/622351)

The dataset comprises 1251 patient cases labeled by expert radiologists. However, cases in the validation set are not labeled.

The dataset is organized in the following directory structure:

![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/DATASET_Structure.jpg)

## A NEW APPROACH
we devised the Training Dataset into 90% Training, 5% Test and 5% Validation. We used the most populated slice with pixels from each NIfTI files as a 2D entry. for the training, we used a new approach to consume way less ressources ( executed using GPU L4 in [Google Collab](https://colab.google) )

# First Approach: Early Fusion
We included all the scans in the training to produce a single predicted mask 2D image.

Exemple:

![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/Deeplabv%2B.png)

# Second Approach: Late Fusion
We trained the model on each type of scan then fused the predicted masks into one result of an image 2D, contructing the final fused mask is done with the majoritarian voting between the previous predicted masks, while giving the mask of the best method in terms of global results a double vote.

Exemple: 

![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/ex_t1c.png)

Image captivated & altered from :Overview of a Neural Network’s Learning Process Neural Networks and Deep Learning Course: Part 8 by Rukshan Pramoditha

In the final results, we compared the two methods: Early Fusion and Late Fusion visually, also using metrics as well.

## EVALUATION

We also used four of Pytorch Evaluation Metrics: 
- Mean Squared Error (MSE): Measures the average squared difference between the predicted and actual values, (used for individual and gloabl approaches).
- Pixel Accuracy (PA):  measures the proportion of correctly predicted pixels to the total number of pixels.(used for individual and gloabl approaches and comparaison).
- Mean Intersection Over Union (MIoU): is a common evaluation metric used in semantic segmentation tasks to measure the accuracy of the model's predictions(used for comparaison)
- Loss Function (Loss): computes the discrepancy between the predicted output and the true target output for a single data point. It is a scalar value (Training Evaluation Metric)

## Unet ARCHITECTURE  

We used DEEPLABV+, an evolved Unet architecture from the [segmentation modeL.pytorch](https://github.com/qubvel/segmentation_models.pytorch).

