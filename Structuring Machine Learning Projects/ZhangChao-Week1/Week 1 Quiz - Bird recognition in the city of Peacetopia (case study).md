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
|：--------|--------：|：----：|
|98%|9 sec|9Mb|
