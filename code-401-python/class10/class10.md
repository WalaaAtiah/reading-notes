## Read 10 - Linear Regressions

### Linear Regression in Python [source](https://realpython.com/linear-regression-in-python/)

**What Is Regression?**
* *Regression searches for relationships among variables,Generally, in regression analysis, you consider some phenomenon of interest and have a number of observations. Each observation has two or more features. Following the assumption that at least one of the features depends on the others, you try to establish a relation among them. In other words, you need to find a function that maps some features or variables to others sufficiently well.*

<br>

**Types of Regression**

 1. **Simple Linear Regression** 

    * *Simple or single-variate linear regression is the simplest case of linear regression, as it has a single independent variable, 𝐱 = 𝑥.*

     <img src="https://files.realpython.com/media/fig-lin-reg.a506035b654a.png" alt="drawing" style="width:500px;"/>

2. **Multiple Linear Regression**
    * *Multiple or multivariate linear regression is a case of linear regression with two or more independent variables.*
3. **Polynomial Regression**
      * generalized case of linear regression. You assume the polynomial dependence between the output and inputs and, consequently, the polynomial estimated regression function.
<br>

**Underfitting and Overfitting**
  * **Underfitting**  occurs when a model can’t accurately capture the dependencies among data, usually as a consequence of its own simplicity. It often yields a low 𝑅² with known data and bad generalization capabilities when applied with new data.
  * **Overfitting** happens when a model learns both data dependencies and random fluctuations. In other words, a model learns the existing data too well.

      <img src="https://files.realpython.com/media/poly-reg.5790f47603d8.png" alt="drawing" style="width:600px;"/>


<br>
<br>


### How to Run Linear Regression in Python scikit-Learn  [source](https://www.crayondata.com/how-to-run-linear-regression-in-python-scikit-learn/)

 *you can implementing linear regression in Python using numpy, scipy, stats model and sckit learn.*
![linear regression](https://bigdata-madesimple.com/wp-content/uploads/2016/04/Prices.png)

### Scikit-learn:is a powerful Python module for machine learning. It contains function for regression, classification, clustering, model selection and dimensionality reduction.

1.  import all the python library need
   
      <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Explore-1.png" alt="drawing" style="width:200px;"/>

**Exploring Boston Housing Data Set**  is available in sklearn Python module

2. import Boston data set into Ipython notebook and store it in a variable called boston.
   
     <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/sklearn.png" alt="drawing" style="width:300px;"/>

3. I am going to convert boston.data into a pandas data frame.

    <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Pandas-DataFrame.png" alt="drawing" style="width:400px;"/>

4. I am going to add these target prices to the bos data frame.
   <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Bos-Price.png" alt="drawing" style="width:300px;"/>

   <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/RAD.png" alt="drawing" style="width:400px;"/>

5. ### Scikit Learn
  * First, I am going to import linear regression from sci-kit learn module. Then I am going to drop the price column as I want only the parameters as my X values. I am going to store linear regression object in a variable called lm.

     <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Skitlearn-linear-model1.png" alt="drawing" style="width:400px;"/>

6. ### Fitting a Linear Model
 * In [20]: lm.fit(X, bos.PRICE)
  
       Out[20] : LinearRegression(copy_X=True, fit_intercept=True, normalize=False)

* I then construct a data frame that contains features and estimated coefficients.

    <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/pd-data-frame.png" alt="drawing" style="width:600px;"/>

* As you can see from the data frame that there is a high correlation between RM and prices. Lets plot a scatter plot between True housing prices and True RM.

   <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Scatter-plot.png" alt="drawing" style="width:500px;"/>
   <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Relationship-between-RM-and-Price.png" alt="drawing" style="width:500px;"/>

7. ### Predicting Prices
 * <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/lm-predict.png" alt="drawing" style="width:500px;"/>
 * <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Scatter-plot-in-the-pandas.png" alt="drawing" style="width:500px;"/>
 * <img src="https://bigdata-madesimple.com/wp-content/uploads/2016/04/Prices-vs-predicted-prices.png" alt="drawing" style="width:500px;"/>