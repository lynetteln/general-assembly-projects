# Capstone Project: Emotion Classification
## 1. Problem Statement
In an increasingly digitalized world, there has been a decreasing focus on soft skills. In many aspects this is great, however in the aspect of Customer Service, dealing with unpleasant staff when ordering your morning coffee may not be the greatest way to start the day. It may not be the intention of the staff to be rude, however if we could use emotion recognition to detect the general satisfaction level of the customer, we can use this to train staff that directly interact with customers to improve the customer's experience. By understanding how customers feel based on their expressions, if we can identify the root source of dissatisfaction (whether it started from the interaction at the counter, or upon receiving their order, etc) companies can take measures to address the root causes of customer dissatisfaction. This way, despite the shift towards digitalizing every possible aspect of daily life, we can still preserve the element of human touch.

There are several measures of Customer Satisfaction. Some explicit examples would be using the Net Promoter Score or requesting for feedback in various ways such as via customer app surveys.

An implicit method that we intend to use to measure Customer Satisfaction is to use Facial Expression Recognition as a gauge of the customer's experience, specifically at cafes where there still exists interactions with customers. While this does not quantify the customer's total experience as it does not take into account separate factors such as the customer's sentiment towards the cafe's food and drinks, it can classify their expressions based on their interaction with the serving staff.

