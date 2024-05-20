Brain tumors are among the deadliest diseases worldwide, with gliomas being particularly common. Physicians and radiologists rely on MRI and CT scans for diagnosis. However, this process is susceptible to human error and can be time-consuming, especially when a timely diagnosis is critical. To assist radiologists, deep learning is being utilized. Deep learning has demonstrated remarkable performance in medical imaging over the years. Consequently, a large dataset is being used to train AI models to ensure accurate diagnosis and facilitate early treatment of the disease.

![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM_DATASET_STRUCTURE.png)

All BraTS23 mpMRI scans are available as NIfTI files, categorized as T2 Fluid Attenuated Inversion Recovery (Flair), native T1 (T1), T2-weighted (T2), and post-contrast T1-weighted (T1Gd). These scans were obtained using different clinical protocols and various scanners from multiple institutions.

Annotations include GD-enhancing tumor (ET — label 3), peritumoral edematous/invaded tissue (ED — label 2), and necrotic tumor core (NCR — label 1). More details are available here.

The dataset comprises 1251 patient cases labeled by expert radiologists. However, cases in the validation set are not labeled. Consequently, the dataset is divided into five folders: four for training and one for evaluation.

The dataset is organized in the following directory structure. Please make any necessary adjustments based on your specific requirements and ensure to include additional supporting files in the dataset directory.


![Example Image](https://github.com/Madovah/IRM-segemntation-with-BRATZ2023-2D/blob/master/IRM2.png)

image from [Baid et al](https://arxiv.org/pdf/2107.02314v1)

