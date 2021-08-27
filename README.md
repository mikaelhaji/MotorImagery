<img width="1000" alt="Screen Shot 2021-07-31 at 11 32 20 PM" src="https://user-images.githubusercontent.com/68840767/131070151-5293c230-b32e-4627-a363-cfcce995acaf.png">



# **Abstract**

One of neuroscience's most important objectives in recent decades has been to rehabilitate people who no longer have a functioning connection between their mind and their body. A brain computer interface (BCI) based on motor imagery can detect the EEG patterns of various imagined motions, such as right or left hand movement. It allows for entirely non-muscular communication.

This is already being done effectively using costly, medical grade EEG gear, but owing to the high cost, it has not yet reached the commercial market. This study tests the performance of low-cost EEG hardware in a BCI, namely OpenBCI's Ultracortex Mark IV, in a proof-of-concept manner. As a result, we used state of the art feature extraction and categorization techniques. Using CSP for feature extraction and LDA as classifier, our algorithms are by far, better than some of the most recent BCI competitions, reaching over 78% accuracy in a 2-class BCI compared to a chance level of 50%.

# **Introduction**

BCIs are communication systems that seek to provide people with an alternative control input to computers. Changes in brain signal modulation are detected by BCIs and translated into control instructions. Electroencephalography (EEG) is now used as the primary acquisition technique for BCI. The obtained EEG signal is a macroscopic assessment of neuronal activity in the brain, which is mediated by a layer of bone, tissue, and fluid. As a result, EEG has poor spatial resolution, and the signal collection through surface electrodes makes EEG vulnerable to interference from a number of sources, including bodily movement, power line noise, and other electronic equipment.

Despite the increasing attention that BCI technology has received with the introduction of low-cost commercial EEG devices in recent years, BCIs are seldom utilised outside of the laboratory setting. This is mostly because existing BCI systems lack reliability and performance when compared to other kinds of interfaces. MI-BCI, for example, requires lengthy training trials each session, and the parameters are subject-specific. As a result, these lengthy and repeated training sessions may cause user fatigue and deterioration in performance over time. Furthermore, extended training is difficult in producing EEG oscillatory rhythms regulated during MI, such as mu (μ) and beta (β). To address these problems, previous BCI research has looked at different methods for developing novel experimental designs, specialised algorithms, and signal processing techniques that reduce the existing limits of EEG-based BCIs.

## **Contribution**

In this study, we effectively analyze and evaluate different classification methods using the uniform feature extraction technique known as common spatial patterns. The primary contribution is an exhaustive evaluation of the scope of low cost EEG hardware for the design of a Motor Imagery Based Brain-Computer-Interface System. The paper touches on every part of the BCI system in order to make it super transferable.

# **Methodology**

This section provides an overview of the study's methodology. The aim is to assess the efficacy of low-cost EEG devices for BCI applications. Many variables influence its performance. To compare the performance of the EEG hardware with other EEG gear, we must have similar performance in the other stages.

### As a result, the following stages may be used to describe our work flow:

1. Making the hardware and getting it to function
2. Putting together the software foundation
3. Data Acquisition
4. Evaluating Data with Different Algorithms

## **Hardware**

To effectively evaluate the accuracy of a Motor Imagery base Brain Computer Interface System, the Ultracortex Mark 4 with the Cyton Board was used. The hardware allowed us to use 8 channels at a 250 Hz sample rate. The main advantage when it comes to using Open BCIs device is its low cost and robust design. The use of dry electrodes reduces the time of setup to a few minutes, with the compromise of poorer data quality due to a high sensitivity to motion artefacts and high impedance.

Oftentimes, electrodes are ideally positioned according to the globally recognised 10-20 System, which is also used by the Ultracortex, for compatibility and reproducibility. However, due to the fact that we are focused primarily on the precentral gyrus, which is a part of the frontal lobe of the brain that controls muscle movement the electrode positions were altered.

Below are the exact electrode positions used for the study:

<img width="1000" alt="Screen Shot 2021-08-26 at 4 10 01 AM" src="https://user-images.githubusercontent.com/68840767/131070219-06204b58-6708-4d6d-bd06-39b8f53f5b91.png">



## **Experimental Setup and Data Acquisition**

One of the goals of this study is to collect and analyse individual motor imagery EEG data. The experimental setup for EEG recording is explained in this section.

### **Motor Imagery Tasks**

The aim of this research is to develop a proof-of-concept for a 2-class BCI, which implies that two distinct motor imagery tasks should be differentiated with a high degree of accuracy. Motor imaging tasks that are well-suited offer the greatest potential spatial dispersion in terms of brain activity. The user must also be able to visualise the matching bodily action well enough for the BCI to recognise it. Hand and leg motions were utilised in this research because they immediately result in activity in the motor cortex or the cerebellum. These two movements are now extensively utilised for 2-class motor imagery BCIs, and we employ them as well for our BCI.

### **EEG Recordings**

The participants sat comfortably in a chair with armrests in front of a computer screen. At the start of a trial (t = 0s), a cue in the shape of a text symbolising hand / feet appeared and was printed 5 times, each signifying 2 seconds. During this period, participants were instructed to complete the necessary motor imaging task until the next cue occurred at t = 10s. During the recording, no feedback was given.

# **EEG Processing**

The EEG processing for a BCI provides a plethora of paradigms from which to select. They all have benefits and drawbacks, such as varying computational and mathematical complexity, the amount of features produced for signal classification, and the assumptions they make about the underlying data. Preprocessing, feature extraction, and classification are the three stages of EEG processing.

## **Preprocessing**

