### Problem Statement
#### To help you practice strategies for machine learning, in this week we’ll present another scenario and ask how you would act. We think this “simulator” of working in a machine learning project will give a task of what leading a machine learning project could be like!

#### You are employed by a startup building self-driving cars. You are in charge of detecting road signs (stop sign, pedestrian crossing sign, construction ahead sign) and traffic signals (red and green lights) in images. The goal is to recognize which of these objects appear in each image. As an example, the above image contains a pedestrian crossing sign and red traffic lights
<div align=center><img src="https://github.com/Kiiiiii123/Coursera-DL-AndrewNg/blob/master/imgs/self-driving%20cars.png"/></div>

#### Your 100,000 labeled images are taken using the front-facing camera of your car. This is also the distribution of data you care most about doing well on. You think you might be able to get a much larger dataset off the internet, that could be helpful for training even if the distribution of internet data is not the same.

#### 1.You are just getting started on this project. What is the first thing you do? Assume each of the steps below would take about an equal amount of time (a few days).
Spend a few days training a basic model and see what mistakes it makes.
#### 2.Your goal is to detect road signs (stop sign, pedestrian crossing sign, construction ahead sign) and traffic signals (red and green lights) in images. The goal is to recognize which of these objects appear in each image. You plan to use a deep neural network with ReLU units in the hidden layers.
#### For the output layer, a softmax activation would be a good choice for the output layer because this is a multi-task learning problem. True/False?
Fales
#### 3.You are carrying out error analysis and counting up what errors the algorithm makes. Which of these datasets do you think you should manually go through and carefully examine, one image at a time?
500 images on which the algorithm made a mistake
#### 4.After working on the data for several weeks, your team ends up with the following data:
- 100,000 labeled images taken using the front-facing camera of your car.
- 900,000 labeled images of roads downloaded from the internet.
- Each image’s labels precisely indicate the presence of any specific road signs and traffic signals or combinations of them. For example,y(i)=[1 0 0 1 0] means the image contains a stop sign and a red traffic light.
#### Because this is a multi-task learning problem, you need to have all your y(i) vectors fully labeled.If one example is equal to [0 ? 1 1 ?] then the learning algorithm will not be able to use that example. True/False?
False
#### 5.The distribution of data you care about contains images from your car’s front-facing camera; which comes from a different distribution than the images you were able to find and download off the internet. How should you split the dataset into train/dev/test sets?
Choose the training set to be the 900,000 images from the internet along with 80,000 images from your car’s front-facing camera. The 20,000 remaining images will be split equally in dev and test sets.
#### 6.Assume you’ve finally chosen the following split between of the data:
|Dataset:|Contains:|Error of the algorithm:|
|:-:|:-:|:-:|
|Training|940,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)|8.8%|
|Training-Dev|20,000 images randomly picked from (900,000 internet images + 60,000 car’s front-facing camera images)|9.1%|
|Dev|20,000 images from your car’s front-facing camera|14.3%|
|Test|20,000 images from the car’s front-facing camera|14.8%|

























- y = 0: There is no bird on the image
- y = 1: There is a bird on the image
#### Your goal is to build an algorithm able to classify new images taken by security cameras from Peacetopia.
#### There are a lot of decisions to make:
- What is the evaluation metric?
- How do you structure your data into train/dev/test sets?
### Matric of success
#### The City Council tells you that they want an algorithm that
1.Has high accuracy.

2.Runs quickly and takes only a short time to classify a new image.

3.Can fit in a small amount of memory, so that it can run in a small processor that the city will attach to many different security cameras.

