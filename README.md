# DALI Data Challenge [Dartmouth Course Exploration]
Hi, I'm Kabir, and here's my submission for the DALI data challenge, specifically with the ```Dartmouth - Courses.csv``` data. The following process is what I followed in ```DALI Course Exploration.ipynb```.
 
## Pipeline

My goal throughout this pipeline was to be able to build up enough understanding to develop a model to predict <b>Median GPA Points</b>.

### Preliminary Exploration / Exploratory Data Analysis
For this portion of the pipeline, I studied the raw data and its features, looking at whether features were categorical or numerical (how many unique values there were), and understanding whether course department had broader, characteristic metrics (i.e. whether certain departments had higher GPAs, enrollments, etc.), as department was some feature I ultimately couldn't figure out how to incorporate in my model but is something that could have potentially been useful if manipulated in some other way. 

* This predominantly meant using pandas and built-in methods/features to analyze the data.

### Data Visualization
I tried to visually study the relationships between features, going through scatterplots between each pair of features. Then, I began focusing on more interesting relationships, such as those between section size, enrollments, etc. and median GPA. I did so on a course by course bases as well as using overall department metrics. I primarily used histograms, bar charts, and scatter plots.

I also studied the above relationships for certain departments that interested me, and my conclusions were that for COSC, GOVT, and SPAN — though there was nothing glaring — COSC and GOVT had relatively nominal relations between course #, enrollments, and section size, and median GPA, while  SPAN tended to show a positive correlation between course # and GPA and a negative correlation between enrollments and section size, and GPA.

Additionally, I looked at a few relationships for department-wide metrics, just out of curioisity to see if departments tended to tell a stronger picture than individual classes (which in some cases seemed true, but again, the complexity that came with encoding posed an issue).

Overall, median GPA seemed to be the most visually related to enrollments and section size.

* Here, I used a mix of matplotlib and seaborn.

### Preprocessing & Analysis
Here, I imputed missing values in the data (for the 1000+ null values) using an imputation library, which prevented me from having to delete those data points entirely, though exploring how deleting them could have been another thing to look into.

I also looked at the Pearson and Spearman correlation values between each numerical feature and median GPA, which substantiated the observation that section size and enrollments seemed the most highly correlated with median GPA.

* Here, I used scikit-learn's KNN imputer for convenience, which seemed to work okay when studying the imputed values, though R and certain libraries could have worked better.
* I used pandas' built-in `.corr()` to study relationships here.

### Machine Learning Steps
Based on the visual relationships and correlation values, I opted to use linear regression for this prediction task. I ultimately went through a few feature selection steps, testing the model with all numerical features (i.e. barring <b>Department</b>), only enrollments and section size, and then just section size. Ultimately, section size on its own seemed to perform better, though this validity is limited by the sample size and randomness of the samples chosen.

I also applied the same pipeline (using only section size as a feature) for the GOVT and COSC departments' classes to see if predicting median GPA for given courses in either was more/less/equally as accurate.

Ultimately, the model didn't perform exceptionally well in any instance but actually performed the best, using the coefficient, R^2, MAD, and MSE, with the whole dataset.



