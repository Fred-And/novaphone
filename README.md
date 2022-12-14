<h1 align="center">NovaPhone Churn Prediction</h1>
<h3 align="center">A classification problem.</h3>


<h4 align="center">Languages and Tools used in this project:</h4>

<p align="center"> <a href="https://git-scm.com/" target="_blank" rel="noreferrer"> 
  <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> 
  </a> 
  <a href="https://pandas.pydata.org/" target="_blank" rel="noreferrer"> 
    <img src="https://raw.githubusercontent.com/devicons/devicon/2ae2a900d2f041da66e950e4d48052658d850630/icons/pandas/pandas-original.svg" alt="pandas" width="40" height="40"/> 
  </a> 
  <a href="https://www.python.org" target="_blank" rel="noreferrer"> 
    <img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/python/python-original.svg" alt="python" width="40" height="40"/> 
  </a> 
  <a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"> 
    <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> 
  </a> 
  <a href="https://seaborn.pydata.org/" target="_blank" rel="noreferrer"> 
    <img src="https://seaborn.pydata.org/_images/logo-mark-lightbg.svg" alt="seaborn" width="40" height="40"/> 
  </a> 
</p>
  <br>
  Subscription services are everywhere! Pretty much every service we pay for nowadays works through subscription plans.
  
  <li>Less bureaucracy
  <li>Possibility to cancel the service anytime
  <li>Lower costs
  <li>Upgrades
  <br><br>Those are just some of the possibilities we get to enjoy...
  <h4>But you own a business...</h4>
  your concern is wether someone is going to leave you solution or stay, in other words, the CHURN!!
  
  ### Nova Phone
  Nova Phone is a telecom company that provides mobile, landline, and internet services. They're in the market for about 72 months and, they're looking for a way to predict whether a client will or will not keep using the NovaPhone services.

They handed me a .csv file containing some key information about the business such as the age (65yo+), if the client is or is not married, months using the company services, the price paid monthly, if the internet is part of the contract and last but not least the Churn.
With that information in hand, I started to explore the phenomena and look for some information that could help identify the causes of the churn.
  
With those information in hand, I started to explore the phenomena and look for some information that could help indentify the causes of the churn.
___
I started with a simple descriptive analysis to understand the data. It has **7043 columns and 18 rows**.

Each line represents a client. In this dataset we have **1869 customers which left the NovaPhone**, the others are still using the services.

1. The client who pays the most in NovaPhone, pays `$118,75 per month.`
2. The client who pays the least in NovaPhone, pays `$18,25 per month.`
3. `72 months` is the time of the longest contract
4. `00 months` is the time of the shortest contract
    
_There're no null values in this dataset_
    
## Data Visualization
    
The first thing I wanted to see, was the relation between the Churn and for how many months the client is using the services. This is the result:
![1](https://github.com/Fred-And/novaphone/blob/main/img/churn_for_month.png)
    
It's possible to see that `the highest concentration of churns are within the first 5 months of contract`, after this mark, the number of churns do not trespass the 50 mark as shown.
> The company could offer a bonus service in the first 6 months of the contract to develop a better relationship with the client.

___
The second thing that I wanted to see, was the relation between the Churn and the type of contract (Monthly, One Year, Two Years)

![2](https://github.com/Fred-And/novaphone/blob/main/img/churn_by_contract.png)
    
> It gets clear to us that NovaPhone has `more clients dropping out when it's a Monthy contract`. This is a logical conclusion but maybe it's interesting to check for bonuses or lower prices for annual plans, this way people will see more advantages in paying for a whole year.
___
Ok, we know that the bill price goes from `$18,25 to $118,75` but...how're they distributed?

![3](https://github.com/Fred-And/novaphone/blob/main/img/bill_price_distribution.png)
    
`I plotted this histogram with only 4 bins on purpose.` I wanted to see how the prices are distributed within this range because that's the price range I'll split the data between:
- Cheap
- Medium
- Expensive
- Expensive +

It's possible to see by the red line, that `the amount of churns is expressive between the $60 and $100 range` and slowly decreases after the $100 mark. To take a better look at this phenomenon, I plotted the relationship between those price ranges mentioned above and the Churn numbers.
    
![4](https://github.com/Fred-And/novaphone/blob/main/img/churn_by_price_intervals.png)
    
**Bam!** That's pretty much what we were expecting, `bigger concentration of churns in the Expensive range.` 
> NovaPhone could renegotiate the bill prices whether by increasing the number of services provided with no additional fees or by reducing the price until it reaches the Medium or Cheap range.
___
Ok, so far we've concluded that:
- [x] Churn is higher in the first five months of contract.
- [x] It's better for NovaPhone to close at least annual contracts in order to decrease the churn caused by Monthly contracts.
- [x] Considering the created price ranges, the customers located within the Expensive price range ($60 - $100), are more likely to churn.
    
After that, I got myself thinking about the distribution of the bill prices and the contract duration. What's the correlation between them and double check the `"Churn price range"` if we may call it this way.
    
![5](https://github.com/Fred-And/novaphone/blob/main/img/kde_month_bill_contract.png)
    
This density plot shows that if a client with 0 - 5 months of NovaPhone is having to pay a monthly subscription of $60 to $100, the chances of churn are higher. **BUT** `who has to tell me whether a client will or will not drop is the algorithm, not my intuition`
    
So let's jump into the

## Modeling
    
Alright, we already know that we're dealing with a `classification problem`. To help me with that, I'll apply three different classification models and check which one fits (literally) the best in our situation.

Before starting, let's balance our data...you can check the left image below where we have the `y - Churn` before balancing. We had only a few samples of `Churn = 1` 

> Considering that this model is all about predicting Churns == 1, we really need to balance this data to help the model achieve better results.

The right image shows the result after the `Oversampling`.

![6](https://github.com/Fred-And/novaphone/blob/main/img/before_after.png)

### Great! We did it!

Now let's put our modeling skills into the game. `I'll be using three different classification algorithms`.
- K-Nearest Neighbors (KNN)
- Naive Bayes
- Decision Tree Classification

___
`KNN using hte Euclidean metric`
![7](https://github.com/Fred-And/novaphone/blob/main/img/knn_modeling.png)
___

`BNN usinf the BernoulliNB`

![8](https://github.com/Fred-And/novaphone/blob/main/img/nb_modeling.png)
___

`DTC using the Gini Impurity criteria instead of entrophy`

![9](https://github.com/Fred-And/novaphone/blob/main/img/dtc_modeling.png)

## Metrics
Used Metrics
- Confusion Matrix
- Accuracy
- Precision
- Recall
- F1 Score

![10](https://github.com/Fred-And/novaphone/blob/main/img/confusion_matrix.png)
![11](https://github.com/Fred-And/novaphone/blob/main/img/accuracy_score.png)
![12](https://github.com/Fred-And/novaphone/blob/main/img/precision_score.png)
![13](https://github.com/Fred-And/novaphone/blob/main/img/recall_score.png)
![14](https://github.com/Fred-And/novaphone/blob/main/img/f1_score.png)

