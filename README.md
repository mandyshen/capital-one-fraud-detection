# capital-one-fraud-detection

I decided to take a crack at the Capital One data science challenge on github https://github.com/CapitalOneRecruiting/DS.

## Dataset Balance
The data is very imbalanced. Less than 1.5% of the data is fraud, so it's very under-represented. Rather than oversampling, I decided to optimize the probability threshold for my models. 

## Testing Performance 
What I should prioritize is reducing false negatives and increasing true positives. For credit card fraud, misclassifying a fraudulent charge could be very bad for the customer and provider. This will create more noise in the form of false positives, but that's less dire. Having said that, it's ultimately a business decision. There will be a certain amount of false positives that the business won't tolerate because the customer will eventually become inundated with false fraud emails. I decided to optimize with ROC+AUC in my grid searches. Then I used the average precision (AP) to set my threshold.

## Features
I tried to use common sense as to what would lead to fraud. Since this is my first foray into a topic like this, I tried to keep the feature engineering simple. However, after testing some of my models, I went back and added about 5 more features. It improved my model a little. The feature engineering is certainly where I could most improve this project.There is no location data other than country code. I think if there was something like “merchant zip code”, it would have greatly improved my models.

## Models
I tested more than 3 models initially, but tightened my scope. Some took way too long to train on my computer when doing grid search (SVM). 
I decided to stick with Logistic Regression, Random Forest, and Gradient Boost. I still had to cut back on the hyper-parameters for them to run in a reasonable time.

## Which Model is best?
Modifying the threshold greatly improved the results. Naturally there is more noise, but there are more true positives (tp) and less false negatives (fn).

In trying to improve tp and reduce fn, the Gradient Boost did best, but the Logistic Regression Model wasn't much worse. 

## Model performance
As I mentioned above, the features could definitely be improved. Below is the confusion matrix from my Gradient Boost model on the test set, and the feature importance.
The results aren't great, but this was certainly a good learning experience. 

![alt text](https://github.com/calvinscottforbes/capital-one-fraud-detection/gb_confusion_matrix.jpg?raw=true)

![alt text](https://github.com/calvinscottforbes/capital-one-fraud-detection/tree/main/gb_feature_importance.jpg?raw=true)

