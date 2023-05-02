![cover](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/cover.jpeg)

# SyriaTel Customer Churn Classification

**Author**: [Heath Rittler](mailto:hrittler@gmail.com)


## Overview

https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset

SyriaTel, a telecommunications company wants to identify the leading factors of why a customer cancels their service.  This is also referred to as 'Churn.'  If they understand the factors that lead to churn, the company can implement programs to reduce the risk of churn, and increase the lifetime value of and for their customers.

My goal is to build a classifer to predict whether a customer will stop doing business with SyriaTel.  I will be using information such as usage, interactions with SyriaTel, and certain features that the customer has purchased.  I am mostly focused on reducing the rate of false negatives so the metric in which I will be evaluating my models is called Recall.  With that being said, we will also keep a close eye on the F1 score, which looks at the harmonic mean between Recall and Precision.  We will keep a close eye here because even though we aren't as concerned about false positives, we want to limit false positives as much as we can, without sacrificing our Recall.


## Business Problem

Acquring a new customer on average costs 3x that of retaining an existing customer.  At Skyvia, they are trying to optimize their retetention strategies, and do to so they are trying to understand what features of different customers indicate churn.  The presentation will be made availble for the VP of Customer Success, and the Chief Revenue Officer.

Within this dataset, 85% of the customers were retained, leading to approximately 15% churn.  This is pretty high compared to other industry standards for tech based companies, typically expericing churn within the 3-8% range.


## Data

This project uses the SyriaTel Kaggle dataset, which can be found in `data.csv` in the data folder in this repository. The dataset includes 3,333 entries, and 21 columns.  Here are the columns in the dataset including our target variable, churn:

* `state`- The state in which the account owner resides.
* `account length` - 
* `area code` - Primary 3 digit area of the line for the account.
* `phone number` - Primary 7 digit area of the line for the account.
* `international plan` - Indicator denoting whether or not the account has an international feature.
* `voice mail plan` - Indicator denoting whether or not the account has an voice mail feature.
* `number vmail messages` - Usage metric counting the total number of voicemails for the phone number in question.
* `total day minutes` - Usage metric indicating how many minutes (call time) were used between 6:00am and 5:00pm.
* `total day calls` - Usage metric indicating how many calls were used between 6:00am and 5:00pm. 
* `total day charge` - Usage metric indicating how much the user was charged for their usage between 6:00am and 5:00pm.
* `total eve minutes` - Usage metric indicating how many minutes (call time) were used between 5:01pm and 8:00pm.
* `total eve calls` - Usage metric indicating how many calls were used between 5:01pm and 8:00pm. 
* `total eve charge` - Usage metric indicating how much the user was charged for their usage between 5:01pm and 8:00pm.
* `total night minutes` - Usage metric indicating how many minutes (call time) were used between 8:01pm and 5:59am.
* `total night calls` - Usage metric indicating how many calls were used between 8:01pm and 5:59am.
* `total night charge` - Usage metric indicating how much the user was charged for their usage between 8:01pm and 5:59a.
* `total intl minutes` - Usage metric indicating how many minutes (call time) were used internationally.
* `total intl calls` - Usage metric indicating how many calls were made internationally.
* `total intl charge` - Usage metric indicating how much the user was charged for their international call usage.
* `customer service calls` - The total number of customer service calls made by the user to the Skyvia Customer Service line.
* `churn` - Our target category indicating whether or not the customer churned/ cancelled their plan.

Additional information about the dataset can be found here: https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset

