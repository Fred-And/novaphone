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
  Subscription services are everywere! Pretty much every service we pay for nowadays works through subscription plans.
  
  <li>Less burocracy
  <li>Possibility to cancel the service anytime
  <li>Lower costs
  <li>Upgrades
  <br><br>Those are just some of the possibilities we get to enjoy...
  <h4>But you own a business...</h4>
  your concern is wether someone is going to leave you solution or stay, in other words, the CHURN!!
  
  ### Nova Phone
  Nova Phone is a telecom company that provides mobile, landline and internet services. They're in the market for about 72 months and, they're looking     for a way to predict whether a client will or will not keep using the NovaPhone services. <br>
 
They handed me a `.csv` file containing some key informations about the business such as the age (65yo+), if the client is or not married, months using the company services, the price paid monthly, if internet is part of the contract and last but not least the **Churn** .
  
With those information in hand, I started to explore the phenomena and look for some information that could help indentify the causes of the churn.
___
I started with simple descriptive analysis to understand the data. It has **7043 columns and 18 rows**.

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
> The company could offer a bonus service in the first 6 months of contract to develop a better relationship with the client.

___
The second thing that I wanted to see, was the realation between the Churn and the type of contract (Monthly, One Year, Two Years)

![2](https://github.com/Fred-And/novaphone/blob/main/img/churn_by_contract.png)
    
> It gets clear for us that NovaPhone has `more clients dropping out when it's a Monthy contract`. This is a logical conclusion but maybe it's interesting to check for bonuses or lower prices for Anual plans, this way people will see more advantages on paying for a whole year.
___
Ok, we know that the bill price goes from `$18,25 till $118,75` but...how're they distributed?
![3](https://github.com/Fred-And/novaphone/blob/main/img/bill_price_distribution.png)
