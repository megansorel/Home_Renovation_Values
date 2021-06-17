# Ames Housing Project

**Problem Statement**

House Flippers LLC makes money traveling the country flipping homes. They are going to Ames, Iowa, due to the large housing market in the area with multiple houses to work on.

They want to know which features will add the most value to the houses they flip so they know what to invest time and money in as they work on the houses. They need a breakdown of possible improvements to a house without adding square-footage, and what is the value each improvement adds so they can decide which features will give the best return on investment.  

**Workbooks**:

Lasso-Best Model - the best predictor for housing prices overall, used for feature selection

LR -Best Features Not Scaled - the actual predicted value of top performing features chosen by Lasso, used for comparison to target variables

LR - Renovations Not Scaled - the actual predicted value of target features

LR Renovations Scale - a look at model performance with LR when features are scaled and transformed. Not used for recommendations.

Ridge Renovations Scaled -a look at model performance with Ridge when features are scaled and transformed. Not used for recommendations.

Test Cleaning

Train Cleaning and EDA

 A list of the data used in this project can be found here

http://jse.amstat.org/v19n3/decock/DataDocumentation.txt

**Summary of Cleaning and Analysis:**

The data used was from Ames, Iowa Assessor’s Office, with over 2930 homes in the database. Certain houses with over 5,000 square feet were removed from the dataset according to the impact it will have on the model.

Additionally, we did not include house features which were specific to less than 15% of the dataset, or were redundant features.

Houses were checked for lot-only listings by looking for places with 0 beds, baths and square feet. Nulls were filled with means of similar listings or with a 0 if the feature did not pertain to that house.

Any features that could be converted to scales were. The scale was determined by the effect each category had on the price relative to not having the feature (which was a 0), whether the category was worse than 0 or better than 0, determined by the effect on price.  

A list of features whose distributions were not even among the housing set was made. This list was used as reference when comparing models and choosing which features to focus on when considering the features to use in the model. We could reference this list or drop, in the case of Linear Regression models without regularization.

**Modeling**

Modeling was done originally in Lasso as a form of feature selection. For the project, it was important to see which features affected the price of the house overall as a starting point. However, some features cannot be controlled specific to a house, so the focus was on features renovators could apply to any home to raise the value.
The Lasso model accounted for 93 percent of the variation in housing prices. The median absolute error from the model prediction and actual price was about 10,000 dollars.

Linear Regression and Ridge were used with the features the renovators could focus on as they improved the house. At first, garage type was scaled however, after the initial modeling, it was worth making the garage into dummy features in the final evaluation, and their ranking did change from my original guess.

Linear Regression was used for the final recommendations for renovations without scaling so that the coefficients would be preserved in the original units, which Ridge would not have been able to do. The model accounted for 78\% of the variation in housing prices given the features in the model.  

**Outcomes**

From the feature selection model, the size and quality of a house are those that add the most value per unit.

The LR model gave insights on the target features for renovation recommendations.

With all other values held constant, the best garage size is that of a 3 car garage, adding a value of \$63,636 to a home. 

A builtin garage is the best type, adding \$54,260 to a home's price holding all other features in this model constant. 

Looking at basement quality (height), which is on 5 point scale: <70 inches to >=100 inches, with 0 being no basement. 
For every 10 inches you add to a basement, the home value increases by \$14,270. 

Every 1 foot of square feet that is finished adds \$24 to the home value.

We can see that bathrooms in the basement actually decrease the value of the home, with every 1 half bath detracting \$8,490 dollars from the home value and each full bath added detracting \$5,885 dollars. 

Finally, adding a wooden deck would also increase the value of the house, with all else held constant, at $43 per square foot deck.

**Final Recommendations**
The final recommendations for garage rennovations would be to add a two or three car gargae. If space is a concern, in terms of total home square feet or lot size, then converting a basement to a garage is a lucrative option. A 20x20 garage (2 car garage) in the basement can add $31,000 dollars to the home value.

When building a garage, it is worth considering the size that it is taking away from the basement. Finished basements do add to the home value, but at what point is it worth it to finish the basement at the expense of the square feet taken up by a garage?

The mean of homes with a basement garage is about $155,600. To beat that price with a finished basement, you would need at least 1,000 square feet.

The best way to add value to the house with a basement is to both raise the ceilings and finish the basement, without adding bathrooms.

Sources:

[Data Dictionary](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt)

Coding

[https://stackoverflow.com/questions/31569384/set-value-for-particular-cell-in-pandas-dataframe-with-iloc/46493001](https://stackoverflow.com/questions/31569384/set-value-for-particular-cell-in-pandas-dataframe-with-iloc/46493001)

[https://towardsdatascience.com/using-pandas-transform-and-apply-to-deal-with-missing-data-on-a-group-level-cb6ccf060531](https://towardsdatascience.com/using-pandas-transform-and-apply-to-deal-with-missing-data-on-a-group-level-cb6ccf060531)

[https://towardsdatascience.com/introduction-to-pandas-apply-applymap-and-map-5d3e044e93ff#:~:text=And%20the%20Pandas%20official%20API,or%20on%20values%20of%20Series.&text=map()%20is%20used%20to,a%20Series%20with%20another%20value](https://towardsdatascience.com/introduction-to-pandas-apply-applymap-and-map-5d3e044e93ff#:~:text=And%20the%20Pandas%20official%20API,or%20on%20values%20of%20Series.&text=map()%20is%20used%20to,a%20Series%20with%20another%20value).

[https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html)

[https://www.python-graph-gallery.com/basic-barplot-with-seaborn](https://www.python-graph-gallery.com/basic-barplot-with-seaborn)

[https://stackoverflow.com/questions/37366717/pandas-print-column-name-with-missing-values](https://stackoverflow.com/questions/37366717/pandas-print-column-name-with-missing-values)

[https://pbpython.com/pandas-qcut-cut.html](https://pbpython.com/pandas-qcut-cut.html)

[https://www.python-graph-gallery.com/](https://www.python-graph-gallery.com/)

[Lesson Notes from DSI](https://git.generalassemb.ly/DSIR-412/course-info)