## 2. Executive Summary
For the scope of this project, we will be using 35,000 labelled images containing 7 different expressions from the FER2013 dataset from this [Kaggle Competition]( https://www.kaggle.com/c/challenges-in-representation-learning-facial-expression-recognition-challenge/data). The images are 48x48 pixel grayscale images of faces with pixel values ranging from 0-255

## 3. Exploratory Data Analysis
In this section, we will analyze the raw data for imbalanced class distributions, corrupt or duplicated data and make necessary adjustments. We also decided to implement a face cropping function using [OpenCVs](https://github.com/opencv/opencv) facial detection classifier in order to ensure we're trained specifically on facial features.

### 3.1 Data Cleaning
Upon inspection we discovered that the original dataset actually has a number of duplicated images and blank images. We have dropped these datapoints.

### 3.2 Merging Classes
Viewing the distributions of the raw fer2013 data set, we noticed an extremely skewed distribution in one of the classes, so we opted to merge **disgust** into **angry**.

![](https://i.ibb.co/t8RZxR8/raw-emotion-count.png)

## 4. Modelling
In this analysis, we will explore 3 different models:
1. Custom CNN model
2. Pretrained [VGG Model](https://github.com/rcmalli/keras-vggface) (Both base model as well as a fine-tuned model)
3. Pretrained [EfficientNet Model](https://github.com/qubvel/efficientnet) (Both base model as well as a fine-tuned model)

For the last two we will carry out the modelling in 2 steps:
1) The base model, which has all layers frozen (with the exception of the prediction layer, that is adjusted to match the number of classes in our problem)
2) The fine-tuned model, where we make use of transfer learning where we adjust some of the hyperparameters to adapt to our problem.

Weights will not be retrained in frozen layers. In unfrozen layers of the pretrained models, weights will be retrained, so we will only be making use of the existing topology in these layers.

### 4.1 Preprocessing
#### Custom CNN
The Custom CNN Model that we made takes in normalized (48,48,1) pixel map as its input. In otherwords, a 48 x 48 black and white image to match the fer2013 dataset

#### Pretrained VGG/EffNet
Pretrained models take in an image shape of (224,224,3) and the input data range is [0,255]. In otherwords, a 224 x 224 RGB image.

In order to make the dataset match with the model's expected input shape - we added fake RGB layers (that was the BW layer duplicated) and added a resizing layer before feeding it into the base models

### 4.2 Model Performance
| Model               | Test Accuracy | Train Loss | Unseen Data Accuracy |
|---------------------|---------------|------------|----------------------|
| Custom CNN          | 60.65%        | 1.0254     | 59.61%               |
| VGG Base            | 58.88%        | 1.0790     | N/A                  |
| VGG Model           | 63.81%        | 0.9800     | N/A                  |
| Efficient Net Base  | 54.52%        | 1.1996     | N/A                  |
| Efficient Net Model | 65.08%        | 0.9766     | 59.61%               |

### 4.3 Evaluation of Best Models on Unseen Data
In attempt to test our models on unseen data, we created a dataframe consisting of manually gathered and labelled image URLs and labels.
However, since this does not come from the same dataset as our train and test images, the images are not in the same size and format and thus are required to go through some preprocessing before carrying out the predictions.
The processing comes in two steps - A function to crop faces, and a processing function that takes the image URL and returns a format that will be used in the crop

In terms of unseen data, both our custom CNN and the EfficientNetB0 have the same number of True and False predictions. We checked both dataframes to make sure that both models weren't predicting the exact same images incorrectly. Performance wise, both performed slightly worse than on our test set.

### 4.4 Misclassification analysis on EfficientNetB0
![](https://i.ibb.co/j6kdSfW/misclassification-analysis.png)

The top 3 misclassified emotions were Fear, Sad and Neutral, with Angry being a close 4th.

Based on our the above images and barplots here are the key takeaways.
- Fear was mostly misclassified as Sad and Angry
- Sad was mostly misclassified as Angry and Neutral
- Neutral was mostly misclassified as Sad and Angry
- Anger was mostly misclassified as Sad and Neutral

We also see this in the confusion plot below that helps us to visualize the Actual vs Predicted emotions. Happy and Surprise had the highest values (deepest colours), and this tells us that the two classes were the best predicted.

In further analysis, the four most misclassified images seem to be misclassified as each other. If we look at the photos, the misclassification seems to be somewhat reasonable as some of these emotions are difficult to tell apart even to human perception.

![](https://i.ibb.co/BCphHYp/classification-confusion-matrix.png)

### 4.5 Sample EffNet Misclassified Umages

![](https://i.ibb.co/GxPcJVQ/misclassified-sample.png)
![](https://i.ibb.co/fdLGhrm/misclassified-fear.png)
![](https://i.ibb.co/qrfQTR5/misclassified-happy.png)
![](https://i.ibb.co/WBmVd32/misclassified-sad.png)
![](https://i.ibb.co/Lr5LqCZ/misclassified-suprise.png)
![](https://i.ibb.co/7v5X5L5/misclassified-neutral.png)

## 5. Conclusions
The accuracy of our two best models are considered average, considering that the top kaggle score for classification with the same dataset (albeit with 7 classes) was 71%. However, given that our custom-made CNN model which was of low complexity had an accuracy score close to that of the pre-trained model, there is room for improvement on the pre-trained EfficientNetB0 model.

Fortunately, tying back to our problem statement of whether or not a customer is satisfied, we should be able to group the classes and separate them into either "Satisfied" or "Dissatisfied", if we find a way correctly classify Neutral expressions. Aside from Neutral, the top 4 misclassified classes are generally considered to show dissatisfactory expressions, while the top 2 correctly classified classes would represent satisfactory expressions.

## 6. Recommendations
1. Models in the scope of this project did not include the use of model tuners such as KerasTuners. Using KerasTuners would help us to better select hyperparameters for our model, and in turn give us better results.
2. Images in our dataset were quite consistent, apart from some that showed watermarks and plain text. It is impossible to visually run through every single image to eliminate "dirty data" such as this. However, images provided to us were 48x48, which is extremely small. When we think about a model generalizing to "new" data in the aspect of our problem, CCTV image resolutions in this day and age are quite high, so training on a 48x48 dataset is unlikely to produce good accuracy. In this aspect Image Augmentation did not prove to be very effective since our images were already quite consistent.
3. More pre-trained models should be explored. In our project, we only used VGG and EfficientNetB0 (ResNet as well, but this was not included due to bad results). However there are many other pre-trained models that were built for facial recognition, and thus would be good to explore on and build on other models as well.
