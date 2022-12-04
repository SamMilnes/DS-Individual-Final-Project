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


![Screenshot 2022-12-04 180701](https://user-images.githubusercontent.com/68667116/205521163-84e986b9-df0f-4150-890c-c43f323d1d63.png)

Next it was time to create our model. After playing around with hyperparameters for a bit, I decided to create a network with 4 hidden layers, a mean squared error loss function, an Adam optimizier, a learning rate of 0.01, and 300 epochs.


![Screenshot 2022-12-04 182711](https://user-images.githubusercontent.com/68667116/205522201-23e7fe78-49e6-437b-b37c-08c63572f56b.png)




## Methods
Tools:
* 1
* 2

* 3
* 4
* 5
## Results
Write results here
## Discussion
Write Discussion here
## Reference
Write Reference Here
