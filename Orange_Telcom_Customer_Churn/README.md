<a href= "https://www.kaggle.com/mnassrib/telecom-churn-datasets">Orange Telecom Churn Dataset (Link to dataset)</a>

## Objective
To predict if a customer will churn from Orange Telcom company<br>
<b>Evaluation Metric</b>: F1 Score

## Variable Definitions
<ul>
    <li>State: State customer is located</li>
    <li>Account length: Customer account length in days</li>
    <li>Area code: Area code of customer's location</li>
    <li>Phone number: Customer Phonenumber</li>
    <li>International plan: Does customer have International plan (Yes or No)</li>
    <li>Voicemail plan: Customer has voice mail plan (Yes or No)</li>
    <li>Number vmail messages: Customer number of voice mail messages</li>
    <li>Total day minutes: Total Call time in the daytime</li>
    <li>Total day calls: Total calls in daytime</li>
    <li>Total day charge: Total charges for calls in daytime</li>
    <li>Total eve minutes: Total Call time in the evening </li>
    <li>Total eve calls: Total calls in the evening</li>
    <li>Total eve charge: Total charges for calls in the evening</li>
    <li>Total night minutes: Total Call time at night</li>
    <li>Total night calls: Total calls at night</li>
    <li>Total night charge: Total charges for calls at night</li>
    <li>Total intl minutes: Total intl call time</li>
    <li>Total intl calls: Total Intl calls</li>
    <li>Total intl charge: Total Intl call charges</li>
    <li>Customer service calls: Customer customer service calls</li>
    <li>Churn: Target- Whether customer churned or not(True or False)</li>
    </ul>

### Approach
In the baseline notebook, the original features (and an interaction of customers with both International and voicemail plans) were used for modelling. Three different models were used- a linear (Logistic regression) and tree models (Randomforest and Gradient boost trees). The linear model wasn't able to model the data accurately, juding by the F1 score metric. It was defaulting on accurately classifying both the negative class and the positive class (ie Churn_Yes).
In Model 1 notebook, features were created that may be important for solving the problem. Features such as the Total calls a customer made, the total call time, the total charges charged for all calls made. Others such as the time spent for each call for day, evening and night calls were created too. These features were able to improved the f1 scores for all the three models compared to the baseline scores.
In model 2 notebook, features with no statistical significance (p-value > 5% significance level) with the target feature, were removed. This led to a slight decrease in the f1 scores compared to Model 1.
I model 3 noteook, alongside the features removed in model2, further features were removed -features from which other features were constructed. The same models used in the other models were still maintained. This idea led to a slight increase in the F1 score compared to model 2, but was comparable to that gotten from Model 1.
