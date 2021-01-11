# Cutomer-Churn-Classification

# Introduction
With the advent of competition in the business world, the average consumer is bombarded with various offers of novel goods and services. What determines whether he or she will take up that new offer or service? What are the best techniques for reducing customer attrition and thus helping increase one’s profits? How does this relate to the highly saturated telecom industry, where growth is minimal, and competition is high? The traditional methodology to answering these questions may have included marketing experts and the theory of consumer behavior. But perhaps there is another method which may work better and be less objective. With the ever-increasing amounts of consumer data available, this problem may be solved better with the use of machine learning techniques that can use complex algorithms to create prediction models. This is exactly what we set out to achieve in this paper.

By using open source Churn Rate data at a Telecommunications firm, this project aim at creating a model to predict future churn rates. There are over 7000 data objects and 21 data attributes in our dataset. The churn-rate and non-churn rates are 73.4% and 26.6% respectively. We employed several machine learning models which were subsequently compared using F1-Score.

# Related Work
There are many prior works for applying data mining techniques on telecom churn prediction. 
Wei and Chiu (2002) [1] worked on churn prediction using data mining approach. In their study they used decision trees for learning. Instead of using customer demographics like other researchers, they only used contract data to build a churn prediction model, which has better applicability on data that have limited information on customers. 

In Keramati, Jabari-Marandi, Aliannejadi, Ahamadian, Mozaffari and Abbasi’s (2014) [2] research, Artificial neural network, K-nearest neighbor, support vector machine (SVM) and decision trees are used. They also introduced a new dimensionality reduction methodology to extract the most influential set of features in the data.

Lu, Lin, Lu and Zhang (2014) [3], used different methodologies from other mentioned prior works: Boosting and Logistic regression. In this case they used boosting to enhance their churn prediction model. The authors separated customers into 2 clusters using the weights that were given by the algorithm. This is different from other boosting methods. Their model allows for an “Implementation Zone” in which a business can give customers with the highest churn propensity some “Retention Action.”

Hung, Yen and Wang (2005) [4] used IT technology to facilitate their study on churn management. Specifically, they used techniques like decision tree, neural network and K-means cluster in their research on Taiwanese telecom service churn. Instead of choosing important variables by running a regression model or doing classification, they interviewed experts to help them select deterministic variables in their research. They used billing amount to understand ‘customer value’, tenure months to know ‘customer loyalty’ and payment behaviors to estimate ‘customer credit risks’.

In general, previous researches on churn prediction in telecom industry mainly used classification techniques like decision tree to construct prediction models using data with different types of features. In our research, we have data with full customer demographics and contract details, so we decided to try all known models for classification and pick the best model from them using the accuracy mean and accuracy standard deviation for evaluation.

# Exploratory Data Analysis
First of all, according to bar chart of Churn, it is clear to see that this dataset is imbalanced. Therefore we need to take some action to deal with this problem. (use class_weight argument and use F1-Score to evaluate our models)

