## MRI SEGMENTATION WITH PYTORCH-UNET/BRATZ-2023
Brain tumors are among the deadliest diseases worldwide, with gliomas being particularly common. Physicians and radiologists rely on MRI and CT scans for diagnosis. However, this process is susceptible to human error and can be time-consuming, especially when a timely diagnosis is critical. To assist radiologists, deep learning is being utilized. Deep learning has demonstrated remarkable performance in medical imaging over the years. Consequently, a large dataset is being used to train AI models to ensure accurate diagnosis and facilitate early treatment of the disease.


![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM.gif)

## DATASET STRUCTURE

All BraTS23 mpMRI scans are available as NIfTI files, categorized as T2 Fluid Attenuated Inversion Recovery (Flair), native T1 (T1), T2-weighted (T2), and post-contrast T1-weighted (T1Gd). These scans were obtained using different clinical protocols and various scanners from multiple institutions.

Annotations include GD-enhancing tumor (ET — label 3), peritumoral edematous/invaded tissue (ED — label 2), and necrotic tumor core (NCR — label 1). 

For details --> [BRATZ-2023](https://www.synapse.org/#!Synapse:syn51156910/wiki/622351)

The dataset comprises 1251 patient cases labeled by expert radiologists. However, cases in the validation set are not labeled.

The dataset is organized in the following directory structure:

![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/DATASET_STRUCTURE.jpg)

## A NEW APPROACH

In the code provided, we devised the Dataset into 90% Training, 5% Test and 5% Validation. We used the most populated slice with pixels from each NIfTI files as a 2D entry. for the training, we used a new approach to consume way less ressources ( executed using GPU L4 in [Google Collab](https://colab.google) ): First we tried to train the model on each type of file, then we englobed all the files in the training to compare the five approches ( obviousely the results were better with some than others).

## EVALUATION

We also used four of Pytorch Evaluation Metrics: 
- Mean Squared Error (MSE): Measures the average squared difference between the predicted and actual values.
- Pixel Accuracy (PA):  measures the proportion of correctly predicted pixels to the total number of pixels.
- Mean Intersection Over Union (MIoU): is a common evaluation metric used in semantic segmentation tasks to measure the accuracy of the model's predictions.
- Loss Function (Loss): computes the discrepancy between the predicted output and the true target output for a single data point. It is a scalar value.

## Unet ARCHITECTURE  

We used Unet architecture from the [segmentation modeL.pytorch](https://github.com/qubvel/segmentation_models.pytorch).


![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM2.png)

image from [Baid et al](https://arxiv.org/pdf/2107.02314v1)

