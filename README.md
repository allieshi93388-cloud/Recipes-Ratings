# Calories in Recipes

by Allie Shi and Vanessa Nguyen

--

## Introduction

What types of recipes tend to have the most calories?

There are 234428 rows in this dataset. The relevant columns to answer this question include: 'minutes' (how long in minutes it took to complete a recipe), 'n_steps' (number of steps in recipe), 'n_ingredients' (number of ingredients in recipe), 'avg_rating' (average rating of recipes containing float values 0 to 5), 'calories' (number of calories in kilocalorie units), 'sugar' (amount of sugar in recipe, respresented by percentage of daily value), 'sodium' (amount of sodium in recipe, represented by percentage of daily value), 'protein' (amount of protein in recipe, represented by percentage of daily value), 'sat_fat' (amount of saturated fat, represented by percentage of daily value), 'sugar_yes' (True if sugar is in the recipe adn False if sugar is not in the recipe), and 'salt_yes' (True if salt is in the recipe adn False if salt is not in the recipe).

--

### Data Cleaning and Exploratory Data Analysis

Below is the cleaned dataset. Any 0 values in the 'rating' column has been filled with np.nan. The 'avg_rating' column has been created by grouping by 'id' and aggregating by mean. Columns 'date' and 'submitted' are converetd to datetime. Both 'nutrition' and 'ingredients' have been converted to lists. The values from the nutrition column has been separated to create columns: 'calories', 'total_fat', 'sugar', 'sodium', 'protein', 'sat_fat', 'carb'. 'sugar_yes' and 'salt_yes' columns are derived from the 'ingredients' column, and both contain boolean values representing if sugar is in the recipe ('sugar_yes') and if salt is in the recipe ('salt_yes').

