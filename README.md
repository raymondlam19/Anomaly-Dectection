# Anomaly-Dectection
 
I assumed the number of outliers / anomalies is 2% of the whole dataset (454 rows).
I used KMeans, isolation forest & one-class SVM respectively to detect the anomalies.
The theory behind those algorithms is to find the points far away from the cluster which are identified as outliers / anomalies.

One-class SVM was used to detect novelties. Novelty detection is the training data is not polluted by outliers and we are interested in detecting whether a new observation is an outlier. In this context an outlier is also called a novelty.

Isolation forest was used to detect outliers. Outlier detection is the training data contains outliers which are defined as observations that are far from the others. Outlier detection estimators thus try to fit the regions where the training data is the most concentrated, ignoring the deviant observations.

Outlier detection and novelty detection are both used for anomaly detection, where one is interested in detecting abnormal or unusual observations. Outlier detection is also known as unsupervised anomaly detection. In the context of outlier detection, the outliers/anomalies cannot form a dense cluster as available estimators assume that the outliers/anomalies are located in low density regions. On the contrary, in the context of novelty detection, novelties/anomalies can form a dense cluster as long as they are in a low density region of the training data, considered as normal in this context.

As they is an unsupervised algorithms, there is no labeled data. We cannot access the accuracy of the algorithms unless we have labelled data. If we have the labelled data, we may use Recall for the small positive class (imbalanced data).

First, during understanding the data, I found that the mean value of the whole data was 85.9 and the max & min were 108 & 2 respectively. Then I guess the value was Fahrenheit and thus I converted the value to Celsius for easy understanding.

Second, during feature engineering, based on the assumption that it was temperature data, I extracted some useful feature from the original dataset (hours, daylight, DayOfTheWeek, WeekDay).

Third, I used 3 different unsupervised algorithms (KMeans, isolation forest & one-class SVM) to detect the outliers / anomalies with the assumption of the dataset having 2% outliers / anomalies.

We might lower the outliers fraction from 2% to 1% (optional) and then combine the results from 3 different unsupervised algorithms to find outliers / anomalies, e.g. 
df[‘anomaly’] = int(df. anomaly_kmeans | df.anomaly_isolationforest |df. anomaly_oneclassSVM)
or using a voting scheme from different models

Try tuning different hyperparameters, e.g.:
1. outliers_fraction
2. Isolation forest: n_estimators, max_samples, max_features
3. one-class SVM: kernel, gamma


