# Baseball-MVP-Predictor

## Overview
Uses Machine Learning to predict the MVP of the current season. in both National and American leagues. Trained models using data created by [my very own web-scraper](https://github.com/jblackledge/MLBStatScraper). The data was obtained for every year that a hitter won the MVP, and included only player names, OPS, batting-average, RBI's, HR's, and of course whether or not that player was the MVP winner that year.

## Cleaning the data set
I chose to leave out years in which a pitcher has won the MVP because the dataset focuses only on hitting data, and I want to avoid "confusing" my model. Pitchers rarely win the MVP award (they typically only win the Cy Young), but when they do, it's because they had a phenomenal year pitching, and not because hitters had a poor year hitting. Meaning that if the pitcher only had an average year (not MVP caliber), then a hitter would have likely won. This means that hitting data in those years doesn't tell us anything about the type of hitting stats required to win the MVP, and would only cause problems with our model. 

## Decision Tree
My first choice in a model was a Decision Tree classification model. Because the MVP is chosen by humans, I wanted to start with a model that can closely mimic human decision-making. Using this model I was able to achieve a 93% prediction accuracy. With about a month left in the current season, it has not picked an MVP winner for either league.
![Decision Tree Image](/DecisionTree/mvp-predictor-decisiontree.png)

## Random Forest
I decided to go with a Random Forest model for my next attempt in order to see if we could improve upon the accuracy of the Decision Tree model. Random Forest seemed like a logical progression after starting with a Decision Tree. Using the Random Forest model on the same data, I was able to achieve a 96% prediction accuracy. Much like the Decision Tree, this model is also not currently picking any of the current league leaders to win the MVP.

## Logistic Regression
Branching out from the Decision Tree classification model, I decided to try a different classification model in that of Logistic Regression. I feel this model is the best choice of the three we've used so far, as our data's output is binary in nature, whereas a Decision Tree would be better suited if we had more options than "MVP"/"Not MVP". Additionally, I liked that it makes predictions by calculating the probability, since MVP voting isn't always about who had the best stats, a probability based decision seems like it would be as good as it gets. Using the Logistic Regression model on the same data, I was able to achieve an 80% prediction accuracy. While this model has a lower accuracy it is the only model of the three to actually make a predction.

For the NLMVP the model is currenlty picking Bryce Harper with a 52% probability, and Juan Soto at 58% probability. These two are great picks as they are currently leading in odds. For the ALMVP, the model is currently picking Vladimir Guerrero Jr at 66% probability, and Teoscar Hernandez at 50% probability. Vladimir Guerrero Jr. is probably a safe bet, but I'm not entirely certain why the model is choosing Teoscar. However, with the ALMVP, the model has a chance at being wrong on both accounts due to the likelihood of Shohei Ohtani winning. Shohei not only put up solid hitting numbers, but also had an All-Star caliber pitching season. Given that the model was not trained on any pitching data, it has no way of knowing just how deservant Ohtani is for the ALMVP, and has him at only a 41% probability. I will be updating this readme in November when the MVP's are announced so stay tuned to see if my model was able to make an accurate prediction! 

## November Update
NLMVP: Bryce Harper
ALMVP: Shohei Ohtani

The model correctly predicted Bryce Harper as the NLMVP winner. Though, he was slated at a lower percentage than Juan Soto, I'm still really happy with the results. The model of course incorecctly predicted Vlad Guerrero Jr. as the ALMVP, however as mentioned in the above section, this is only because of Shohei Ohtani's phenomenal season on both sides of the ball. Had Ohtani not pitched, Guerrero Jr. likely would have won, so this was not a bad pick by the model at all given the data it had. With this being said, I am going to leave out the ALMVP when updating the model using this season's stats, so as to avoid confusing it (like we talked about above in the cleaning section).

## Conclusion
I'm incredibly happy with the results from my first ever machine learning project! I learned so much about the process, and was able to create a usable model. Moving forward, I would probably like to adjust the way I collect stat data. In order to improve the model's ability to make predictions AND allow the model to make predictions regardless of the amount of a given stat, by using an "offset" approach for stat values. This would be accomplished by placing the leader of a given stat category at 0, and everyone behind the leader will have a value indicating how much behind they are. For example, if the leader has 102 RBI's, instead of placing 102 as their RBI value, place the value as 0, and then the next player back, say at 101 RBI's, would then get the value -1, and so on and so forth. This would allow the model to make daily predictions throughout the season, without worrying if the amount of the stat is "MVP-Worthy" or not.