Additional information about this dataset can be found on the [Kaggle Dataset](https://www.kaggle.com/datasets/becksddf/churn-in-telecoms-dataset) website. 


## Methods

After our exploratory analysis, we looked at different classfication models to see if we could accurately predict churn within our data.  We trained our model on 80% of the dataset, while saving the remaining 20% to test our assumptions in what our algorithms learned.  We leveraged a Logistic Regression model, and tuned the regression's hyperparameters to arrive at our baseline model.  

That model was then iterated on, leveraging multiple models such as Decision Tree, Random Forest, Ridge, and XGBoost to evaluate the best model.  Each approach was modeled with and without tuned hyperparameters.  We chose our XGBoost model, which performed the best from a Recall perspective, and from an F1 perspective.  We did consider the second meric for evaluation so we didn't include too many false positives in our predictions.

For our final model, we were able to predict positive churn cases 82% of the time.

![final_confusion](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/final_confusion.png)

The top 3 features that lead to churn are customers that have the international plan, folks that engage with customer service frequently, and those with the voice mail plan.  Those that are engaging with customer service already, most likely have some other questions or concern about the value that the features/ service are providing.  These would be good indicators of risk, and information to understand what issues customers are experiencing.  

Having customer service calls on this list, actually will make it easier to identify risk within the customer base.  Thus making the outbound efforts to engage with customers with the international plan and the voice mail plan that aren't engaging frequently with customer service.

![feature_importance](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/feature_importance.png)


## Results

Customers that had the internation plan feature on their plan churned at a higher rate than those without the international plan feature.  Customers that have the international plan feature churn at a rate near 40% vs those without the feature at 11%.  Understanding why this feature is causing so much dissatisfaction will be an important task for the company to understand. 

![international_plan_churn](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/international_plan_churn.png)

The second most important feature in our data set was customers that were contacting customer service multiple times.  This could be service related, or it could be related to general questions, however once a customer reaches 4 customer service calls, the churn rate goes up significantly.  Churn rate jumps close to 45% once a customer reaches 4 customer service calls.

![churn_cs_calls](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/churn_cs_calls.png)

As the product is used, charges are increasing.  What we really want to investigate though is if the price per minute is going down, as the the total minutes go up.  If there was a strategic pricing, I think we would want to see the price per minute go down, but the charges stay flat because of the increase in minutes used.  I think we would actually want to see a negative slope here indicating that the customers that use the product the most, would be getting a slight discount on pricing as usage increases.  Looking at different pricing mechanisms and strategies may also help with customer sentiment and experience, impacting overall churn.

![price_per_minute](https://github.com/heathlikethecandybar/phase_3_project/blob/main/phase_3/project/images/price_per_minute.png)


## Conclusions & Recommendations

In conclusion, we were able to create a model that will accurate predict customers that are at risk of churn.  By leveraging that model, and some of the strategies listed below, SyriaTel will be able to mitigate their churn, and increase the Lifetime Value of their customers.  In summary those strategies are:

- **Customers that have the international plan and the voice mail plan should be surveyed to understand product performance and value.  Although the voice mail plan performances better when paired with the international plan, it should be noted still that no international plan, and no voice mail plan performs the worst of the possible feature combinations (with those products).** 

- **Once a customer reaches 3 customer service calls, flag the account as at risk.  Once the account reaches 4 calls, the probability of canceling goes from 10% to 45%.**

- **Scale pricing to offer some relief for customers that use the plan more often.  The pricing scale doesn't incentivize more usage of the product.  Another option would be to look at unlimited usage based pricing, to give customers that use the plan more, the relief knowing that if they use the plan more, they won't necessarily be charged more for that usage.** 


## Moving Forward

Further analyses in these areas could yield additional insights:

- **Look at additional features such as location, or splitting out usage between low, moderate, and high usage**
- **Include other sources of information such as Salesforce to look at additional account attributes to help with prediction, and strategies to mitigate risk.**
- **Refresh the analysis regularly with new data to understand how the market is evolving over time.**


## For More Information

The full analysis is located in the [Jupyter Notebook](./phase_3_notebook.ipynb) or review this summary [presentation](./phase_3_presentation.pdf).

For additional info, contact Heath Rittler at [hrittler@gmail.com](mailto:hrittler@gmail.com)


## Repository Structure

```
├── data
├── images
├── README.md
├── phase_3_presentation.pdf
├── phase_3_notebook.pdf
└── phase_3_notebook.ipynb
```


cover photo credit:  OpenAI labs - Dall-E created on 12/31/2022