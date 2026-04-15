# metastatic-tissue-classification
Classification of Histopathological Images (from PCAM) for Cancer Detection Using Python and sklearn 

*This project was developed for the class ISyE 6740 Computational Data Analytics in 2023. The file Team_51_submitted.pdf contains full details and conclusions*

“Contrary to popular belief, the first forays into the use of digital image processing and computerized image analysis were not in face recognition or face detection, but rather for the analysis of cell and microscopy images” (1).

Histopathology has for a long time been a human-centered task: pathologists visually analyze tissue samples under microscope to detect features and patterns related to disease, particularly cancer. The whole process is time consuming, first because of the preparation of the tissue, the staining with -for example- H&E, and finally the visual inspection. 

The problem of detecting the presence of cancer in a tissue using histopathology images is considered here. This problem can be viewed naturally as a classification problem (classifying the samples into presence/absence of cancer). But I wonder whether applying techniques such as non-linear dimensionality reduction as a way of identifying non-linear patterns in tissue can improve the classification.

The dataset used for this project is the PatchCamelyon image classification dataset. It consists of 327.680 color images (96 x 96px) extracted from histopathologic scans of lymph node sections. The center 32x32 square of each patch contains at least 1 pixel of metastatic tissue. Both training and test sets are provided, with labels: 1 for presence and a 0 for the absence of metastatic tissue. 

<img width="1363" height="250" alt="image" src="https://github.com/user-attachments/assets/a6022553-dfc9-478d-8168-bd8ad14dd454" />

Link: https://github.com/basveeling/pcam

Coding was performed using Python 3.11 in Jupyter Notebook, and mainly with ML tools from the sci-kit learn module.

Analytical Approach

Since the data provides a label, the classification setting is pretty much straightforward. I carried out different combinations of classifiers, train-test split sizes and source images as detailed below:

The classifiers were chosen based on the inherent non-linearity of the data, and the binary nature of the classification. Not all of them were used at each stage or phase. For example, SVM was included basically out of curiosity, even though it was expected to perform poorly. For the first 3 phases, the following classifiers were used:

- KNeighborsClassifier with k=5 in all of the Phases, including CV
- LogisticRegression with default parameters
- SVC with ‘linear’ kernel and KSVM with ‘rbf’ kernel and C=5
- MLPClassifier with hidden layers (10,10)
- AdaBoostClassifier(DecisionTreeClassifier()) with n_estimators=200
