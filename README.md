# Can a Neural Network Predict Golf Scores for the PGA Masters Event?
![My Remote Image](https://www.cbs42.com/wp-content/uploads/sites/81/2020/03/Masters-UPDATED.jpg?w=1920&h=1080&crop=1)
## Introduction
When brainstorming project ideas, it came apparent that I wanted to work on something that I was heavily interested in. I decided I wanted to combine my interests of neural networks with the sport of golf.

I was curious to see if I could accurately predict the golf scores for the annual PGA Masters Tournament, using deep learning techniques. This project would not be hosted or deployed anywhere. Instead, it would be able to be run locally on ones computer. 

The goal of this project was to try to predict golf scores, while also further gaining knowledge in the deep learning/machine learning space.
## Selection of Data.
The first step in this project was to get data. Because of time constraints, I decided to use this web scraper I found on github, that scrapes the data of the offical PGA website using R. [https://github.com/jdubbert/Scrape-World-Golf-Rankings](https://github.com/jdubbert/Predicting-2019-Masters/blob/master/PGA_Scrape_Data.Rmd)

This CSV file can be found here

Data preview:
This data has 42 different features, and has 1003 samples.
![ds data preview](https://user-images.githubusercontent.com/68667116/205520250-e7baa61c-6634-4ce2-a640-11f4560b2242.png)


Fortunately, this data did not need that much munging and cleaning, besides some formating issues with 5 different columns.
![Screenshot 2022-12-04 175739](https://user-images.githubusercontent.com/68667116/205520672-50ae91b8-5042-49c6-8b27-d299e9a7394f.png)

These columns needed to be converted to numerical columns. I did this by creating these five functions.
![Screenshot 2022-12-04 175856](https://user-images.githubusercontent.com/68667116/205520750-59bfa90b-8ae8-47e3-9787-5c293ca58741.png)

Problem Solved!

Next we needed to find what features we would use for our model. To do this I used a classifier called ExtraTreesClassifier (https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.ExtraTreesClassifier.html):


![Screenshot 2022-12-04 180942](https://user-images.githubusercontent.com/68667116/205521313-c4b184d0-c41b-40f8-a5f3-d3760fddbc7b.png)


We then needed to normalize our features, so all of the numbers were on the same scale. We did this using make_column_transformer (https://scikit-learn.org/stable/modules/generated/sklearn.compose.make_column_transformer.html) function from the sklearn library:

![Screenshot 2022-12-04 214754](https://user-images.githubusercontent.com/68667116/205538583-dc5229ff-bc00-4011-a241-11a95fb9a047.png)


Next it was time to create our model. After playing around with hyperparameters for a bit, I decided to create a network with 4 hidden layers, a mean squared error loss function, an Adam optimizier, a learning rate of 0.01, and 300 epochs. The does not need to be saved anywhere, because I created a random seed, so the numbers will always be the same.


![Screenshot 2022-12-04 182711](https://user-images.githubusercontent.com/68667116/205522201-23e7fe78-49e6-437b-b37c-08c63572f56b.png)




## Methods
Tools:
* Google Colab for code development
* NumPy, Pandas, Seaborn, Matplotlib, for EDA (exploratory data analysis) and data cleaning
* sklearn for data splitting and normalization
* TensorFlow for model creation and validation
## Results
After compiling the model. It was time to evaluate. To make things easier and more consistent, I used train_test_split's random_state and TensorFlows random.set_seed both equal to 11, so that I would get the same model performance each run I did.


![Screenshot 2022-12-06 120552](https://user-images.githubusercontent.com/68667116/205976383-13114516-6a7c-4c70-991d-b50bd905394b.png)

Plotting the loss function againts the number of epochs

![Screenshot 2022-12-06 120800](https://user-images.githubusercontent.com/68667116/205976794-0ef52a12-ace2-4e8d-8b5f-dfc89f877b96.png)


CSV file of test results can be found here https://github.com/SamMilnes/DS-Individual-Final-Project/blob/main/Results_Final%20(4).csv



## Discussion
After experimenting with different hyperparamters for my deep learning network, I found that my model was most accurate when I used Sequential model with 4 differnt dense layers, as well as using an Adam optimizer, learning rate of 0.01, 300 epocs, a relu activation function, anda mean squared error loss function. 

Diving deeper into my results, it turns out that it is actually pretty hard to predict golf scores for a specific golf tournament. Having a background in golf, there is so many other external factors that can go into someones final round score. Golf is an indivdual sport, meaning if one player has one bad day, it can mess up there entire total score.


The final mean squared error for my training data was 53.89, which in reality is not that good. But looking at the test results, some of the scores were actually pretty close. Now on the flip side, some of the predicted scores were actually really off the mark.

Overall, this was a really fun project to do. I learned a lot about machine learning and also learned that it is extremly difficult to predict someones scores for the PGA Masters tournament that happens every year.

Even though I did this project for my data science class project, I plan on trying to make my model more accurate and mess around with it more in the feature.
## Reference
Write Reference Here
## Instructions For Running Project
The only special instructions for running the code is to change the file path to the csv data file being read in. When I created this project, I used Google Colab so I had the file in my drive and read it in that way.

To run the code, you need to download this file, 

https://github.com/SamMilnes/DS-Individual-Final-Project/blob/main/golf_data_forDSFinalProject%20(1).csv

and save it somewhere of your choosing. After doing this you need to go to the first cell and comment out this line,

drive.mount('/content/gdrive')


Lastly, you need to change the file path to where you saved the file. So in the second cell instead of 

golf_data = pd.read_csv('/content/gdrive/MyDrive/Data Science Individual Project/golf_data_forDSFinalProject.csv', encoding= 'unicode_escape')


it should be,

golf_data = pd.read_csv('YOUR_FILE_PATH/golf_data_forDSFinalProject.csv', encoding= 'unicode_escape')


After you do this, everything should run smoothly.

