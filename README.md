# Jointly-trained-Autoencoder-and-MLP-for-Autism-Classification-


Jointly training an autoencoder and a MLP on the time-series extracted from from the correlation
 matrix computed on the ABIDE-1 fMRI data in [Pytorch](https://pytorch.org/).

 



## Dataset

Resting-state functional magnetic resonance imaging (fMRI) data is obtained
from [Autism Brain Imaging Exchange (ABIDE-1)](https://fcon_1000.projects.nitrc.org/indi/abide/). 

## Prepocessing steps:
__Derivative__: rois_cc200 (Timeseries extracted from Cameron Craddock's 200 ROI parcellation atlas)
__Pipeline__ : Configurable Pipeline for the Analysis of Connectomes(CPAC).   
__Strategy__ : filt_global (band-pass filtering and global signal regression)


## Processing 
Pearson’s correlation matrix is computed on the CC-200 timeseries. In CC-200 atlas,
the brain is parcellated into m = 200 regions. 
Its a symmetric matrix, hence we only consider the upper-triangle and there are 
m × (m − 1)/2 = 19, 900 distinct pairwise Pearson’s correlations.


## Model
We feed the time-series into an autoencoder to extract discriminant features from the 
available feature set. The bottleneck layer of the autoencoder is fed to a MLP. The 
autoencoder is jointly trained with a multi-layer perceptron. We minimize both the 
reconstruction loss as well as the CrossEntropyLoss.


## Performance 

Training over 10-fold cross-validation, the model achieved : 
Accuracy = 87.2, Precision = 86.32, Recall = 87.3
## Environment Variables

### Hardware requirements
A server containing CUDA enabled GPU with compute capability 3.5 or above.


### Software requirements

`Pytorch version 0.4.1`   

`CUDA version 8+`  

`Python version 3.5+` 
