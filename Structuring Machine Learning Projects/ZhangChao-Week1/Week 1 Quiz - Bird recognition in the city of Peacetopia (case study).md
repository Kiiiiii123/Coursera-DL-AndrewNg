### Problem Statement
#### This example is adapted from a real production application, but with details disguised to protect confidentiality.
<div align=center><img src="https://github.com/Kiiiiii123/Coursera-DL-AndrewNg/blob/master/imgs/Alcazar.jpg"width="500"height="400"/></div>

#### You are a famous researcher in the City of Peacetopia. The people of Peacetopia have a common characteristic: they are afraid of birds. To save them, you have to build an algorithm that will detect any bird flying over Peacetopia and alert the population.

#### The City Council gives you a dataset of 10,000,000 images of the sky above Peacetopia, taken from the city’s security cameras. They are labelled:
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
<div align=center><img src="https://github.com/Kiiiiii123/Coursera-DL-AndrewNg/blob/master/imgs/Alcazar.jpg"width="400"height="300"/></div>

#### You have only 1,000 images of the new species of bird. The city expects a better system from you within the next 3 months. Which of these should you do first?
