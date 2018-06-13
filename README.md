# West Nile Prevention: 
Pesticide recommendations using predictive modeling 

# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Kaggle Competition - Starter

## Introduction

Chicago has a decades long history of West Nile, a virus spread to humans through infected mosquitoes. While many infected with the virus develop no symptoms, 20% develop mild symptoms such as fever and vomiting, and 0.7% develop serious symptoms that may result in death [1].  The first human cases of West Nile appeared in Chicago in 2002, with 225 cases and 22 fatalities [2]. In 2004, the City of Chicago started a surveillance and control program where mosquito traps were placed throughout the city and captured mosquitoes are tested for the virus every year from late spring to early fall [2]. The test results influence airborne pesticide usage to eradicate adult mosquitoes and prevent the spread of the virus. There is therefore value in accurately predicting West Nile outbreaks to help the city allocate resources for disease prevention.   

The goals for this project were to build a machine learning model to predict the presence of West Nile in mosquitoes in traps at specified locations in the city of Chicago. In addition, we conduct a pesticide cost-benefit analysis provide further recommendations to the City to maximize desired outcomes.   

## Dataset

The dataset, along with description, can be found here: [https://www.kaggle.com/c/predict-west-nile-virus/](https://www.kaggle.com/c/predict-west-nile-virus/).

**This is also where you will be submitting your code for evaluation**. We will be using the Kaggle Leaderboard to keep track of your score. The public leaderboard uses roughly 30% of the dataset to score an AUC (Area Under Curve) metric. [You can read more about the scoring metric here](https://www.kaggle.com/wiki/AreaUnderCurve).

> If you do not already have a Kaggle account, you will need to sign up on the website.  Also note that you will be submitting a "Late Submission" on Kaggle because the official competition has ended.  You can use the leaderboard to see how your results compare against roughly 1300 other data science teams!

You can submit predictions as many times as you want to Kaggle, but there is a limit of 5 submissions per day.  Be intentional with your submissions!


#### Navigating Group Work

This project will be executed as a group.  To make your team as effective and efficient as possible you should do the create a shared GitHub repo and project planning document as described in the deliverables section below.

## Deliverables

**GitHub Repo**

1. Create a GitHub repository for the group. Each member should be added as a contributor.
2. Retrieve the dataset and upload it into a directory named `assets`.
3. Generate a .py or .ipynb file that imports the available data.

**Project Planning**

1. Define your deliverable - what is the end result?
2. Break that deliverable up into its components, and then go further down the rabbit hole until you have actionable items. Document these using a project managment tool to track things getting done.  The tool you use is up to you; it could be Trello, a spreadsheet, GitHub issues, etc.
3. Begin deciding priorities for each task. These are subject to change, but it's good to get an initial consensus. Order these priorities however you would like.
4. You planning documentation (or a link to it) should be included in your GitHub repo.

**EDA**

1. Describe the data. What does it represent? What types are present? What does each data points' distribution look like? Discuss these questions, and your own, with your partners. Document your conclusions.
2. What kind of cleaning is needed? Document any potential issues that will need to be resolved.

**Note:** As you know, EDA is the single most important part of data science. This is where you should be spending most of your time. Knowing your data, and understanding the status of its integrity, is what makes or breaks a project.

# Modeling

While many of the best Kaggle submissions used highly engineered features (time-lagged weather statistics, polynomially-smoothed interaction terms, etc.) with excellent effects on their model scores, our time constraints prevented us from delving too deeply into feature engineering. We selected features that broadly related to temperature, moisture, and location.  We began with a broad feature set that we pruned down experimentally before settling on our final features.

For model selection, we began by identifying our data science problem as binary classification, yes/no West Nile virus present.  We considered a large family of classification models from sklearn. Including logistic regression, support vector classifiers, tree-based classifiers (decision trees, random forests, extra trees), and neural networks (pure dense and convolutional).

This data posed a peculiar difficulty: we had to predict even-year data but we could only train on odd-year data.  Since yearly trends in temperature and weather were idiosyncratic (some years very different than others), overfitting to these years was an early pitfall of our modeling process.  We mitigated this tendency by adapting our features to try to take year-to-year variance into account.

After tuning, our best model was logistic regression.  Our final logistic model received an RoC-AuC score of 0.68869, and its most important features were [insert graph].  These features out-performed more broad weather and location features, vindicating our initial belief that these features were good predictors.

[insert 2014 prediction plot]


**Presentation**
* Audience: You are presenting to members of the CDC. Some members of the audience will be biostatisticians and epidemiologists who will understand your models and metrics and will want more information. Others will be decision-makers, focusing almost exclusively on your cost-benefit analysis. Your job is to convince both groups of the best course of action in the same meeting and be able to answer questions that either group may ask.
* The length of your presentation should be about 20 minutes (a rough guideline: 2 minute intro, 10 minutes on model, 5 minutes on cost-benefit analysis, 3 minute recommendations/conclusion).  Touch base with your local instructor... er, manager... for specific logistic requirements!

---

**Your project is due at 10:00 AM EST/9:00 AM CST on Friday, Jun3 15.**

---

### Project Feedback + Evaluation

Data science is a field in which we apply data to solve real-world problems. Therefore, projects and presentations are means by which we can assess your ability to solve real-world problems in a data-driven manner.

Your final assessment ("grade," if you will) will be calculated based on a [topical rubric](https://docs.google.com/spreadsheets/d/1V6OzSHPXCJEe_sVT7B1vE7sT-jqNMNo-NrmZHtafMXY/edit?usp=sharing). For each category, you will receive a score of 0-3. From the rubric you can see descriptions of each score and what is needed to attain those scores. Make sure you look at the "Rubric P4" tab of the [spreadsheet](https://docs.google.com/spreadsheets/d/1V6OzSHPXCJEe_sVT7B1vE7sT-jqNMNo-NrmZHtafMXY/edit?usp=sharing).