| name                                 |     id |   minutes |   contributor_id | submitted           | tags                                                                                                                                                                                                                        | nutrition                                  |   n_steps | steps                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | description                                                                                                                                                                                                                                                                                                                                                                       | ingredients                                                                                                                                                                            |   n_ingredients |   user_id |   recipe_id | date                |   rating | review                                                                                                                                                                                                                                                                                                                                           |   avg_rating |   calories |   total_fat |   sugar |   sodium |   protein |   sat_fat |   carb | sugar_yes   | salt_yes   |
|:-------------------------------------|-------:|----------:|-----------------:|:--------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-------------------------------------------|----------:|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------:|----------:|------------:|:--------------------|---------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------:|-----------:|------------:|--------:|---------:|----------:|----------:|-------:|:------------|:-----------|
| 1 brownies in the world    best ever | 333281 |        40 |           985201 | 2008-10-27 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'for-large-groups', 'desserts', 'lunch', 'snacks', 'cookies-and-brownies', 'chocolate', 'bar-cookies', 'brownies', 'number-of-servings'] | 138.4, 10.0, 50.0, 3.0, 3.0, 19.0, 6.0     |        10 | ['heat the oven to 350f and arrange the rack in the middle', 'line an 8-by-8-inch glass baking dish with aluminum foil', 'combine chocolate and butter in a medium saucepan and cook over medium-low heat , stirring frequently , until evenly melted', 'remove from heat and let cool to room temperature', 'combine eggs , sugar , cocoa powder , vanilla extract , espresso , and salt in a large bowl and briefly stir until just evenly incorporated', 'add cooled chocolate and mix until uniform in color', 'add flour and stir until just incorporated', 'transfer batter to the prepared baking dish', 'bake until a tester inserted in the center of the brownies comes out clean , about 25 to 30 minutes', 'remove from the oven and cool completely before cutting']                                                  | these are the most; chocolatey, moist, rich, dense, fudgy, delicious brownies that you'll ever make.....sereiously! there's no doubt that these will be your fav brownies ever for you can add things to them or make them plain.....either way they're pure heaven!                                                                                                              | ['bittersweet chocolate', ' unsalted butter', ' eggs', ' granulated sugar', ' unsweetened cocoa powder', ' vanilla extract', ' brewed espresso', ' kosher salt', ' all-purpose flour'] |               9 |    386585 |      333281 | 2008-11-19 00:00:00 |        4 | These were pretty good, but took forever to bake.  I would send it ended up being almost an hour!  Even then, the brownies stuck to the foil, and were on the overly moist side and not easy to cut.  They did taste quite rich, though!  Made for My 3 Chefs.                                                                                   |            4 |      138.4 |          10 |      50 |        3 |         3 |        19 |      6 | False       | False      |
| 1 in canada chocolate chip cookies   | 453467 |        45 |          1848091 | 2011-04-11 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'cuisine', 'preparation', 'north-american', 'for-large-groups', 'canadian', 'british-columbian', 'number-of-servings']                                                               | 595.1, 46.0, 211.0, 22.0, 13.0, 51.0, 26.0 |        12 | ['pre-heat oven the 350 degrees f', 'in a mixing bowl , sift together the flours and baking powder', 'set aside', 'in another mixing bowl , blend together the sugars , margarine , and salt until light and fluffy', 'add the eggs , water , and vanilla to the margarine / sugar mixture and mix together until well combined', 'add in the flour mixture to the wet ingredients and blend until combined', 'scrape down the sides of the bowl and add the chocolate chips', 'mix until combined', 'scrape down the sides to the bowl again', 'using an ice cream scoop , scoop evenly rounded balls of dough and place of cookie sheet about 1 - 2 inches apart to allow for spreading during baking', 'bake for 10 - 15 minutes or until golden brown on the outside and soft & chewy in the center', 'serve hot and enjoy !'] | this is the recipe that we use at my school cafeteria for chocolate chip cookies. they must be the best chocolate chip cookies i have ever had! if you don't have margarine or don't like it, then just use butter (softened) instead.                                                                                                                                            | ['white sugar', ' brown sugar', ' salt', ' margarine', ' eggs', ' vanilla', ' water', ' all-purpose flour', ' whole wheat flour', ' baking soda', ' chocolate chips']                  |              11 |    424680 |      453467 | 2012-01-26 00:00:00 |        5 | Originally I was gonna cut the recipe in half (just the 2 of us here), but then we had a park-wide yard sale, & I made the whole batch & used them as enticements for potential buyers ~ what the hey, a free cookie as delicious as these are, definitely works its magic! Will be making these again, for sure! Thanks for posting the recipe! |            5 |      595.1 |          46 |     211 |       22 |        13 |        51 |     26 | False       | False      |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | 194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', ' cream of chicken soup', ' sharp cheddar cheese', ' garlic powder', ' ground black pepper', ' salt', ' milk', ' soy sauce', ' french-fried onions']          |               9 |     29782 |      306168 | 2008-12-31 00:00:00 |        5 | This was one of the best broccoli casseroles that I have ever made.  I made my own chicken soup for this recipe. I was a bit worried about the tsp of soy sauce but it gave the casserole the best flavor. YUM!                                                                                                                                  |            5 |      194.8 |          20 |       6 |       32 |        22 |        36 |      3 | False       | False      |
|                                      |        |           |                  |                     |                                                                                                                                                                                                                             |                                            |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                        |                 |           |             |                     |          | The photos you took (shapeweaver) inspired me to make this recipe and it actually does look just like them when it comes out of the oven.                                                                                                                                                                                                        |              |            |             |         |          |           |           |        |             |            |
|                                      |        |           |                  |                     |                                                                                                                                                                                                                             |                                            |           |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                                                                                                                   |                                                                                                                                                                                        |                 |           |             |                     |          | Thanks so much for sharing your recipe shapeweaver. It was wonderful!  Going into my family's favorite Zaar cookbook :)                                                                                                                                                                                                                          |              |            |             |         |          |           |           |        |             |            |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | 194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', ' cream of chicken soup', ' sharp cheddar cheese', ' garlic powder', ' ground black pepper', ' salt', ' milk', ' soy sauce', ' french-fried onions']          |               9 |   1196280 |      306168 | 2009-04-13 00:00:00 |        5 | I made this for my son's first birthday party this weekend. Our guests INHALED it! Everyone kept saying how delicious it was. I was I could have gotten to try it.                                                                                                                                                                               |            5 |      194.8 |          20 |       6 |       32 |        22 |        36 |      3 | False       | False      |
| 412 broccoli casserole               | 306168 |        40 |            50969 | 2008-05-30 00:00:00 | ['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']                                                                        | 194.8, 20.0, 6.0, 32.0, 22.0, 36.0, 3.0    |         6 | ['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']                                                                                                                                                                                                                                                                                                                              | since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008 | ['frozen broccoli cuts', ' cream of chicken soup', ' sharp cheddar cheese', ' garlic powder', ' ground black pepper', ' salt', ' milk', ' soy sauce', ' french-fried onions']          |               9 |    768828 |      306168 | 2013-08-02 00:00:00 |        5 | Loved this.  Be sure to completely thaw the broccoli.  I didn&#039;t and it didn&#039;t get done in time specified.  Just cooked it a little longer though and it was perfect.  Thanks Chef.                                                                                                                                                     |            5 |      194.8 |          20 |       6 |       32 |        22 |        36 |      3 | False       | False      |

Below is a boxplot depicting the distribution of sodium values from the dataset. There are quite a few outliers, all are in the upper direction, and this can skew our predictions since there is less representation of high sodium recipes.

<iframe
  src="assets/sodium_box.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Below is a boxplot depicting the distribution of the number of ingredients values from the dataset. There are outliers in the upper direction, so this may cause skew in our predictions.

<iframe
  src="assets/n_ingredients.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Below is a scatterplot depicting the behavior of calories as sugar increases. There is a relatively positive relationship, which may be biased due to the outliers near higher sodium and calorie levels.

<iframe
  src="assets/sugar_calories.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Below is a scatterplot depicting the behavior of calories as sodium increases. There is a relatively positive relationship, which may be biased due to the outlier near sodium level 30000 and the high calorie levels near sodium level 0.

