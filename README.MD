# Kaggle Titanic: Machine Learning from Disaster

This repository contains my solution for the Titanic challenge on Kaggle. The goal is to predict which passengers survived the shipwreck based on data such as age, gender, and class.

This was my first data science challenge on Kaggle.

## Variables Used

For model training, I used the following processed columns:

- Pclass: Passenger class.
- IsFemale: Binary variable indicating female gender.
- DeckLevel: Numerical representation based on passenger class (First Class = 3, Second Class = 2, Third Class = 1).
- FamilySize: Sum of 1 + Parch + SibSp.
- IsElderly: Binary variable for elderly passengers.
- IsKid: Binary variable for children.
- IsTeen: Binary variable for teenagers.

### Data Observations

- Redundancy in DeckLevel: I noticed that DeckLevel, as constructed, causes redundancy with the Pclass column, since it derives directly from the passenger class.
- DeckLevel Improvement: Extracting the deck level solely by class was simplified; a better approach could have been implemented.
- Gender Encoding: I did not include an IsMale column because it would be redundant given the presence of the IsFemale column.
- Age Encoding: Four encodings (Kid, Teen, Adult, Elderly) were not used. Since any passenger who is not a Kid, Teen, or Elderly is automatically an Adult, the fourth column was omitted to avoid redundancy.

## Feature Engineering

1. FamilySize: Calculated by the sum of family members on board (1 + Parch + SibSp).
2. Age Groups: Passengers were grouped into kid, teen, adult, and elderly.
3. Handling Missing Values: To fill missing ages, I used the titles present in the names (Mr, Miss, etc.) to attempt to categorize them into one of the groups.

## Challenges in Test Processing

While processing the test.csv file, I encountered the title "Ms", which was not accounted for in the original processing. To resolve this, I treated "Ms" as "Miss" and processed it identically to Notebook 1.

## Modeling and Results

For the final prediction, I used a voting ensemble approach combining three models:

- Logistic Regression
- KNN
- XGBoost

## Performance

- Final Score: 0.78229
- I believe this is a good score for my first data science challenge on Kaggle.