![alt text](https://github.com/MiaoHu17/Cutomer-Churn-Classification/blob/main/plot/plot2.png?raw=true)

For ***gender*** and ***PhoneService*** it is clear to see that churn percent is almost the same in case of Male and Females and No PhoneService and Yes PhoneService

![alt text](https://github.com/MiaoHu17/Cutomer-Churn-Classification/blob/main/plot/plot1.png?raw=true)

Further Chi-Square Test indicates that ***gender*** and ***PhoneService*** should be excluded from the models

| Variable         | Chi squared value | p-value       |
|------------------|-------------------|---------------|
| gender           | 0.475455          | 4.904885e-01  |
| SeniorCitizen    | 158.440816        | 2.479256e-36  |
| Partner          | 157.503151        | 3.973798e-36  |
| Dependents       | 186.321639        | 2.019659e-42  |
| PhoneService     | 0.873733          | 3.499240e-01  |
| MultipleLines    | 11.271541         | 3.567927e-03  |
| InternetService  | 728.695614        | 5.831199e-159 |
| OnlineSecurity   | 846.677389        | 1.400687e-184 |
| OnlineBackup     | 599.175185        | 7.776099e-131 |
| DeviceProtection | 555.880327        | 1.959389e-121 |
| TechSupport      | 824.925564        | 7.407808e-180 |
| StreamingTV      | 372.456502        | 1.324641e-81  |
| StreamingMovies  | 374.268432        | 5.353560e-82  |
| Contract         | 1179.545829       | 7.326182e-257 |
| PaperlessBilling | 256.874908        | 8.236203e-58  |
| PaymentMethod    | 645.429900        | 1.426310e-139 |

# Experiement Design

Because we do not know which classification model would perform best, we decided to try all the classification techniques we introduced in the previous section. Initially, we wanted to use Logistic Regression, Decision Tree, Random Forest, XGBoost, Support Vector Machine and Multilayer Perceptron. F1-Score is selected to be the evaluation criteria.

# Conclusion

| Model                  |    F1-Score    |
|------------------------|----------------|
| Logistic Regression    |    76.55%      |
| Decision Tree          |    78.48%      |
| Support Vector Machine |    78.43%      |
| Multilayer Perceptron  |    79.48%      |
| Random Forest          |    78.78%      |
| XGBoost                |    78.72%      |

The winner on the validation set is Multilayer Perceptron, therefore it is used for test set. The performance on test set is 79.31%.

There are several important insights our model can provide to a telecom industry business looking to reduce churn rate. Off course, one very useful way our model can be utilized is to use it directly on new customer data to find customers most likely to churn, and then provide those customers with extra incentives to not-churn. Considering that our F1-Score is approximately 80%, we believe this would be a very effective technique in reducing churn rate.

![alt text](https://github.com/MiaoHu17/Cutomer-Churn-Classification/blob/main/plot/plot3.png?raw=true)

However, there are other less obvious actions our study can suggest in improving customer churn rate. One has to do with the finding that a lower Monthly-Charge can improve churn-rate. This leads us to suggest that firms should consider using discounted introductory rates that will provide enticing incentives for new customers to try their service. Although some customers may cancel their service after this discounted time period, other customers will choose to stay because of the extra hassles of switching services. Another is the finding that increased-tenure leads to lower churn rate. Thus, we would suggest firms to focus on converting short-term customers to long-term customers. Long-term customers are already less likely to churn, but by offering short-term customers incentives to become long-term customers, one can reduce the churn rate of ‘high risk’ customers.


# Reference
[1] Wei, C., & Chiu, I. (2002). Turning telecommunications call details to churn prediction: A data mining approach. Expert Systems with Applications, 23(2), 103-112. doi:10.1016/S0957-4174(02)00030-1

[2] Keramati, A., Jafari-Marandi, R., Aliannejadi, M., Ahmadian, I., Mozaffari, M., & Abbasi, U. (2014). Improved churn prediction in telecommunication industry using data mining techniques. Applied Soft Computing Journal, 24, 994-1012. doi:10.1016/j.asoc.2014.08.041

[3] Lu, N., Lin, H., Lu, J., & Zhang, G. (2014). A customer churn prediction model in telecom industry using boosting. IEEE Transactions on Industrial Informatics, 10(2), 1659-1665. doi:10.1109/TII.2012.2224355

[4] Hung, S., Yen, D. C., & Wang, H. (2006). Applying data mining to telecom churn management. Expert Systems with Applications, 31(3), 515-524. doi:10.1016/j.eswa.2005.09.080

[5] S. Kim, K.S. Shin, K. Park, An Application of Support Vector Machines for Cus-
tomer Churn Analysis: Credit Card Case, 2005, pp. 636–647.

[6] X. Liu, W. Pedrycz, The development of fuzzy decision trees in the framework 
of axiomatic fuzzy set logic, Appl. Soft Comput. J. 7 (2007) 325–342.

[7] C. Cortes, V. Vapnik, Support-vector networks, Mach. Learn. 20 (1995) 273–297.

[8] Breiman, L. (2001). Random forests. Machine Learning, 45(1), 5-32. doi:http://dx.doi.org/10.1023/A:1010933404324

[9] A Gentle Introduction to XGBoost for Applied Machine Learning. (2016, September 21). Retrieved from https://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/
