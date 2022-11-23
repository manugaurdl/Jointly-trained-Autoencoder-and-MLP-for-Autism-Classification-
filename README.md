# Jointly-trained-Autoencoder-and-MLP-for-Autism-Classification-
An autoencoder and a MLP is jointly trained on the time-series extracted from from the correlation matrix computed on the ABIDE-1 fMRI data. 

#Dataset

Resting-state functional magnetic resonance imaging (fMRI) data is obtained from Autism Brain Imaging Exchange (ABIDE-1). 
Prepocessing steps:
Derivative : rois_cc200 (Timeseries extracted from Cameron Craddock's 200 ROI parcellation atlas)
Pipeline : Configurable Pipeline for the Analysis of Connectomes(CPAC).
Strategy : filt_global (band-pass filtering and global signal regression)

Processing : 

Pearson’s correlation matrix is computed on the CC-200 timeseries. In CC-200 atlas,the brain is parcellated into m = 200 regions. Its a symmetric matrix, hence we only consider the upper-triangle and there are m × (m − 1)/2 = 19, 900 distinct pairwise Pearson’s correlations.

Model : 

We feed the time-series into an autoencoder to extract discriminant features from the available feature set. The bottleneck layer of the autoencoder is fed to a MLP. The autoencoder is jointly trained with a multi-layer perceptron. We minimize both the reconstruction loss as well as the CrossEntropyLoss.

#Performance over 10-fold cross-validation : 
Accuracy = 87.2, Precision = 86.32, Recall = 87.3  
