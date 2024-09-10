Schuster is a multinational retail company dealing in sports goods and accessories. Schuster conducts significant business with hundreds of its vendors, with whom it has credit arrangements. Unfortunately, not all vendors respect credit terms and some of them tend to make payments late. Schuster levies heavy late payment fees, although this procedure is not beneficial to either party in a long-term business relationship. The company has some employees who keep chasing vendors to get the payment on time; this procedure nevertheless also results in non-value-added activities, loss of time and financial impact. Schuster would thus try to understand its customers’ payment behaviour and predict the likelihood of late payments against open invoices.

To understand how to approach this problem using data science, let’s first understand the payment process at Schuster now. Every time a transaction of goods takes place with a vendor, the accounting team raises an invoice and shares it with the vendor. This invoice contains the details of the goods, the invoice value, the creation date and the payment due date based on the credit terms as per the contract. Business with these vendors occurs quite frequently. Hence, there are always multiple invoices associated with each vendor at any given time.

Goal 
•	Schuster would like to better understand the customers’ payment behaviour based on their past payment patterns (customer segmentation).
•	Using historical information, it wants to be able to predict the likelihood of delayed payment against open invoices from its customers.
•	It wants to use this information so that collectors can prioritise their work in following up with customers beforehand to get the payments on time.
To summarise, as a business analyst, you want to find the answer to these questions:
•	How can we analyse the customer transactions data to find different payment behaviours?
•	In which way can you segregate the customers based on their previous payment patterns/behaviours?
•	Based on the historical data, can you predict the likelihood of delayed payment against open invoices from the customers?
•	Can you draw any business insights based on your developed model?



Data Preparation 
The following data preparation steps are crucial for this problem:
1.	Start with the ‘Received Payment Data’ file. This is the invoice-level dataset, which you will need to analyse customers’ past payment patterns and to train and test your ML model.
2.	Since we are dealing with data related to payments received, you have to ignore any observation where the invoice value is less than 0. 
3.	Make sure that you take care of any data quality issues lurking in both your datasets.
4.	Your target variable is whether the payment against an invoice was made on time or late. As explained above, you can derive this by checking whether the payment receipt date falls before or after the due date. By doing so, you can create your binary target variable as 1 or 0.
5.	Once you have determined your target variable, you have to decide on the features to use for your model. Invoice-level attributes, such as invoice value or USD Amount, are important. Payment Term is also an important attribute but is currently in text format. You may have to derive the Payments Terms feature based on the difference between the Due Date and the Invoice Creation Date so that it gives you a numerical variable. You can explore what other features could be important for your model building.
6.	Customer-level attributes could also be important independent variables to be included in the model. A customer-level attribute can be determined via customer segmentation. You have to segment your customers based on two derived variables: the average payment time in days for a customer and the standard deviation for the payment time. Using clustering techniques would result in a few distinct clusters of customers, which can be used as an input variable for the ML model.
 
Model Building & Model Evaluation
1.	Identify important variables that are strong predictors of late payments. These variables may also indicate why customers will likely make late payments in the future.
2.	Try and build multiple classification models to predict whether a payment will be delayed or not at an invoice level. The predicted score (0 or 1) derived at an invoice level can be aggregated to show the result at a customer level. 
3.	You may notice that the open invoice data has a column 'AGE'. The age is calculated by taking the difference between Transaction Date and AS_OF_DATE (refer to the data dictionary if required). This means that a positive value in the AGE column clearly indicates that the payment is already overdue. So, there is nothing to predict. But, a negative value in the AGE column means that the due date is yet to be crossed. Hence, your model should be able to predict whether the payment will be delayed or not only for those customers whose AGE value is negative.
 
Results Expected
1.	You have to conduct appropriate exploratory data analysis to extract useful insights (whether directly useful for business or for eventual modeling/feature engineering).
2.	Once you performed the EDA, you can segregate the customer into different groups based on their payment pattern using historical data.
3.	Next, you have to build a classification model. Make sure that your model output predicts whether a payment will be delayed or not at the invoice level. Note that, this is a classic binary classification problem.
4.	After identifying important predictors, and the final model to be adopted by Schuster, you have to apply the model on the open invoice data to suggest how this model will be applied in real-time data going forward. You have to ensure that the probability of late payment is aggregated at a customer level.
5.	You have to display your model’s outputs, that is, the customer segmentation output, visually – you can use plots, summary tables, etc. for this. Use whatever you think best conveys the importance of the features and the model’s results.
6.	Finally, you have to identify customers for whom Schuster has to take precautionary measures beforehand.
 

