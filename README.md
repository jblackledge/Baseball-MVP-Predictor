# Baseball-MVP-Predictor

## Overview
Uses Machine Learning to predict the MVP of the current season. in both National and American leagues. Trained models using data created by [my very own web-scraper](https://github.com/jblackledge/MLBStatScraper). The data was obtained for every year that a hitter won the MVP, and included only player names, ops, batting-average, RBI's, HR's, and of course whether or not that player was the MVP winner that year.

## Cleaning the data set
I chose to leave out years in which a pitcher has won the MVP because the dataset focuses only on hitting data, and I want to avoid "confusing" my model. Pitchers rarely win the MVP award (they typically only win the Cy Young), but when they do, it's because they had a phenomenal year pitching, and not because hitters had a poor year hitting. Meaning that if the pitcher only had an average year (not MVP caliber), then a hitter would have likely won. This means that hitting data in those years doesn't tell us anything about the type of hitting stats required to win the MVP, and would only cause problems with our model. 

## Decision Tree
My first choice in a model was a Decision Tree. Because the MVP is chosen by humans, I wanted to start with a model that can closely mimic human decision-making. Using this model I was able to achieve a 92% prediction accuracy. With about a month left in the current season, it has not picked an ALMVP winner, however the model has already chosen Bryce Harper to win the NLMVP (as of 09-05-2021). I will be re-checking the model's predictions with updated stats once we get closer to the end of the season.

![Decision Tree Image](/DecisionTree/mvp_predictor_decisiontree_image.png)
