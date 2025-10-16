# Penguin Features Analysis to Detect Species Differentiation
## Using Sex, Culmen Length (mm), and Culmen Depth (mm)
After creating visualizations of different quantitative features we see that culmen length versus culmen depth has fairly distinct clusters between species. When looking at the histogram of body mass and boxplots of flipper length the species have more overlap. Specifically with flipper length, the Adelie and Chinstrap penguins have very similar ranges of lengths, which would make it difficult to predict species using flipper length alone. We also created scatter plots to explore the variables relating to isotopes in the blood; some of the combinations of this figure had better clustering than others. However it seems the scatter plot of culmen length and depth has the best separation.

![alt text](https://github.com/cotaffe/Penguin-Features-Analysis/blob/main/BodyMassHistogram.png)

![alt text](https://github.com/cotaffe/Penguin-Features-Analysis/blob/main/CulmenScatterplot.png)

![alt text](https://github.com/cotaffe/Penguin-Features-Analysis/blob/main/FlipperLengthBoxplot.png)


### Feature Selection
We performed a thorough exploratory analysis, which included scatterplots and grouped summary tables that help to visualize distinctions between the various species. Our visualizations include combinations of 6 quantitative features from the penguins data frame. After creating the visualizations, we analyzed these distributions between species leading to our final decision. We chose Sex, Culmen Length (mm), and Culmen Depth (mm) as our key features due to their leading ability to distinguish between penguin species among the available features.

Sex

Sex was chosen as the qualitative feature as it will provide valuable information in distinguishing penguins based on size and morphology between sexes. The summary table unveils that the culmen length (mm), culmen depth (mm) and even body mass is very different between males and femalles in each species. An example of this is how males have longer culmens than females in the Adelie species, thus highlighting differentiation. This gender-based distinction is important, as it helps the model differentiate between male and female penguins of the same species, which can significantly vary in size. Including Sex as a feature provides an extra layer of information that complements the quantitative features and aids in effective classification.

Culmen Length (mm)

Culmen Length (mm) was chosen as our first quantitative feature. The scatterplot comparing culmen length (mm) and culmen depth (mm) reveals that different culmen lengths correspond to different penguin species. For example, according to the scatterplot, Chinstrap penguins have the longest culmen lengths, while Adelie penguins are typically seen to have shorter culmen lengths.Furthermore, according to the summary table, the mean values of the culmen length also are different across the penguin species, demonstrating its differentiating power. For instance, Adelie penguins usually have culmen lengths of approximately 38 mm, while Chinstrap penguins have culmen lengths of approximately 50 mm. Therefore, culmen length (mm) would be an insightful predictor in distinguishing penguin species.

Culmen Depth (mm)

Culmen Depth (mm) was chosen as our second quantitative feature. The scatterplot comparing culmen length (mm) and culmen depth (mm) shows that culmen depths (mm) offer an additionaly layer of insight in distinguishing penguin species. For example, while Adelie penguins have much deeper culmens while the Gentoo penguins have more moderate culmen depths. The summary table further elicits that the mean values for culmen depths (mm) can also illustrate differences between species. For instance, Chinstrap penguins have culmen depths of approximately 17 mm while Adelie penguins have culmen depths of approximately 18 mm. Therefore, culmen depth (mm) also would provide valuable information to help distinguish between penguin species.

### Model

![alt text](https://github.com/cotaffe/Penguin-Features-Analysis/blob/main/ModelVisulization.png)

Logistic regression creates linear decision boundaries, making it highly effective for instances where classes are linearly separable. However, it struggles in cases where the species have overlapping distributions or nonlinear relationships. For instance, in regions where the Culmen Length (mm) and Culmen Depth (mm) values are close, the model's linear approximation may misclassify points that belong to a species with a more complex boundary. This limitation is evident in the decision regions where misclassified points lie at the edges of two species' boundaries.

While the Support Vector Machine performed well overall, it misclassified a few instances in a class with lower representation, likely due to a suboptimal balance between margin maximization and fitting complex decision boundaries. The non-linear kernel allows for flexibility, but in regions with significant overlap between species, especially for points near the boundary of two regions, the model may overfit or underfit slightly depending on the chosen hyperparameters (C and gamma). This is reflected in the jagged or overly constrained boundaries in the decision region plots.

K-Nearest Neighbors adapts well to local patterns and performs well in regions with clear separation between classes. However, it is highly sensitive to noise and outliers, as predictions depend directly on the local neighborhood. This sensitivity can result in errors when a sample from one species is surrounded by a majority of neighbors from another species, leading to misclassification. The decision regions for K-Nearst Neighbors show a patchy pattern, particularly at the borders between classes, indicating susceptibility to small-scale variations in the data distribution.

In summary, the mistakes made by each model highlight their inherent trade-offs: Logistic Regression struggles with non-linear boundaries, Support Vector Machine with hyperparameter sensitivity in complex overlaps, and K-Nearst Neighbors with noise and boundary ambiguity. These errors are illustrated in the decision region plots, where the regions of misclassification align with the models' respective limitations.

### Discussion
Following our exploratory analysis section, we chose to create our models using Sex, Culmen Length (mm) and Culmen Depth (mm). We performed a logistic regression, support vector machine and K-nearest neighbors model on these features, all of which performed very well, scoring from 0.96 to 0.98 on the separated test data. This high accuracy suggests that Sex, Culmen Length (mm), and Culmen Depth (mm) are highly valuable and informative features for predicting penguin species.

Based on accuracy of the test data alone, the logistic regression and/or the K-nearest neighbors would be great models for the data. When looking at the Decision Regions by Sex Model, it seems that the K-nearest neighbors model, due to its ability to capture nonlinear boundaries between species, fits the data the best as most of the data points are in their respective decision region. However, logistic regression (which performed just as well) might be more advantageous for its simplicity. Despite the high accuracy, all three models faced challenges with certain overlapping data points, where species boundaries are less distinct. In the future,it might be beneficial to explore more features in our models, which could further enhance differentiation between species when Culmen Length (mm) and Culmen Depth (mm) leaves uncertainty.

Due to the jagged nature of the K-nearest neighbors decision regions, we are concerned about overfitting with this model. In the male models, we can see the blue has two seperate pockets to account for only a couple points. Because we got accurate results with the test data, overfitting may not be the best case. Nonetheless, it is important to sitll keep the K-nearest neighbors model in mind.

When looking at the differences in the decision regions between male and female models, it is interesting to note that the decision regions on the visualizations corresponding to male penguins don't seem to be as accurate. Specifically, the Chinstrap data expands into the Gentoo and Adelie regions on the logistic regression and support vector machine models. Due to this disparity between males and females, it might be beneficial to split the data and test the models separately by sex first, which is followed by choosing the best corresponding model to visualize the data.
