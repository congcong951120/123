# Machine Learning Engineer Nanodegree
## Introduction and Foundations
## Project: Titanic Survival Exploration
In 1912, the ship RMS Titanic struck an iceberg on its maiden voyage and sank, resulting in the deaths of most of its passengers and crew. In this introductory project, we will explore a subset of the RMS Titanic passenger manifest to determine which features best predict whether someone survived or did not survive. To complete this project, you will need to implement several conditional predictions and answer the questions below. Your project submission will be evaluated based on the completion of the code and your responses to the questions.
## Data collection and processing
### Data collection
To begin working with the RMS Titanic passenger data, we'll first need to import the functionality we need, and load our data into a pandas DataFrame.From a sample of the RMS Titanic data, we can see the various features present for each passenger on the ship:

•Survived: Outcome of survival (0 = No; 1 = Yes)

•Pclass: Socio-economic class (1 = Upper class; 2 = Middle class; 3 = Lower class)

•Name: Name of passenger

•Sex: Sex of the passenger

•Age: Age of the passenger (Some entries contain NaN)

•SibSp: Number of siblings and spouses of the passenger aboard

•Parch: Number of parents and children of the passenger aboard

•Ticket: Ticket number of the passenger

•Fare: Fare paid by the passenger

•Cabin Cabin number of the passenger (Some entries contain NaN)

•Embarked: Port of embarkation of the passenger (C = Cherbourg; Q = Queenstown; S = Southampton)

### Data preprocessing
Since we're interested in the outcome of survival for each passenger or crew member, we can remove the Survived feature from this dataset and store it as its own separate variable outcomes. We will use these outcomes as our prediction targets.
## Making Predictions
If we were asked to make a prediction about any passenger aboard the RMS Titanic whom we knew nothing about, then the best prediction we could make would be that they did not survive. This is because we can assume that a majority of the passengers (more than 50%) did not survive the ship sinking.

1.Assuming they all survive, how accurate will our predictions be?
The prediction accuracy was 60.00%.

2.Assuming they were all killed, how accurate would we be?
The accuracy of the prediction is 61.62%.

3.According to the surviving data, most women survived the shipwreck. If a passenger is a female, she is predicted to survive; otherwise, she is killed. What is the accuracy of the prediction? .
The accuracy of the prediction is 78.68%.

Using just the Sex feature for each passenger, we are able to increase the accuracy of our predictions by a significant margin. Now, let's consider using an additional feature to see if we can further improve our predictions. For example, consider all of the male passengers aboard the RMS Titanic: Can we find a subset of those passengers that had a higher rate of survival? Let's start by looking at the Age of each male, by again using the survival_stats function. This time, we'll use a fourth parameter to filter out the data so that only passengers with the Sex 'male' will be included.

4.How accurate would a prediction be that all female passengers and all male passengers younger than 10 survived? 
Predictions have an accuracy of 79.35%.

5.Add constraints and make predictions
Make predictions if passenger is female and younger than 10 years; survival

If the passenger is between 10 and 20 years old, Parch = 2, SibSp <3, make predictions; survive

If the passenger is older than 20 years old and younger than 40 years old, is in the upper class, Parch = 0, make a prediction; survive

If the passenger is younger than 40 and is in the upper class, Parch = 1, SibSp = 1, make a prediction; survive

If the passenger is between the ages of 40 and 50 and is in the upper class, Parch = 0, SibSp = 1, make a prediction; survive
Other predictions, killed

Predictions have an accuracy of 80.13%

### Analysis

In this forecast, we first analyzed the data to find that age, gender, class, and number of spouses, children, and brothers are important factors for survival, so we conducted an in-depth analysis to find the important factors that affect the survival rate:

1.Passengers younger than 10 survive.

2.Female passengers in 1st and 2nd class survive first. Females in 3rd class have a higher survival rate when the number of relatives is 0.

3.Survival rates for passengers aged 20 to 45 are higher
By analyzing the characteristics of the data, step-by-step debugging improves the prediction accuracy rate to 80.13%.
## Conclusion
Through the study of this case, the principle of the decision number prediction method was mastered. It divides the data into smaller and smaller groups according to a feature, and each time a subset of the data is separated out, if the similarity between the new subsets after segmentation is higher than before (including approximate labels) , Our prediction is more accurate.
Thanks Peter for telling us about the course of machine language learning, and also for sharing many learning platforms, which will be more helpful to my future learning.