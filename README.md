# MLB-MVP-Prediction

## Overview
Uses Machine Learning to predict the MVP of the current season. in both National and American leagues. Trained models using data created by [my very own web-scraper](https://github.com/jblackledge/MLBStatScraper). The data was obtained for every year that a hitter won the MVP, and included only player names, ops, batting-average, RBI's, HR's, and of course whether or not that player was the MVP winner that year.

## Cleaning the data set
I chose to exclude years that a pitcher won the MVP, because this would likely "confuse" the model. Reason being, it is rare for a pitcher to win the MVP award, they typically only win the Cy Young award. Thus when a pitcher wins the MVP, it's because they had a phenomenal season, and not because hitters were having a poor season. Had the same pitcher had only an okay season, a hitter would likely win. Meaning that hitting data of those years is essentially meaningless.

## Decision Tree
My first choice in a model was a Decision Tree. Because the MVP is chosen by humans, I wanted to started with a model that can closely mimic human decision-making. Using this model I was able to achieve a 92% prediction accuracy. With about a month left in the current season, it has not picked an ALMVP winner, however the model has already chosen Bryce Harper to win the NLMVP (as of 09-05-2021).

![Decision Tree Image](/DecisionTree/mvp_predictor_decisiontree_image.png)
