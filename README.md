![image](https://user-images.githubusercontent.com/122312679/229404999-3ff3b489-8e94-4416-945c-512ae2f80ec7.png)

# Predicting Pneumonia through X-Ray Image-Processing
authored by Jae Heon Kim

## Overview


The goal of this project is to build a deep learning model that can accurately predict the presence of pneumonia in patients based on their chest X-ray images. The model will be used by medical professionals at Mt Sinai Hospital to improve the accuracy of pneumonia diagnoses and reduce the number of false positives generated by current detection methods.

To achieve this, we will preprocess the chest X-ray images and extract features using convolutional neural networks. We will then train and validate the model using a dataset of chest X-ray images of normal people and people with pneumonia. Once the model is trained, we will evaluate its performance on a separate test dataset and optimize its hyperparameters to achieve the desired level of accuracy and minimize false negatives.

The final model will be a valuable tool for medical professionals, enabling them to quickly and accurately diagnose pneumonia in patients and provide timely treatment, without subjecting healthy individuals to unnecessary second-level pneumonia screening.

## Business Understanding
The objective of this project is to create a deep learning model that can accurately diagnose pneumonia in patients based on their chest X-ray images. The primary stakeholders of this project are the medical professionals at Mt Sinai Hospital, who are seeking a reliable and efficient means of diagnosing pneumonia in patients.

Our goal is to develop a highly accurate model that prioritizes the reduction of false positives, as this can help medical professionals to quickly identify and treat patients with pneumonia while minimizing the need for unnecessary follow-up testing for those who do not have pneumonia.

Reducing false positives can have significant benefits for the hospital, including improved operational efficiency, reduced costs, and increased patient satisfaction. By enabling faster and more accurate diagnoses, our deep learning model can streamline the diagnosis process and help medical staff to better manage their resources and workload.

In addition to these benefits, our model can also improve patient outcomes by facilitating earlier treatment for patients with pneumonia, which can lead to faster recovery times and improved overall health. By improving the accuracy and efficiency of pneumonia diagnoses at Mt Sinai Hospital, our deep learning model can make a valuable contribution to the field of medical diagnosis and help to improve patient care.

## Data Understanding
### Data Description
The dataset contains chest X-ray images (anterior-posterior) of pediatric patients between the ages of one to five years old, obtained from Guangzhou Women and Children's Medical Center, Guangzhou.

The data is available on Kaggle at the following link: https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia.

The dataset is organized into three folders (train, test, val) and includes subfolders for each image category (Pneumonia/Normal). There are a total of 5,863 JPEG images in the dataset, which have been pre-screened for quality control by removing all low-quality or unreadable scans.

The diagnoses for each image have been graded by two expert physicians to ensure accuracy and reliability. To account for any grading errors, the evaluation set has also been checked by a third expert. The dataset is intended for use in training and evaluating AI systems for the detection of pneumonia in chest X-ray images.

The data is available under a Creative Commons Attribution 4.0 license, and the original source of the data is the Guangzhou Women and Children's Medical Center, Guangzhou. A citation for the dataset is available in a research article published in the journal Cell, and the dataset is also available on Mendeley Data.

### Data Examples
![image](https://user-images.githubusercontent.com/122312679/229408222-5fd79415-4f45-4a82-a8b0-cfc0edc491d5.png)
![image](https://user-images.githubusercontent.com/122312679/229408257-b249171f-36c8-4cb7-840d-9184dfa76b2a.png)

## Data Preparation
At this step every image was scaled for better processing. Also, a random division within train data was made to create a validation data. This validation data will play a pivotal role in training the model. Image-generators were instantiated so that modeling can take place.

## Modeling
Our baseline model was a simple convolutional neural network model with just a single flattening hidden layer.
<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/122312679/229409683-ba5cdd0a-9226-4035-bb91-1f6adba99471.png"></td>
    <td><img src="https://user-images.githubusercontent.com/122312679/229409709-93e21d9b-cd45-4ec2-9e64-c99ddcf93937.png"></td>
  </tr>
</table>

The model's performance was already remarkable, setting a high bar for future models to surpass. We proceeded to experiment with various deep learning techniques to enhance its performance further. The graph below displays a comparison of each model's recall and precision, with our focus on increasing precision while maintaining a high level of recall. The dotted lines represent the average recall and precision values of all the models.

![image](https://user-images.githubusercontent.com/122312679/229422291-80fbf780-119a-43bc-863e-76c7ca00b280.png)

After testing numerous models utilizing various deep learning techniques, we ultimately selected the fifth model as our final choice. While the seventh model displayed an appealing precision score, it came at the expense of increased false negatives, which was not desirable.

The final model we selected underwent a rigorous evaluation process and demonstrated superior performance in terms of both precision and recall. It was able to accurately detect instances of pneumonia in X-ray images, while minimizing the occurrence of false negatives. Further details regarding this model are provided below.

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/122312679/229422599-028b7df6-e6c1-42f8-97c2-0cb4945989e1.png"></td>
    <td><img src="https://user-images.githubusercontent.com/122312679/229422637-7534ccf6-1d87-46ab-9d21-088037ca517e.png"></td>
  </tr>
</table>

It consisted of VGG-16, Flatten layer, Dense layer of 512, and finally a sigmoid funtion in its output layer. Additional layers only created overfitting models.

## Evaluation

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/122312679/229422944-51962aa1-dee6-4a8c-938e-6ea7414ee84f.png"></td>
    <td><img src="https://user-images.githubusercontent.com/122312679/229422976-29f4af6c-0639-4115-92e6-6a86276989c4.png"></td>
    <td><img src="https://user-images.githubusercontent.com/122312679/229422998-a8177c85-3d1b-44f4-bf4e-5aaad832ab25.png"></td>
  </tr>
</table>

Although our study has primarily emphasized precision score, we have also taken measures to ensure that false negatives are not overlooked. The three X-ray images in question represent examples of false negatives, which highlight a potential weakness of our model, particularly in bacterial cases. We aim to continue our research in order to enhance the model's ability to distinguish such cases accurately.

## Conclusion
Although we were able to maintain the recall score of our simple baseline model, we notably improved the precision score through our research efforts. Nevertheless, we recognize that there is still room for further refinement of our models, which could result in even more favorable outcomes.

By leveraging this model, Mount Sinai could potentially optimize their pneumonia detection process, resulting in cost savings in terms of staff, space, and other resources.

## Next Steps
In order to improve the accuracy and fairness of the lung disease detection project, our next steps involve collecting more data, particularly X-ray images of healthy lungs, as well as gathering data from a more diverse population. Specifically, we aim to acquire data from men and individuals outside of China, as the current dataset may not provide a representative sample of the general population.

## Repository Structure
```
├── [data]
│    ├── [modified]
│    └── [original]
├── [pdf]
│    ├── notebook.pdf
│    └── powerpoint.pdf
├── .gitignore
├── README.md
├── notebook.ipynb
└── powerpoint.pptx
```
