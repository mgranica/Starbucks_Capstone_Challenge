# Starbucks_Capstone_Challenge

## Project description

* Within the business strategy of the Starbucks company, we focus on the permeability of its offers for a limited group. The datasets provide us with information on both the demographic characteristics of consumers and their receptivity to different types of offers.
* Within the supervised models of Machine learning, these types of problems refer to Classification issues. It consists of a predictive model that infers a target class from a data set
* The objective will be to build a machine learning model that allows identifying, based on the different demographic segments, the result of the offers offered to customers.


## Requirements & Dependencies

* data analysis
 * pandas
 * numpy
 * math
 * json
 * ipywidgets
 * seaborn
 
* Machine leerning
 * scikit learn

## Data Sets

The data is contained in three files:

* portfolio.json - containing offer ids and meta data about each offer (duration, type, etc.)
* profile.json - demographic data for each customer
* transcript.json - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

**portfolio.json**
* id (string) - offer id
* offer_type (string) - type of offer ie BOGO, discount, informational
* difficulty (int) - minimum required spend to complete an offer
* reward (int) - reward given for completing an offer
* duration (int) - time for offer to be open, in days
* channels (list of strings)

**profile.json**
* age (int) - age of the customer 
* became_member_on (int) - date when customer created an app account
* gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
* id (str) - customer id
* income (float) - customer's income

**transcript.json**
* event (str) - record description (ie transaction, offer received, offer viewed, etc.)
* person (str) - customer id
* time (int) - time in hours since start of test. The data begins at time t=0
* value - (dict of strings) - either an offer id or transaction amount depending on the record


## Project Design

### Data Cleaning
* portfolio dataframe:
  * Rename id column name to offert_id and set as index
  * Hot-encoding the offer_type column
  * Hot-encoding the channels column
* profile dataframe:
  * Drop age values == 118
  * Drop NaN values for income and gender columns
  * Dateformat became_member_on
  * Binary values for gender column
* transcript dataframe:
  * unstack amount and offer id columns
  * set time unit in days

###Exploratoriy Data Analysis
* Univariable exploration
* Bivariable exploration
* Segmentation demographics and offer status summary table

### Machine learning & preprocessing

* Based on the different categorical fields, how the different demographic segmentations respond to each one of the types of offers present in the exercise, we can build a Machine learning model that indicates how a certain demographic profile would respond to the different types of offers
* To validate the impact that Starbucks promotions have, we are going to exclude received offers from the study, in this way we will only take into account the offers seen over the completed ones.

### ML train&fit the model

* Even if we decide to do a binary classification we could also have tried to do Multiclass classification for the offerts status:
  * Logistic regression
  * Support Vector Machine
  * K-Nearest Neighbors
  * Decision Tree
  * Random forest