<iframe
  src="assets/sodium_calories.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Below is a pivot table evaluating the average calories of recipes based on the 'sodium' and 'n_ingredients' categories they fall into. The columns are sodium levels split into intervals derived from the boxplot quartiles. The rows are the number of ingredients split into intervals derived from its respective boxplot quartiles. The highest mean calorie score corresponds to the sodium interval [75,30000) and the n_ingredient interval [11,18). The average calories tend to increase from left to right, or as sodium increases. From top to bottom, or as the number of ingredients increase, the average calories seems to increase and peak midway, and then decrease slightly. So there seems to be a relatively positive relationship between average calories and sodium, but a less linear relationship between average calories and number of ingredients.

|   [0,5) |   [15,33) |   [33,75) |   [5,15) |   [75,30000) |
|--------:|----------:|----------:|---------:|-------------:|
| 195.943 |   377.271 |   577.398 |  278.437 |      1097.21 |
| 222.921 |   435.097 |   576.927 |  319.318 |      1376.78 |
| 328.948 |   504.151 |   659.334 |  397.228 |      1274.84 |
| 206.863 |   372.063 |   560.464 |  279.264 |      1163.99 |
| 224.273 |   403.747 |   576.977 |  284.964 |      1275.48 |

--

### Assessment of Missingness

The columns with missing values are: 'name' (1), 'description' (114), 'rating' (15035), 'review' (57), 'avg_rating' (2776). All columns except 'name' have shown significant difference between missing and non-missing when tested with at least one other column. So only the 'name' column is MNAR. Additional data on age, for example, could explain the missingness of this column. 

The missingness in the 'rating' column is dependent on the 'calories' column with a p-value of 0 at a .01 signifiance level. Therefore, the missingness of the 'rating' column is missing at random. The distribution of 'calories' when 'rating' is missing and not missing is displayed below:

<iframe
  src="assets/Calories_Rating_Missingness.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

Below depicts the distribution of the simulated Total Variation Distances (TVD) compared to the observed TVD.

<iframe
  src="assets/TVD_dist.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

--

### Hypothesis Testing

Question: What is the relationship between the sodium intake and calories of recipes?
Null hypothesis: There is no significant calorical difference between recipes with sodium levels greater than or equal to 100 and less than 100.
Alternative hypothesis: There is a significant calorical difference between recipes with sodium levels greater than or equal to 100 and less than 100.
Test statistic: absolute difference in means
Significance level = .01
p-value = 0.0
Conclusion: Since the p-value is less than the significance level, we reject the null that there is no significant calorical difference between recipes with sodium levels greater than or equal to 100 and less than 100.

Below depicts the distribution of the simulated test statistic compared to the observed test statistic.

<iframe
  src="assets/abs_diff_dist.html"
  width="800"
  height="600"
  frameborder="0"
></iframe>

--

### Framing a Prediction Problem

Prediction problem: Predict calories of recipes

I am using a regression model to predict the 'calories' column of the dataset. The metric used to evaluate the model will be the R squared value since this is a regression model. Other metrics, such as accuracy, are stronger metrics when looking at classification models.

--

### Baseline Model

Features and Encodings: The features used in this model are 'sugar_yes' (nominal) and 'sodium' (quantitative). One-hot-encoding was used to transform the 'sugar_yes' column. 

Data: Testing (unseen) and training (seen) data was generated from the original dataset. 

Results: The model had R-squared values .04641 on the training data and 0.0634 on the testing data. 

Performance: Overall, the performance of this model was fair since R-squared values are relatively low for both training and testing data. The R-sqared value is slightly higher for the testing data, but not by a lot, so there is minimal overfitting.


--

### Final Model

Changes: From the baseline model, 'sugar_yes' was removed, and 'sugar', 'protein', and 'sat_fat' columns were added as predictors. The new predictors model the behavior of the 'calories' column more closely than 'sugar_yes', which could not make as good predicions with its binary values. 

Data: Testing (unseen) and training (seen) data was generated from the original dataset. These remain the same from the baseline model.

Parameter and Model Selection: When performing cross-validation, predicting on 'sugar', 'sodium', 'protein', and 'sat_fat' yielded the smallest negative root mean squared error compared to the features used in the baseline model as well as other feature combinations. The linear regression model remained the same since the data of 'calories' and of the features all relatively appear linear. 

Results: The training data had a R-squared value of 0.84916 and the test data had a R-squared value of 0.8567. The entire dataset had a R-squared value of 0.8504.

Performance: The final model is a worse predictor of both the training and testing data since its R-squared values are higher than the baseline model's. Regardless, there was less difference between the R-squared values of the training and testing data for the final model. So this can indicate more less surprising predictions from the final model on unseen data.

--

### Fairness Analysis

Group X: recipes with sugar levels greater than 64
Group Y: recipes with sugar levels less than or equal to 64

Evaluation metric: root mean squared error (RMSE)

Test Statistic: absolute difference in RMSE
Significance Level =  .01

Null Hypothesis: Our model is fair. The difference in RMSE for recipes with sugar levels greater than 64 and less than or equal to 64 are roughly the same, and any differences are due to random chance.
Alternative Hypothesis: Our model is unfair. The difference in RMSE for recipes with sugar levels greater than 64 and less than or equal to 64 are different.

p-value = 0.0

Conclusion: Since the p-value is less than the signifiance level, we reject the null that our model is fair.  