Preprocessing plays an important role in BCIs. Its main goal is to improve the signal to noise ratio (SNR), which will enhance the performance of the ensuing steps. By signal the components of brain signals that reflect the users intention are meant. Preprocessing can be partitioned into spatial and temporal filtering. Preprocessing is very essential in BCIs. Its primary aim is to increase the signal-to-noise ratio (SNR), which will improve the performance of the subsequent stages. The components of brain signals that represent the user's purpose are intended by signal. Preprocessing may be divided into two categories: spatial filtering and temporal filtering.

### **Spatial Filtering**

Spatial filtering takes use of the fact that most EEG recordings include several channels. This may be used to eliminate background noise. The following are the most common spatial filtering techniques.

### **Common Average Reference**

The common average reference (CAR) technique is used to fine-tune the signal obtained by subtraction of the average of all electrodes at each electrode. This is very effective for minimising noise that is shared by all electrodes and therefore increasing usable brain occurrences of signals at electrodes

### **Temporal Filtering**

**Band Pass Filter**

Signal processing design to have a frequency response as flat as possible as band-pass is known as Butterworth filter. A Band-pass filter passes any certain frequencies and it rejects all the frequencies outside of this band. So just cascading the high pass and low pass filter we can design this band-pass filter. In this study we applied a 2nd order 5 - 50 Hz Butterworth Bandwidth Filter in order to effectively remove a low-frequency noise from EEG, which is obtained by high power DC waves.

**Notch Filter**

In contrast to HFFs and LFFs, which have a progressive roll-off curve, the objective of a notch filter is to remove a particular frequency from an EEG signal. When the field of AC current from the electrical wiring and outlets that surround the patient contaminates the record, these notch filters come in handy. The transmission curve of an ideal notch filter has a flat response for all frequencies except the nominal frequency of the filter, where there is a notch in the curve indicating near perfect attenuation of any waves at that frequency. Of course, in the real world of functioning EEG, notch filters may not perform as well as this description suggests, but they usually do a decent job of reducing undesirable AC line voltage artefacts. As such, a 60 Hz Notch Filter was applied to the data.

**Detrend Time Series Data**

A trend is a rise or decrease in the level of a time series over a lengthy period of time. Identifying and understanding trend information can aid in improving model performance. We can correct or remove the trend to simplify modeling and improve model performance. A time series with a trend is called non-stationary. An identified trend can be modeled. Once modeled, it can be removed from the time series dataset. This is called detrending the time series. If a dataset does not have a trend or we successfully remove the trend, the dataset is said to be trend stationary.

### **Feature Extraction**

The goal of feature extraction is to decrease the dimensionality of the data to a feature vector of a certain size that can subsequently be utilised for classification. There are many methods for extracting such features, each focused on a particular characteristic/property of the data.

**Common Spatial Patterns**

For the sake of the study, a common spatial pattern was used for optimal data shape. A spatial filter with common spatial patterns (CSP) is a subtype of a spatial filter. It is a supervised technique, as opposed to PCA, and therefore needs class label information for each every training sample. CSP optimises the variance-ratio of two classes; that is, CSP finds a transformation matrix that produces feature vectors with the greatest variance for the first class in the first few items and the greatest variance for the second class in the last few elements.

### **Machine Learning For Classification**

The classification phase is the last stage in the processing pipeline. A class label should be given to each feature vector produced by the feature extraction phase. There were many algorithms used throughout the study, such as linear discriminant analysis, support vector machines, and k-nearest-neighbors.

An exhaustive comparison of the different machine learning approaches is given in the results section of the paper.

### **Cross Validation**

It would be a methodological error to learn and test on the same data. An algorithm that just repeats the labels of previously observed training data would get a perfect score but would be unable to predict anything meaningful on previously unseen data. This is referred to as overfitting. Cross-validation is used to solve this issue. The data is divided into two sets: train, and test. The aim is to train the algorithm on the training set, then test its performance on the test set. Using this approach, no information from the test set is utilised in the design or optimization of the algorithm.

### **Linear Discriminant Analysis**

Linear discriminant analysis (LDA) is an extension of Fisher's linear discriminant. Its aim is to differentiate the means of two groups as much as feasible while minimising variance. This may be shown graphically by inserting a hyperplane into the n-dimensional feature space with the aim of separating the means of the point clusters of each class as far as feasible.

It assumes that the data is regularly distributed. LDA is a supervised technique for reducing dimensionality in classification tasks. Its output may be utilised to guide the input in the most discriminatory ways. Shrinkage may assist decrease the dimensionality of high-dimensional input data. LDA is one of the most widely utilised machine learning methods for BCIs based on motor imagery.

Using Linear Discriminant analysis on the data acquired, we were able to achieve an accuracy of 80%, 30% higher than that of chance for a two class motor imagery BCI system.

### **Other Algorithms**

Many additional machine learning techniques were employed in addition to LDA. One of them is the Support Vector Machine (SVM). SVM makes use of a hyperplane to optimise the minimum margin between two classes. Kernels may be used to modify the distribution of data and assist in dealing with a nonlinear feature space. All of these classifiers are better suited to various kinds of data, and a comparison will reveal which classifier is best suited to our feature space.

# **Results**

This section presents the results of previously improved feature extraction and classification methods applied to our own data. There were two kinds of motor images that needed to be distinguished. Our approach's classification accuracies are shown. There are many machine learning methods available for classification. In this part, we evaluate the performance of some of the most popular methods on all of the data from the contests to determine which approach best matches the data. As previously stated, the feature vectors are created using CSP, thus each classifier receives precisely the same input. Prior to categorization, the feature vectors were normalised.


<img width="1000" alt="Screen Shot 2021-08-27 at 12 08 47 AM" src="https://user-images.githubusercontent.com/68840767/131070423-3cf628dd-2817-49a2-bf71-c7803a3585ab.png">

