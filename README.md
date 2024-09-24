# RandomWalk Data Science Assessment

## Instructions:

1) Fork the github repo into your personal Github account and take a clone into your local system.

   Guide to Forking Github Repo: https://docs.github.com/en/github-ae@latest/get-started/quickstart/fork-a-repo

   Guide for cloning Github Repo: https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository

2) Intantiate a Jupyter Notebook instance in the local working directory and create a notebook which answers the following questions.

   Guide for installing Jupyter Notebook in Local system: https://test-jupyter.readthedocs.io/en/latest/install.html

3) Save the notebook and push it into forked Github github repo.

   Guide to pushing code into Github Repo: https://docs.github.com/en/migrations/importing-source-code/using-the-command-line-to-import-source-code/adding-locally-hosted-code-to-github
   
4) Record a screencast video recording demonstrating the solution in your system and upload the video into the forked github repo.

   Guide to record screen in

   a) MAC: https://support.apple.com/en-in/102618

   b) Windows: https://www.microsoft.com/en-us/windows/learning-center/how-to-record-screen-windows-11

   c) Ubuntu: https://askubuntu.com/questions/4428/how-can-i-record-my-screen
   
5) Share the repository link into the Google Form: https://forms.gle/QCfjjyQQ5jnoegNe9

## Questions:

Q1: Identify missing or incorrect data in the dataset and apply appropriate preprocessing steps to clean it (code and explanation)

To address outliers that could affect missing value imputation, I removed penguins with body weights exceeding 6300 grams and replaced unknown 'sex' values with NaN.

I performed a pairplot analysis, revealing that Gentoo penguins, especially from Biscoe Island, formed distinct clusters, while other species overlapped. This distinction suggests that species is a strong feature for categorical mean-based imputation.

Since this task is data analysis, I used the entire dataset for filling missing values. In predictive modeling, it's better to use only training data to avoid data leakage.

For imputing 'sex,' I found strong correlations with features like bill length, bill depth, flipper length, and body mass. I confirmed these relationships using one-hot encoding and a correlation matrix.

Next, I created scatter plots and observed clear differences between males and females, particularly in the Bill Depth vs Flipper Length plot. This led me to use KNN to predict missing 'sex' values. After removing rows with missing 'sex,' I trained the KNN model, tuned the value of 'k,' and selected the best-performing model. I visualized the results using a confusion matrix before imputing the missing values.

This process ensured accurate and consistent handling of missing data throughout the analysis.

Q2: What is the average body_mass_g for Gentoo penguins? (code)

To find the average body mass of Gentoo penguins, the logic involves first identifying the rows in the dataset that correspond to the Gentoo species. Once these penguins are isolated, their body mass values are extracted. The average of these values is then calculated, giving the mean body mass for all Gentoo penguins in the dataset. Finally, this average is displayed in a readable format.

Q3: How do the distributions of bill_length_mm and bill_depth_mm differ between the three penguin species? Analyze the skewness and kurtosis of each feature for different species. (code and explanation)

The analysis reveals that Gentoo penguins have longer bill lengths and exhibit more distinct distributions compared to Adelie and Chinstrap penguins. While Adelie and Chinstrap penguins show relatively symmetric distributions with minor differences, Gentoo penguins display a right-skewed, more peaked distribution for bill length, suggesting greater variability in their bill measurements. These differences are useful for distinguishing between species.


Q4: Identify which features in the dataset have outliers. Provide the method used to detect them and visualize the outliers. (code and explanation)

I detected outliers by applying the 1.5x Interquartile Range (IQR) rule and visualized them using boxplots and histograms. Outliers were identified and subsequently removed from the dataset.

Q5: Does this dataset contribute to the curse of dimensionality? If yes perform PCA. (code and explanation required)

The dataset does not contribute to the curse of dimensionality, as it contains only 9 columns. To prepare the data for analysis, I applied one-hot encoding to transform categorical columns into binary features. Subsequently, I performed Principal Component Analysis (PCA) to reduce the dimensionality of the dataset.

I visualized the relationship between the number of principal components and the cumulative explained variance. This analysis indicated that 5 principal components are needed to capture 95% of the variance in the dataset. However, since the dataset remains relatively small with only 9 columns after modification, the impact of dimensionality reduction is minimal in this case.


Q6: Use bill_length_mm vs bill_depth_mm and plot 7 different graphs to visualize them. (code)

To visualize the relationship between bill length and bill depth, I created seven different types of graphs:

Scatter plots to depict the relationship between the two numerical variables.
Hexbin plots and 2D histograms to illustrate the density of overlapping data points.
KDE plots to present smoother distributions of variables such as body mass.
Regression plots to analyze linear trends between the features.
Violin plots to showcase the distribution and variability of bill dimensions across different penguin species.

Q7: Find the maximum flipper_length_mm for each combination of species and island. Which species has the longest flippers on each island? (code)

To determine the maximum flipper length for each combination of species and island, I utilized the groupby method on both the species and island columns. This allowed me to identify the maximum flipper length for each unique species-island pair. I also conducted a separate groupby operation on the island to find the species with the longest flippers for each island.


Q8: Perform z-score normalization on this dataset. (code)

To normalize the dataset, I first applied z-score normalization using a StandardScaler on the numerical columns. After normalizing the numerical data, I used one-hot encoding to transform the categorical columns into binary format and then combined them with the normalized numerical data.