#### 1.Note: Having three evaluation metrics makes it harder for you to quickly choose between two different algorithms, and will slow down the speed with which your team can iterate. True/False?
True
#### 2.After further discussions, the city narrows down its criteria to:
- "We need an algorithm that can let us know a bird is flying over Peacetopia as accurately as possible."
- "We want the trained model to take no more than 10sec to classify a new image.”
- “We want the model to fit in 10MB of memory.”
#### If you had the three following models, which one would you choose?
|Test Accuracy|Runtime|Memory Size|
|:-:|:-:|:-:|
|98%|9 sec|9Mb|
#### 3.Based on the city’s requests, which of the following would you say is true?
Accuracy is an optimizing metric; running time and memory size are a satisficing metrics.
### Structuring your data
#### 4.Before implementing your algorithm, you need to split your data into train/dev/test sets. Which of these do you think is the best choice?
|Train|Dev|Test|
|:-:|:-:|:-:|
|9,500,000|250,000|250,000|
#### 5.After setting up your train/dev/test sets, the City Council comes across another 1,000,000 images, called the “citizens’ data”. Apparently the citizens of Peacetopia are so scared of birds that they volunteered to take pictures of the sky and label them, thus contributing these additional 1,000,000 images. These images are different from the distribution of images the City Council had originally given you, but you think it could help your algorithm.
#### You should not add the citizens’ data to the training set, because this will cause the training and dev/test set distributions to become different, thus hurting dev and test set performance. True/False?
False
#### 6.One member of the City Council knows a little about machine learning, and thinks you should add the 1,000,000 citizens’ data images to the test set. You object because:
- The test set no longer reflects the distribution of data (security cameras) you most care about.
- This would cause the dev and test set distributions to become different. This is a bad idea because you’re not aiming where you want to hit.
#### 7.You train a system, and its errors are as follows (error = 100%-Accuracy):
|Training set error|Dev set error|
|:-:|:-:|
|4.0%|4.5%|
#### This suggests that one good avenue for improving performance is to train a bigger network so as to drive down the 4.0% training error. Do you agree?
No, because there is insufficient information to tell.
#### 8.You ask a few people to label the dataset so as to find out what is human-level performance. You find the following levels of accuracy:
|Bird watching expert#1|Bird watching expert#2|Normal person #1 (not a bird watching expert)|Normal person #2 (not a bird watching expert)|
|:-:|:-:|:-:|:-:|
|0.3%error|0.5%error|1.0%error|1.2%error|
#### If your goal is to have “human-level performance” be a proxy (or estimate) for Bayes error, how would you define “human-level performance”?
0.3% (accuracy of expert #1)
#### 9.Which of the following statements do you agree with?
- A learning algorithm’s performance can be better than human-level performance but it can never be better than Bayes error.
#### 10.You find that a team of ornithologists debating and discussing an image gets an even better 0.1% performance, so you define that as “human-level performance.” After working further on your algorithm, you end up with the following:
|Human-level performance|Training set error|Dev set error|
|:-:|:-:|:-:|
|0.1%|2.0%|2.1%|
#### Based on the evidence you have, which two of the following four options seem the most promising to try? (Check two options.)
- Try decreasing regularization.
- Train a bigger model to try to do better on the training set.
#### 11.You also evaluate your model on the test set, and find the following:
|Human-level performance|Training set error|Dev set error|Test set error|
|:-:|:-:|:-:|:-:|
|0.1%|2.0%|2.1%|7.0%|
#### What does this mean? (Check the two best options.)
- You have overfit to the dev set.
- You should try to get a bigger dev set.
#### 12.After working on this project for a year, you finally achieve:
|Human-level performance|Training set error|Dev set error|
|:-:|:-:|:-:|
|0.10%|0.05%|0.05%|
#### What can you conclude? (Check all that apply.)
- It is now harder to measure avoidable bias, thus progress will be slower going forward.
- If the test set is big enough for the 0.05% error estimate to be accurate, this implies Bayes error is ≤0.05
#### 13.It turns out Peacetopia has hired one of your competitors to build a system as well. Your system and your competitor both deliver systems with about the same running time and memory size. However, your system has higher accuracy! However, when Peacetopia tries out your and your competitor’s systems, they conclude they actually like your competitor’s system better, because even though you have higher overall accuracy, you have more false negatives (failing to raise an alarm when a bird is in the air). What should you do?
Rethink the appropriate metric for this task, and ask your team to tune to the new metric.
#### 14.You’ve handily beaten your competitor, and your system is now deployed in Peacetopia and is protecting the citizens from birds! But over the last few months, a new species of bird has been slowly migrating into the area, so the performance of your system slowly degrades because your data is being tested on a new type of data.
<div align=center><img src="https://github.com/Kiiiiii123/Coursera-DL-AndrewNg/blob/master/imgs/Birds.jpg"width="400"height="300"/></div>

#### You have only 1,000 images of the new species of bird. The city expects a better system from you within the next 3 months. Which of these should you do first?
Use the data you have to define a new evaluation metric (using a new dev/test set) taking into account the new species, and use that to drive further progress for your team.
#### 15.The City Council thinks that having more Cats in the city would help scare off birds. They are so happy with your work on the Bird detector that they also hire you to build a Cat detector. (Wow Cat detectors are just incredibly useful aren’t they.) Because of years of working on Cat detectors, you have such a huge dataset of 100,000,000 cat images that training on this data takes about two weeks. Which of the statements do you agree with? (Check all that agree.)
- Needing two weeks to train will limit the speed at which you can iterate.
- If 100,000,000 examples is enough to build a good enough Cat detector, you might be better of training with just 10,000,000 examples to gain a \approx≈10x improvement in how quickly you can run experiments, even if each model performs a bit worse because it’s trained on less data.
- Buying faster computers could speed up your teams’ iteration speed and thus your team’s productivity.
