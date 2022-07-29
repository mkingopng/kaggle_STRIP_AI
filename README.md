# Kaggle_STRIP_AI

<img src="data/strip_AI.png"/>

mayo clinic: classify the blood clot origins in ischemic stroke

# Goal of the Competition
The goal of this competition is to classify the blood clot origins in ischemic stroke. Using whole slide digital 
pathology images, you'll build a model that differentiates between the two major acute ischemic stroke (AIS) etiology 
subtypes: cardiac and large artery atherosclerosis.

Your work will enable healthcare providers to better identify the origins of blood clots in deadly strokes, making it 
easier for physicians to prescribe the best post-stroke therapeutic management and reducing the likelihood of a second 
stroke.

# Context
Stroke remains the second-leading cause of death worldwide. Each year in the United States, over 700,000 individuals 
experience an ischemic stroke caused by a blood clot blocking an artery to the brain. A second stroke (23% of total 
events are recurrent) worsens the chances of the patient’s survival. However, subsequent strokes may be mitigated if 
physicians can determine stroke etiology, which influences the therapeutic management following stroke events.

During the last decade, mechanical thrombectomy has become the standard of care treatment for acute ischemic stroke 
from large vessel occlusion. As a result, retrieved clots became amenable to analysis. Healthcare professionals are 
currently attempting to apply deep learning-based methods to predict ischemic stroke etiology and clot origin. However, 
unique data formats, image file sizes, as well as the number of available pathology slides create challenges you could 
lend a hand in solving.

The Mayo Clinic is a nonprofit American academic medical center focused on integrated health care, education, and 
research. Stroke Thromboembolism Registry of Imaging and Pathology (STRIP) is a uniquely large multicenter project led 
by Mayo Clinic Neurovascular Lab with the aim of histopathologic characterization of thromboemboli of various 
etiologies and examining clot composition and its relation to mechanical thrombectomy revascularization.

To decrease the chances of subsequent strokes, the Mayo Clinic Neurovascular Research Laboratory encourages data 
scientists to improve artificial intelligence-based etiology classification so that physicians are better equipped to 
prescribe the correct treatment. New computational and artificial intelligence approaches could help save the lives of 
stroke survivors and help us better understand the world's second-leading cause of death.

# Evaluation
Submissions are evaluated using a weighted multi-class logarithmic loss. The overall effect is such that each class is 
roughly equally important for the final score.

Each image has been labeled with an etiology class, either CE or LAA. For each image, you must submit a probability for 
each class. The formula is then:

$\text{Log Loss} = - \Bigg( \dfrac{\sum_{i=1}^{M} w_i \cdot \sum_{j=1}^{N_i} \dfrac{y_{ij}}{N_i} \cdot \ln p_{ij}}{\sum_{i=1}^{M} w_i} \Bigg)$

<img src="data/metric.png"/>

where $N$ is the number of images in the class set, $M$ is the number of classes, $\ln$ is the natural logarithm, 
$Y_{ij}$ is 1 if observation $i$ belongs to class $j$ and 0 otherwise, $p_{ij}$ is the predicted probability that image 
$i$ belongs to class $j$.

The submitted probabilities for a given image are not required to sum to one because they are rescaled prior to being 
scored (each row is divided by the row sum). In order to avoid the extremes of the log function, each predicted 
probability $p$ is replaced with $\max(\min(p, 1 - 10^{-15}), 10^{-15}$.

